<script>
    import { onMount } from "svelte";
    import L from "leaflet";
  
    let map;
    let polyline;
    let watchId = null;
    let isTracking = false;
    let positions = [];
    let totalDistance = 0;
  
    function startTracking() {
      if (navigator.geolocation) {
        isTracking = true;
        positions = [];
        totalDistance = 0;
        
        watchId = navigator.geolocation.watchPosition(
          (position) => {
            const { latitude, longitude } = position.coords;
            positions.push([latitude, longitude]);
  
            if (positions.length > 1) {
              totalDistance += getDistance(positions[positions.length - 2], positions[positions.length - 1]);
            }
  
            updateMap();
          },
          (error) => {
            console.error("Erreur GPS:", error.message);
          },
          { enableHighAccuracy: true }
        );
      } else {
        alert("La géolocalisation n'est pas supportée par votre navigateur.");
      }
    }
  
    function stopTracking() {
      if (watchId) {
        navigator.geolocation.clearWatch(watchId);
        watchId = null;
      }
      isTracking = false;
      console.log("Distance totale parcourue :", totalDistance.toFixed(2), "km");
    }
  
    function updateMap() {
      if (positions.length === 1) {
        map.setView(positions[0], 15);
      }
  
      polyline.setLatLngs(positions);
    }
  
    function getDistance([lat1, lon1], [lat2, lon2]) {
      const R = 6371; // Rayon de la Terre en km
      const dLat = (lat2 - lat1) * (Math.PI / 180);
      const dLon = (lon2 - lon1) * (Math.PI / 180);
      const a =
        Math.sin(dLat / 2) * Math.sin(dLat / 2) +
        Math.cos(lat1 * (Math.PI / 180)) *
          Math.cos(lat2 * (Math.PI / 180)) *
          Math.sin(dLon / 2) *
          Math.sin(dLon / 2);
      const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
      return R * c; // Distance en km
    }
  
    onMount(() => {
      map = L.map("map").setView([48.8566, 2.3522], 13); // Paris par défaut
  
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        attribution: "&copy; OpenStreetMap contributors",
      }).addTo(map);
  
      polyline = L.polyline([], { color: "blue" }).addTo(map);
    });
  </script>
  
  <style>
    #map {
      width: 100%;
      height: 400px;
    }
  </style>
  
  <div>
    <button on:click={startTracking} disabled={isTracking}>Go</button>
    <button on:click={stopTracking} disabled={!isTracking}>Arrivé</button>
    <p>Distance parcourue : {totalDistance.toFixed(2)} km</p>
  </div>
  
  <div id="map"></div>
  