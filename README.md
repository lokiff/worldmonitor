# 🌍 WorldMonitor — Global Conflict Intelligence Dashboard

Dashboard OSINT de monitoreo geopolítico en tiempo real. Conflictos activos, noticias internacionales, canales Telegram de guerra y eventos GDELT — todo en un único archivo HTML, sin instalación, accesible desde cualquier navegador.

**🔗 Live:** [lokiff.github.io/worldmonitor](https://lokiff.github.io/worldmonitor)

---

## Características

### 🗺️ Mapa Interactivo
- Mapa oscuro Leaflet con tiles CartoDB
- **21 conflictos activos** (actualizados a marzo 2026) con 5 niveles de intensidad: CRÍTICO / ALTO / MEDIO / BAJO / LATENTE
- Marcadores animados con pulso según intensidad
- Popup con descripción táctica al hacer clic en cada conflicto
- Navegación por regiones: Global, Europa, MENA, África, Asia-Pac, Américas, Cáucaso
- Zoom y desplazamiento libre

### 📰 Panel de Medios (23 fuentes RSS)
Fuentes internacionales de referencia actualizadas automáticamente:

| Fuente | Categoría |
|---|---|
| BBC World, Al Jazeera, Reuters, AP News | General |
| NYT World, Guardian, Sky News, France 24, DW | General |
| ISW, Kyiv Independent, Meduza | Ucrania |
| Times of Israel, Middle East Eye | Oriente Medio |
| Bellingcat, Foreign Policy, Defense News, Breaking Defense | Análisis/Defensa |
| Africa Report, SCMP, Radio Free Asia | Regional |
| ICG, CFR | Geopolítica |

Filtros por región: Ucrania · M.Este · África · Asia · 🔴 Flash

### 📡 Panel OSINT / Telegram (15 canales)
Canales Telegram militares y de inteligencia vía RSS (rsshub.app):

| Canal | Enfoque |
|---|---|
| Rybar | Operaciones Rusia/Ucrania (fuente pro-rusa) |
| Intel Slava Z | Reportes militares Ucrania |
| OSINTdefender | OSINT global |
| GeoConfirmed | Geolocalización de conflictos |
| DeepState UA | Mapas de frente Ucrania |
| Intel Crab | Inteligencia global |
| War Monitor | Monitor conflictos |
| Quds News Network | Oriente Medio |
| Syria Map | Siria |
| Sahel Intelligence | África Occidental |
| + 5 canales adicionales | — |

### 🌐 Panel GDELT
- Consulta en tiempo real a la [GDELT API v2](https://www.gdeltproject.org/) (sin API key)
- Últimas 2 horas de eventos globales filtrados por conflicto
- Indicador de tono por noticia: 🔴 Negativo / ⚪ Neutral / 🟢 Positivo
- País de origen y dominio de cada fuente

### ⏱️ Auto-refresh
- Actualización automática cada **2 minutos** en los 3 paneles simultáneamente
- Contador regresivo visible en tiempo real
- Refresh manual disponible en cualquier momento

### 📺 Ticker de Titulares
- Barra de últimas noticias deslizante con los 15 titulares más recientes
- Se actualiza con cada ciclo de refresh

---

## Uso

Abre directamente en el navegador — no requiere instalación ni servidor:

```
https://lokiff.github.io/worldmonitor
```

O descarga `index.html` y ábrelo localmente (**requiere conexión a internet** para RSS y GDELT).

---

## Arquitectura técnica

```
index.html  (único archivo, ~980 líneas)
│
├── Leaflet.js          — mapa interactivo
├── CartoDB Dark tiles  — mapa base oscuro
├── allorigins.win      — proxy CORS principal para RSS
├── corsproxy.io        — proxy CORS fallback #1
├── codetabs.com        — proxy CORS fallback #2
├── rsshub.app          — convierte canales Telegram a RSS
└── GDELT API v2        — base de datos eventos globales
```

**Sin backend.** Todo corre en el navegador del cliente. Las peticiones externas se enrutan a través de proxies CORS públicos con sistema de fallback automático (si uno falla, prueba el siguiente).

---

## Conflictos monitoreados (Mar 2026)

| Conflicto | Intensidad | Región |
|---|---|---|
| Irán – Israel – EEUU | 🔴 CRÍTICO | Oriente Medio |
| Rusia – Ucrania | 🔴 ALTO | Europa Oriental |
| Israel – Gaza | 🔴 ALTO | Oriente Medio |
| Sudán – Guerra Civil | 🔴 ALTO | NE África |
| Myanmar – Guerra Civil | 🔴 ALTO | SE Asia |
| DRC – Congo Este | 🔴 ALTO | África Central |
| Sahel – Insurgencia | 🔴 ALTO | África Occ. |
| Haití – Pandillas | 🟠 ALTO | Caribe |
| Somalia – Al-Shabaab | 🟠 ALTO | Este África |
| Corea del Norte – Proxy | 🟠 ALTO | Este Asia |
| Estrecho de Taiwán | 🟡 MEDIO | Este Asia |
| Mar del Sur de China | 🟡 MEDIO | SE Asia |
| Yemen – Houthis | 🟡 MEDIO | Oriente Medio |
| Etiopía | 🟡 MEDIO | Este África |
| Mozambique | 🟡 MEDIO | África Sur. |
| Armenia – Azerbaiyán | 🟡 MEDIO | Cáucaso |
| Georgia – Crisis Política | 🟡 MEDIO | Cáucaso |
| Venezuela – Esequibo | 🔵 BAJO | Sudamérica |
| Pakistán – Baluchistán | 🔵 BAJO | Asia Sur |
| Sáhara Occidental | 🔵 BAJO | Norte África |
| Nigeria – Insurgencias | 🔵 BAJO | África Occ. |

---

## Limitaciones conocidas

- **Telegram vía rsshub.app**: el servicio es gratuito y puede estar saturado ocasionalmente. Si un canal no carga, los demás continúan funcionando con normalidad.
- **GDELT**: la API pública tiene límites de velocidad. Si no carga, reintenta automáticamente en el siguiente ciclo.
- **Proxies CORS**: servicios de terceros gratuitos. En caso de caída de los 3 simultáneamente, algunos feeds pueden no cargar hasta que se recuperen.
- **Datos de conflictos**: la información táctica está actualizada a **marzo 2026** y es estática (no se actualiza automáticamente con el mapa). Las noticias RSS sí son en tiempo real.

---

## Inspiración

Inspirado en [worldmonitor.app](https://github.com/koala73/worldmonitor) y [watchwar.live](https://watchwar.live).

---

## Licencia

MIT — uso libre para fines informativos y de investigación.
