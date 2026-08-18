# sabrinis-dashboard

Dashboard interno de Sabrini's Royal Treats (Walmart Canada), publicado con GitHub Pages.

El HTML no contiene datos: los lee en vivo de un Google Sheet vía gviz CSV.
Para conectarlo, pegá el ID del Sheet en la constante `SHEET_ID` al inicio del
`<script>` en `index.html`. El Sheet debe estar como "cualquiera con el link
puede ver", con estas pestañas:

| Pestaña | Columnas |
|---|---|
| `Verdict` | Section, Headline, Body, Tone (good/warn/bad) |
| `SKU_Sales` | SKU, Name, Species, ItemID, Status, Units_90d, Units_Boom, Units_PreBoom, Pct_Catalog, Price, Reviews, Signal |
| `Price_Cadence` | Date, Units_Day, Price_Era, Event |
| `Blockers` | Item, Type, Detail, Owner, Status, Priority |
| `PPC_Campaigns` | Campaign, CampaignID, Type, Status, Budget_Day, Spend_Real, Impressions, Clicks, CTR, Orders, Sales, RoAS, Note |
| `Actions` | Date, Title, Detail, Status, Week |

Alternativa: dejar `SHEET_ID` vacío y completar las 6 URLs de `CSV_URLS` con
"Publicar en la web -> CSV".

## Regla de datos

El Sheet es público e indexable. **No** debe contener montos de deuda de billing,
COGS ni márgenes. Billing se registra como estado, sin cifra. El render tiene una
red de seguridad (`scrubMoney`) que tapa montos en campos sensibles, pero es una
red, no un permiso.

Actualizar el Sheet y recargar la página alcanza: solo los cambios de estructura
requieren tocar el HTML.
