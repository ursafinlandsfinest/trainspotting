<!DOCTYPE html>
<html lang="fi">
<head>
  <meta charset="UTF-8" />
  <title>Ursa Trainspotting</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  />

  <style>
    html,
    body {
      margin: 0;
      padding: 0;
      height: 100%;
      font-family: Arial, sans-serif;
      background: #111;
      color: white;
    }

    body {
      display: flex;
      flex-direction: column;
    }

    header {
      padding: 12px 16px;
      background: #181818;
      border-bottom: 1px solid #333;
    }

    h1 {
      margin: 0 0 8px 0;
      font-size: 21px;
    }

    .controls {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
      margin-top: 8px;
    }

    input,
    button,
    label {
      font-size: 14px;
    }

    input {
      padding: 7px 9px;
      border-radius: 6px;
      border: 1px solid #555;
      background: #222;
      color: white;
    }

    button {
      padding: 7px 10px;
      border-radius: 6px;
      border: 1px solid #555;
      background: #2a2a2a;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background: #3a3a3a;
    }

    #status {
      margin-top: 8px;
      font-size: 14px;
      color: #ccc;
    }

    .disclaimer {
      margin-top: 8px;
      padding: 8px 10px;
      background: #2a2415;
      border: 1px solid #7a6420;
      border-radius: 8px;
      color: #f2d27a;
      font-size: 13px;
      line-height: 1.35;
    }

    #map {
      flex: 1;
      width: 100%;
      min-height: 420px;
    }

    .cargo-popup,
    .spot-popup,
    .yard-popup {
      font-size: 14px;
      line-height: 1.45;
    }

    .popup-note {
      margin-top: 8px;
      padding-top: 8px;
      border-top: 1px solid #ccc;
      font-size: 12px;
      color: #555;
    }

    .legend {
      position: absolute;
      z-index: 1000;
      bottom: 20px;
      left: 12px;
      background: rgba(20, 20, 20, 0.92);
      color: white;
      padding: 10px 12px;
      border-radius: 8px;
      font-size: 13px;
      border: 1px solid #444;
    }

    .legend-row {
      margin-bottom: 5px;
    }

    .dot {
      display: inline-block;
      width: 11px;
      height: 11px;
      border-radius: 50%;
      margin-right: 6px;
      vertical-align: middle;
    }

    .red {
      background: #e84b4b;
    }

    .green {
      background: #4be86e;
    }

    .gray {
      background: #888;
    }

    .blue {
      background: transparent;
      border: 2px solid #4bb3ff;
      box-sizing: border-box;
    }

    .triangle-symbol {
      display: inline-block;
      width: 0;
      height: 0;
      border-left: 7px solid transparent;
      border-right: 7px solid transparent;
      border-bottom: 13px solid #ffcc33;
      margin-right: 6px;
      vertical-align: middle;
    }

    .triangle-marker {
      width: 0;
      height: 0;
      border-left: 11px solid transparent;
      border-right: 11px solid transparent;
      border-bottom: 20px solid #ffcc33;
      filter: drop-shadow(0 0 3px rgba(0,0,0,0.8));
    }

    .info-panel {
      display: none;
      position: absolute;
      z-index: 1001;
      top: 190px;
      right: 14px;
      max-width: 380px;
      background: rgba(20, 20, 20, 0.96);
      border: 1px solid #555;
      border-radius: 10px;
      padding: 14px;
      font-size: 13px;
      line-height: 1.45;
      color: #eee;
    }

    .info-panel h2 {
      margin: 0 0 8px 0;
      font-size: 16px;
    }

    .info-panel p {
      margin: 0 0 8px 0;
    }

    @media (max-width: 700px) {
      h1 {
        font-size: 18px;
      }

      .controls {
        align-items: flex-start;
        flex-direction: column;
      }

      .info-panel {
        left: 12px;
        right: 12px;
        top: 210px;
        max-width: none;
      }

      .legend {
        font-size: 12px;
        bottom: 12px;
      }
    }
  </style>
</head>

<body>
  <header>
    <h1>Ursa Trainspotting</h1>

    <div class="controls">
      <input id="searchInput" type="text" placeholder="Hae junanumerolla" />

      <button onclick="applyFilters()">Hae</button>
      <button onclick="clearFilters()">Tyhjennä</button>
      <button onclick="toggleInfo()">Turvallisuus ja tietolähteet</button>

      <label>
        <input id="stoppedOnly" type="checkbox" onchange="applyFilters()" />
        Näytä vain pysähtyneet
      </label>

      <label>
        <input id="showYards" type="checkbox" checked onchange="renderStaticLayers()" />
        Ratapihat
      </label>

      <label>
        <input id="showSpots" type="checkbox" checked onchange="renderStaticLayers()" />
        Katselupaikat
      </label>
    </div>

    <div id="status">Ladataan junadataa...</div>

    <div class="disclaimer">
      Tämä sivusto on tarkoitettu junien katseluun ja seuraamiseen julkisilta, turvallisilta paikoilta.
      Älä mene raiteille, ratapihoille, aidatuille alueille tai junien läheisyyteen.
      Reittiohjeet annetaan vain erikseen merkittyihin katselupaikkoihin, ei junan sijaintiin tai ratapihoille.
    </div>
  </header>

  <div id="map"></div>

  <div class="legend">
    <div class="legend-row"><span class="dot red"></span> Pysähtynyt cargo</div>
    <div class="legend-row"><span class="dot green"></span> Liikkeessä oleva cargo</div>
    <div class="legend-row"><span class="dot gray"></span> Nopeus ei tiedossa</div>
    <div class="legend-row"><span class="dot blue"></span> Ratapiha, hahmottava alue</div>
    <div class="legend-row"><span class="triangle-symbol"></span> Turvallinen katselupaikka</div>
  </div>

  <div id="infoPanel" class="info-panel">
    <h2>Turvallisuus ja tietolähteet</h2>

    <p>
      Tämä sivusto on tarkoitettu junaharrastajille ja junien katselijoille,
      jotka haluavat seurata tavarajunien liikkeitä ja löytää turvallisia, julkisia katselupaikkoja.
    </p>

    <p>
      Junasijainnit perustuvat avoimeen liikennedataan. Tiedot voivat olla viiveellisiä,
      puutteellisia tai epätarkkoja.
    </p>

    <p>
      Ratapihat on merkitty kartalle vain hahmottamisen vuoksi. Ne eivät ole katselupaikkoja.
      Sivusto ei anna reittiohjeita ratapihoille, raiteille, aidatuille alueille tai junien luo.
    </p>

    <p>
      Katselupaikat on tarkoitettu julkisilta alueilta tapahtuvaan junien katseluun,
      esimerkiksi silloilta, asemien sallituilta alueilta, kävelyteiltä tai muilta turvallisilta paikoilta.
    </p>

    <p>
      Älä ylitä raiteita luvattomasta paikasta, mene ratapihalle, kiipeä junaan,
      koske junakalustoon tai liiku alueilla, joille pääsy on kielletty.
    </p>

    <button onclick="toggleInfo()">Sulje</button>
  </div>

  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <script>
    const API = "https://rata.digitraffic.fi/api/v1";

    const map = L.map("map").setView([64.5, 26.0], 6);

    L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
      maxZoom: 18,
      attribution: "© OpenStreetMap | Data: Fintraffic / Digitraffic"
    }).addTo(map);

    let trainLayer = L.layerGroup().addTo(map);
    let yardLayer = L.layerGroup().addTo(map);
    let spotLayer = L.layerGroup().addTo(map);

    let latestCargoData = [];
    let stationNames = new Map();
    let followedTrainKey = null;

    /*
      Ratapihat ovat hahmottavia alueita, eivät virallisia rajoja.
      Näihin ei anneta reittiohjeita.
    */
    const railYards = [
      { name: "Oulu ratapiha", lat: 65.013, lon: 25.472, radius: 1400 },
      { name: "Tampere ratapiha", lat: 61.497, lon: 23.766, radius: 1500 },
      { name: "Kouvola ratapiha", lat: 60.869, lon: 26.704, radius: 1700 },
      { name: "Pasila ratapiha", lat: 60.205, lon: 24.933, radius: 1300 },
      { name: "Riihimäki ratapiha", lat: 60.738, lon: 24.777, radius: 1200 },
      { name: "Seinäjoki ratapiha", lat: 62.790, lon: 22.842, radius: 1200 },
      { name: "Tampere Viinikka", lat: 61.475, lon: 23.775, radius: 1300 },
      { name: "Turku ratapiha", lat: 60.455, lon: 22.253, radius: 1200 },
      { name: "Joensuu ratapiha", lat: 62.601, lon: 29.763, radius: 1200 },
      { name: "Jyväskylä ratapiha", lat: 62.242, lon: 25.754, radius: 1000 },
      { name: "Kokkola ratapiha", lat: 63.839, lon: 23.131, radius: 1300 },
      { name: "Vainikkala ratapiha", lat: 60.868, lon: 28.303, radius: 1500 }
    ];

    /*
      Lisää tähän vain paikkoja, jotka tiedät julkisiksi ja turvallisiksi katselupaikoiksi.
      Alla on yksi esimerkkipaikka, jotta näet, miten kolmio toimii.
      Voit poistaa sen ja lisätä oikeat paikat.
    */
    const viewingSpots = [
      {
        name: "Esimerkki: julkinen katselupaikka",
        lat: 65.010,
        lon: 25.470,
        type: "Julkinen silta tai kävelyalue",
        description: "Vaihda tämä oikeaan, itse varmistettuun katselupaikkaan.",
        access: "Reitti vain julkista kulkuväylää pitkin.",
        bestFor: "Junien katselu julkiselta paikalta.",
        safetyNote: "Pysy julkisella kulkualueella. Älä mene raiteille tai ratapihalle."
      }
    ];

    const triangleIcon = L.divIcon({
      className: "",
      html: '<div class="triangle-marker"></div>',
      iconSize: [22, 20],
      iconAnchor: [11, 20],
      popupAnchor: [0, -18]
    });

    function escapeHtml(value) {
      if (value === null || value === undefined) return "";
      return String(value)
        .replaceAll("&", "&amp;")
        .replaceAll("<", "&lt;")
        .replaceAll(">", "&gt;")
        .replaceAll('"', "&quot;")
        .replaceAll("'", "&#039;");
    }

    function toggleInfo() {
      const panel = document.getElementById("infoPanel");
      panel.style.display = panel.style.display === "block" ? "none" : "block";
    }

    function formatTime(timestamp) {
      if (!timestamp) return "ei tiedossa";
      return new Date(timestamp).toLocaleString("fi-FI");
    }

    function formatShortTime(timestamp) {
      if (!timestamp) return "ei tiedossa";

      return new Date(timestamp).toLocaleTimeString("fi-FI", {
        hour: "2-digit",
        minute: "2-digit"
      });
    }

    function getStationName(shortCode) {
      if (!shortCode) return "ei tiedossa";
      return stationNames.get(shortCode) || shortCode;
    }

    function getSpeedStatus(speed) {
      if (speed === null || speed === undefined) {
        return {
          label: "nopeus ei tiedossa",
          color: "#888"
        };
      }

      if (speed === 0) {
        return {
          label: "pysähtynyt",
          color: "#e84b4b"
        };
      }

      return {
        label: "liikkeessä",
        color: "#4be86e"
      };
    }

    function getDestination(train) {
      const rows = (train.timeTableRows || []).filter(row => row.cancelled !== true);

      if (rows.length === 0) return null;

      const lastRow = rows[rows.length - 1];

      return {
        stationShortCode: lastRow.stationShortCode,
        stationName: getStationName(lastRow.stationShortCode)
      };
    }

    function getNextStop(train) {
      const rows = train.timeTableRows || [];
      const now = new Date();

      const candidates = rows
        .filter(row => row.type === "ARRIVAL")
        .filter(row => row.cancelled !== true)
        .filter(row => row.trainStopping === true)
        .filter(row => !row.actualTime)
        .map(row => {
          const timeValue = row.liveEstimateTime || row.scheduledTime;

          return {
            stationShortCode: row.stationShortCode,
            stationName: getStationName(row.stationShortCode),
            scheduledTime: row.scheduledTime,
            liveEstimateTime: row.liveEstimateTime,
            unknownDelay: row.unknownDelay,
            differenceInMinutes: row.differenceInMinutes,
            timeValue,
            time: timeValue ? new Date(timeValue) : null
          };
        })
        .filter(row => row.time && row.time >= new Date(now.getTime() - 5 * 60 * 1000))
        .sort((a, b) => a.time - b.time);

      return candidates.length > 0 ? candidates[0] : null;
    }

    function getNextDeparture(train) {
      const rows = train.timeTableRows || [];
      const now = new Date();

      const candidates = rows
        .filter(row => row.type === "DEPARTURE")
        .filter(row => row.cancelled !== true)
        .filter(row => !row.actualTime)
        .map(row => {
          const timeValue = row.liveEstimateTime || row.scheduledTime;

          return {
            stationShortCode: row.stationShortCode,
            stationName: getStationName(row.stationShortCode),
            scheduledTime: row.scheduledTime,
            liveEstimateTime: row.liveEstimateTime,
            unknownDelay: row.unknownDelay,
            differenceInMinutes: row.differenceInMinutes,
            timeValue,
            time: timeValue ? new Date(timeValue) : null
          };
        })
        .filter(row => row.time && row.time >= new Date(now.getTime() - 5 * 60 * 1000))
        .sort((a, b) => a.time - b.time);

      return candidates.length > 0 ? candidates[0] : null;
    }

    function formatStopInfo(stop) {
      if (!stop) return "Ei tulevaa pysähdystä tiedossa";

      if (stop.unknownDelay) {
        return `${escapeHtml(stop.stationName)}<br>Saapumisarvio: myöhässä, ei luotettavaa arviota`;
      }

      const source = stop.liveEstimateTime ? "ennuste" : "aikataulu";
      const delay =
        stop.differenceInMinutes !== null &&
        stop.differenceInMinutes !== undefined
          ? `, ${stop.differenceInMinutes} min`
          : "";

      return `${escapeHtml(stop.stationName)}<br>Saapuu: ${formatShortTime(stop.timeValue)} (${source}${delay})`;
    }

    function formatDepartureInfo(departure) {
      if (!departure) return "Ei tulevaa lähtöaikaa tiedossa";

      if (departure.unknownDelay) {
        return `${escapeHtml(departure.stationName)}<br>Lähtöarvio: myöhässä, ei luotettavaa arviota`;
      }

      const source = departure.liveEstimateTime ? "ennuste" : "aikataulu";
      const delay =
        departure.differenceInMinutes !== null &&
        departure.differenceInMinutes !== undefined
          ? `, ${departure.differenceInMinutes} min`
          : "";

      return `${escapeHtml(departure.stationName)}<br>Lähtö: ${formatShortTime(departure.timeValue)} (${source}${delay})`;
    }

    function distanceInMeters(lat1, lon1, lat2, lon2) {
      const R = 6371000;
      const toRad = value => value * Math.PI / 180;

      const dLat = toRad(lat2 - lat1);
      const dLon = toRad(lon2 - lon1);

      const a =
        Math.sin(dLat / 2) * Math.sin(dLat / 2) +
        Math.cos(toRad(lat1)) * Math.cos(toRad(lat2)) *
        Math.sin(dLon / 2) * Math.sin(dLon / 2);

      const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));

      return R * c;
    }

    function formatDistance(meters) {
      if (meters < 1000) {
        return `${Math.round(meters)} m`;
      }

      return `${(meters / 1000).toFixed(1)} km`;
    }

    function getNearestViewingSpot(lat, lon) {
      if (viewingSpots.length === 0) return null;

      let nearest = null;
      let nearestDistance = Infinity;

      viewingSpots.forEach(spot => {
        const distance = distanceInMeters(lat, lon, spot.lat, spot.lon);

        if (distance < nearestDistance) {
          nearest = spot;
          nearestDistance = distance;
        }
      });

      return {
        spot: nearest,
        distance: nearestDistance
      };
    }

    function openDirectionsToSpot(lat, lon) {
      const url = `https://www.google.com/maps/dir/?api=1&destination=${lat},${lon}`;
      window.open(url, "_blank");
    }

    window.openDirectionsToSpot = openDirectionsToSpot;

    async function loadStationMetadata() {
      try {
        const response = await fetch(`${API}/metadata/stations`);
        const stations = await response.json();

        stations.forEach(station => {
          stationNames.set(station.stationShortCode, station.stationName);
        });
      } catch (error) {
        console.warn("Liikennepaikkojen nimien lataus epäonnistui.", error);
      }
    }

    async function loadCargoTrains() {
      const status = document.getElementById("status");

      try {
        status.textContent = "Haetaan aktiivisia tavarajunia ja GPS-sijaintejä...";

        const [trainsResponse, locationsResponse] = await Promise.all([
          fetch(`${API}/live-trains`),
          fetch(`${API}/train-locations.geojson/latest`)
        ]);

        const trains = await trainsResponse.json();
        const locations = await locationsResponse.json();

        const cargoTrains = trains.filter(train =>
          train.trainCategory === "Cargo" && train.cancelled !== true
        );

        const cargoByKey = new Map();

        cargoTrains.forEach(train => {
          const key = `${train.trainNumber}-${train.departureDate}`;
          cargoByKey.set(key, train);
        });

        latestCargoData = [];

        locations.features.forEach(feature => {
          const props = feature.properties;
          const coords = feature.geometry.coordinates;

          const key = `${props.trainNumber}-${props.departureDate}`;
          const train = cargoByKey.get(key);

          if (!train) return;

          const latitude = coords[1];
          const longitude = coords[0];

          const destination = getDestination(train);
          const nextStop = getNextStop(train);
          const nextDeparture = getNextDeparture(train);
          const nearestViewingSpot = getNearestViewingSpot(latitude, longitude);

          latestCargoData.push({
            key,
            trainNumber: props.trainNumber,
            departureDate: props.departureDate,
            longitude,
            latitude,
            speed: props.speed,
            accuracy: props.accuracy,
            timestamp: props.timestamp,
            operatorShortCode: train.operatorShortCode,
            trainType: train.trainType,
            destination,
            nextStop,
            nextDeparture,
            nearestViewingSpot
          });
        });

        renderMarkers();
        renderStaticLayers();

      } catch (error) {
        console.error(error);
        status.textContent = "Datan lataus epäonnistui.";
      }
    }

    function renderMarkers() {
      const status = document.getElementById("status");
      const searchValue = document.getElementById("searchInput").value.trim();
      const stoppedOnly = document.getElementById("stoppedOnly").checked;

      trainLayer.clearLayers();

      let filteredData = latestCargoData;

      if (searchValue) {
        filteredData = filteredData.filter(item =>
          String(item.trainNumber).includes(searchValue)
        );
      }

      if (stoppedOnly) {
        filteredData = filteredData.filter(item => item.speed === 0);
      }

      filteredData.forEach(item => {
        const speedStatus = getSpeedStatus(item.speed);

        const nearest = item.nearestViewingSpot;
        const nearestSpot = nearest ? nearest.spot : null;

        const directionsButton = nearestSpot
          ? `<button onclick="openDirectionsToSpot(${nearestSpot.lat}, ${nearestSpot.lon})">
               Avaa reitti lähimmälle katselupaikalle
             </button>`
          : "";

        const nearestInfo = nearestSpot
          ? `${escapeHtml(nearestSpot.name)}<br>Etäisyys linnuntietä: ${formatDistance(nearest.distance)}`
          : "Ei katselupaikkaa tiedossa";

        const marker = L.circleMarker([item.latitude, item.longitude], {
          radius: item.key === followedTrainKey ? 11 : 7,
          weight: item.key === followedTrainKey ? 4 : 2,
          color: speedStatus.color,
          fillColor: speedStatus.color,
          fillOpacity: 0.85
        });

        marker.bindPopup(`
          <div class="cargo-popup">
            <strong>Tavarajuna ${escapeHtml(item.trainNumber)}</strong><br>
            Tila: ${escapeHtml(speedStatus.label)}<br>
            Nopeus: ${item.speed ?? "ei tiedossa"} km/h<br>
            Päivitetty: ${formatTime(item.timestamp)}<br><br>

            <strong>Määränpää</strong><br>
            ${item.destination ? escapeHtml(item.destination.stationName) : "Ei tiedossa"}<br><br>

            <strong>Seuraava pysähdys</strong><br>
            ${formatStopInfo(item.nextStop)}<br><br>

            <strong>Seuraava lähtö</strong><br>
            ${formatDepartureInfo(item.nextDeparture)}<br><br>

            <strong>Operaattori</strong><br>
            ${escapeHtml(item.operatorShortCode || "ei tiedossa")}<br><br>

            <strong>Junatyyppi</strong><br>
            ${escapeHtml(item.trainType || "ei tiedossa")}<br><br>

            <strong>Lähin katselupaikka</strong><br>
            ${nearestInfo}<br><br>

            ${directionsButton}

            <div class="popup-note">
              Reitti avataan vain katselupaikalle, ei junan sijaintiin.
              Katso junia vain julkiselta ja turvalliselta paikalta.
            </div>
          </div>
        `);

        marker.on("click", () => {
          followedTrainKey = item.key;
        });

        marker.addTo(trainLayer);
      });

      const stoppedCount = latestCargoData.filter(item => item.speed === 0).length;
      const movingCount = latestCargoData.filter(item =>
        item.speed !== null &&
        item.speed !== undefined &&
        item.speed > 0
      ).length;

      status.textContent =
        `Kartalla näkyy ${filteredData.length} cargoa. Pysähtyneitä: ${stoppedCount}. Liikkeessä: ${movingCount}. Päivitetty ${new Date().toLocaleTimeString("fi-FI")}.`;
    }

    function renderStaticLayers() {
      const showYards = document.getElementById("showYards").checked;
      const showSpots = document.getElementById("showSpots").checked;

      yardLayer.clearLayers();
      spotLayer.clearLayers();

      if (showYards) {
        railYards.forEach(yard => {
          const circle = L.circle([yard.lat, yard.lon], {
            radius: yard.radius,
            color: "#4bb3ff",
            fillColor: "#4bb3ff",
            fillOpacity: 0.08,
            weight: 2
          });

          circle.bindPopup(`
            <div class="yard-popup">
              <strong>${escapeHtml(yard.name)}</strong><br>
              Ratapiha, hahmottava alue.<br><br>
              Tämä ei ole katselupaikka. Reittiohjeitä ei anneta ratapihalle.
            </div>
          `);

          circle.addTo(yardLayer);
        });
      }

      if (showSpots) {
        viewingSpots.forEach(spot => {
          const marker = L.marker([spot.lat, spot.lon], {
            icon: triangleIcon
          });

          marker.bindPopup(`
            <div class="spot-popup">
              <strong>${escapeHtml(spot.name)}</strong><br>
              Tyyppi: ${escapeHtml(spot.type)}<br><br>
              ${escapeHtml(spot.description)}<br><br>

              <strong>Saapuminen</strong><br>
              ${escapeHtml(spot.access)}<br><br>

              <strong>Sopii</strong><br>
              ${escapeHtml(spot.bestFor)}<br><br>

              <strong>Turvallisuus</strong><br>
              ${escapeHtml(spot.safetyNote)}<br><br>

              <button onclick="openDirectionsToSpot(${spot.lat}, ${spot.lon})">
                Avaa reitti katselupaikalle
              </button>

              <div class="popup-note">
                Reitti vie vain tähän katselupaikkaan. Älä mene raiteille, ratapihalle tai aidatuille alueille.
              </div>
            </div>
          `);

          marker.addTo(spotLayer);
        });
      }
    }

    function applyFilters() {
      renderMarkers();
    }

    function clearFilters() {
      document.getElementById("searchInput").value = "";
      document.getElementById("stoppedOnly").checked = false;
      followedTrainKey = null;
      renderMarkers();
    }

    async function init() {
      await loadStationMetadata();
      await loadCargoTrains();

      setInterval(loadCargoTrains, 30000);
    }

    init();
  </script>
</body>
</html>
