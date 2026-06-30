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

## Map Credits

Map tiles and labels are provided by Esri, OpenStreetMap contributors, and CARTO. Attribution is shown on the page.

## Final Mobile Behavior

- iPhone/mobile uses the real Leaflet map markers in a dedicated reservoir selection area before the dashboard cards.
- The mobile map is locked in place and fitted so all reservoir markers remain visible in portrait and landscape.
- Mobile map attribution is shown in the reservoir selection area for readability.
- The mobile background map stays fixed while scrolling, while reservoir markers remain tappable and open the existing detail panel.
- iPad and desktop keep the standard desktop layout.
