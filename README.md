# RY Water Intelligence Center

Final static landing page for Rayong water dashboards.

## Pages

- Water Dashboard: https://pabank10-png.github.io/water-dashboard/
- Rayong Rainfall Dashboard: https://pabank10-png.github.io/rayong-rainfall-dashboard/

## Data

The landing page loads latest reservoir values directly from RID public APIs:

```text
https://app.rid.go.th/reservoir/api/reservoir/public/
https://app.rid.go.th/reservoir/api/dam/public/
```

The browser stores the latest successful API response in `localStorage` and uses that cache if the RID APIs are temporarily unavailable.

### RID Data Fallback Rule

- The page fetches current RID API data first.
- It also fetches historical RID API data for the previous 7 days.
- Reservoir values are applied per reservoir, not as one global date.
- If a reservoir returns `volume = 0` or invalid data for the current API date, the page uses the newest previous day with `volume > 0` for that reservoir.
- The popup date displays the actual data date used by that reservoir.
- Static `index.html` default values are only used when both live API and local cache are unavailable.

## Reservoir Markers

- DK: อ่างเก็บน้ำดอกกราย
- NPL: อ่างเก็บน้ำหนองปลาไหล
- KY: อ่างเก็บน้ำคลองใหญ่
- PS: อ่างเก็บน้ำประแสร์
- BP: เขื่อนบางพระ
- NK: อ่างเก็บน้ำหนองค้อ
- PK: อ่างเก็บน้ำคลองประแกด
- HM: อ่างเก็บน้ำคลองหางแมว

Marker and water-bar colors are dynamic:

- Red: below 30% / วิกฤต
- Yellow: 30.01-50.00% / เฝ้าระวัง
- Green: above 50.00% / น้ำปกติ

## Final Map View

Desktop default map view is locked at:

```js
center: [12.9346, 101.377]
zoom: 10
```

iPad/tablet map view is locked separately at:

```js
center: [12.752, 101.135]
zoom: 10
```

Do not reuse the iPhone/mobile fit behavior for iPad. iPad should keep the desktop-style layout with the iPad-specific map center above.

## Map Credits

Map tiles and labels are provided by Esri, OpenStreetMap contributors, and CARTO. Attribution is shown on the page.

## Final Mobile Behavior

- iPhone/mobile uses the real Leaflet map markers in a dedicated reservoir selection area before the dashboard cards.
- The mobile map is locked in place and fitted so all reservoir markers remain visible in portrait and landscape.
- Mobile map attribution is shown in the reservoir selection area for readability.
- The mobile background map stays fixed while scrolling, while reservoir markers remain tappable and open the existing detail panel.
- iPad keeps the standard desktop layout, but uses the iPad-specific map view documented above.

## Update Log

### 2026-07-01

- Fixed iPad 13-inch map view so it matches the approved reference framing.
- Added per-reservoir RID fallback logic to prevent temporary `0` values on a new API date from replacing valid previous-day data.
- Confirmed RID historical endpoint pattern:

```text
https://app.rid.go.th/reservoir/api/reservoir/public/YYYY-MM-DD
https://app.rid.go.th/reservoir/api/dam/public/YYYY-MM-DD
```
