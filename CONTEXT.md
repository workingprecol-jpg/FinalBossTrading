# Contexto del proyecto Final Boss

Actualizado el **2 de octubre de 2026**. Este archivo es el punto de entrada
para retomar el proyecto en futuras sesiones. Las observaciones de ejecución
son instantáneas; consultar el estado actual antes de actuar.

## Objetivo y decisión del usuario

El usuario pidió que el bot **no ejecute ninguna operación ni trade**: debe
buscar información para ayudarle a decidir manualmente si entrar ahora o esperar,
y explorar diferentes monedas con potencial de fuertes aumentos de precio,
incluidas memecoins y tokens DEX. No limitar la búsqueda a los cuatro contratos
del motor anterior. No afirmar que se cubren todas las monedas ni garantizar
qué moneda va a subir explosivamente.

La operación actual es **solo análisis**. Se prohíben trades reales, Demo y paper.
No reactivar el motor, sus tareas ni simulaciones como parte de un arranque
rutinario. El comando heredado `python -m bot run` está bloqueado en código,
incluso con otra configuración, `--mode demo`, otro directorio o Docker.
`ANALYSIS_ONLY` registra esta política; eliminar ese archivo no habilita órdenes.
Las decisiones de entrada corresponden al usuario.

Solicitud anterior: mostrar la moneda y qué condiciones deben cumplirse para
una entrada spot, long o short; incluir siempre BTC, ETH (Ethereum), SOL y otras
monedas principales. No llamar «segura» a una entrada ni ocultar requisitos
pendientes. Long/short son escenarios informativos de futuros, nunca órdenes.

Solicitud de ampliación: «Let's add those», autorizando ampliar análisis técnico,
posicionamiento, ballenas, riesgos, descubrimiento e historial. Conservar el
diseño claro actual. Estas funciones ya están implementadas; proveedores
opcionales sin clave muestran estado desconocido, no datos ficticios.

Solicitud del 26 de septiembre: ejecutar la auditoría del agente analista financiero.
Se aplicó el perfil XML de `agents/analista-financiero.md` y se guardó el informe
en `reports/auditorias/2026-09-26_105100_analista-financiero.md`, con evidencia
reproducible y propuestas priorizadas. No se implementaron correcciones.

Solicitud del 28 de septiembre: añadir un título por moneda indicando posible
continuidad bajista/bearish o alcista/bullish y fechas. Implementado en el detalle
del radar con contexto propio EMA20/50 de 1h/4h/1d y precio observado. Muestra
sesgos en conflicto o desconocidos cuando corresponde; el lado spot/long/short
no determina la tendencia. Fechas de revisión a 1h/4h/24h desde la observación,
en Colombia, sin estimación validada de duración ni fecha de reversión.
Datos antiguos/desconectados y DEX sin series no reciben fechas inventadas.
No cambia las reglas de entrada, consultas, historial ni tareas de Windows.
Validación de esta ampliación: 30 pruebas JavaScript aprobadas; comprobación
del panel activo, fechas Colombia, desplegables conservados al actualizar y DEX
sin series. Sin errores de consola observados. Captura del detalle en
`reports/ui/2026-09-28_continuidad.jpg`.

Solicitudes posteriores: publicar el proyecto en GitHub (completado el 30 de
septiembre), explicar las fuentes sin configurar y la viabilidad de ampliar
proveedores (1 de octubre), y guardar el contexto actualizado en este archivo
(2 de octubre). La conversación sobre fuentes fue una revisión y recomendaciones;
no autorizó contratar servicios, configurar claves ni añadir proveedores.

## Repositorio y publicación — 30 de septiembre de 2026

Repositorio: [workingprecol-jpg/Investigador_Market](https://github.com/workingprecol-jpg/Investigador_Market).
Remoto `origin`: `https://github.com/workingprecol-jpg/Investigador_Market.git`.
Rama local `main`, con seguimiento de `origin/main`.

La carpeta local no tenía metadatos Git. Se inicializó Git y se tomó como base
el commit remoto `8e0785d5e4b00d6b0efbaea1f87da8b1a1b0d369`, que solo contenía
un archivo `Test` de un byte. Se conservó ese archivo y se incorporaron 76
archivos de código, pruebas, configuración y documentación, sin eliminar
archivos remotos.

Commit creado y subido correctamente a `main`:
[`de3e2fb13c9899371ce19d2dc166237d786c1186`](https://github.com/workingprecol-jpg/Investigador_Market/commit/de3e2fb13c9899371ce19d2dc166237d786c1186),
mensaje **Add analysis-only crypto market radar**, autor `Codex`.
Antes de publicar pasaron **318 pruebas Python y 30 JavaScript**, la revisión
del diff y una búsqueda de patrones de secretos sin coincidencias.
`.gitignore` excluye `.env`, `data/`, `reports/`, logs, entorno virtual y cachés;
`.env.example` solo contiene campos vacíos de claves. No se publicaron bases
operativas ni reportes generados. Las auditorías y capturas enlazadas aquí son
archivos locales ignorados por Git; no asumir que están disponibles en GitHub.

Git en el sandbox puede detectar propietario distinto o negar escritura en
`.git`. Se usó `git -c safe.directory=D:/BotTradingFinalBoss ...` por comando,
sin cambiar la confianza global. Las escrituras de metadatos y el acceso de red
requirieron ejecución fuera del sandbox. El push funcionó seleccionando la
credencial existente de `workingprecol-jpg` con
`-c credential.username=workingprecol-jpg -c credential.interactive=never`;
no se guardaron tokens en el proyecto ni en este documento.

Al guardar este contexto el 2 de octubre, la lectura local seguía mostrando
`main...origin/main` y ese commit como HEAD; no se consultó de nuevo el remoto.
Esta edición de `CONTEXT.md` es un cambio local posterior a la publicación.

## Revisión de fuentes y ampliación — 1 de octubre de 2026

Se leyó el panel y el código para explicar «Sin configurar» frente a «Parcial».
Instantánea consultada: **2026-10-01 10:34:41 Colombia**, estado `ok`, datos
vigentes en ese momento. CoinDesk RSS, Binance Spot y GoPlus estaban disponibles;
Binance Futures, DEX Screener y la muestra pública BTC tenían cobertura parcial.
Spot completó 42/42 análisis, futuros 41/42 y DEX obtuvo 2 tokens de 10 consultas.
Son cifras históricas de un ciclo, no el estado actual del 2 de octubre.

Tres integraciones seguían sin configurar porque no tenían clave en el entorno
del proceso: CoinGecko, Whale Alert y CoinGlass (calendario de desbloqueos).
El scanner no carga `.env`; escribir allí una clave no activa estas fuentes.
«Parcial» no implica que falte una clave: puede reflejar consultas incompletas,
mercados sin datos suficientes o alcance limitado por diseño. La muestra BTC
cubre hasta diez transacciones pendientes, sin atribuir dueños ni compra/venta.

Condiciones verificadas en fuentes oficiales el 1 de octubre; volver a consultar
antes de contratar, porque planes, límites y precios pueden cambiar:

- **CoinGecko:** capitalización y FDV de monedas principales por ID. Demo
  gratuito, hasta 10.000 llamadas mensuales según los
  [planes oficiales](https://www.coingecko.com/en/api/pricing).
  Fue la primera integración recomendada para activar.
- **Whale Alert:** la implementación actual usa Enterprise REST para transferencias
  atribuidas. La [documentación oficial](https://developer.whale-alert.io/api-account/documentation)
  anunciaba Enterprise a US$699/mes y Alerts a US$29,95/mes, con posibles impuestos.
  Alerts usa WebSocket y no es compatible directamente con el adaptador REST
  actual: requiere adaptación de código. Se recomendó posponerlo por coste.
- **CoinGlass:** el [endpoint de desbloqueos](https://docs.coinglass.com/reference/coin-unlock-list)
  requiere Startup o superior; Hobbyist no tiene acceso. Se recomendó valorarlo
  después, si el calendario aporta información útil. No se verificó un precio
  de suscripción ni se contrató un plan.

La ampliación es técnicamente viable si cada proveedor aporta evidencia distinta.
La recomendación práctica fue empezar con 6–8 proveedores bien elegidos, no como
límite técnico ni garantía de mejores señales. Binance Spot y Futures son dos
mercados del mismo proveedor; el número de filas del panel no equivale al número
de fuentes independientes.

Pendientes propuestos, todavía sin implementar por esta conversación:

- Activar CoinGecko mediante configuración local y evaluar una segunda fuente
  independiente de noticias para corroboración.
- Corregir fallos de consultas y manejo de límites antes de añadir proveedores,
  incluido **AF-03** de la auditoría anterior.
- Separar frecuencias por fuente, añadir caché y pausas tras errores, y evitar
  que un proveedor complementario lento retrase la publicación del análisis.
  Actualmente algunas consultas complementarias comparten el ciclo del scanner.
- Conservar fecha, procedencia e identidad del activo; deduplicar noticias y
  contratos para no contar información repetida como confirmación independiente.

No se configuraron claves, no se añadieron fuentes y no se cambiaron reglas de
entrada, tareas ni código de producción como resultado de esta revisión.

## Implementación actual

Se creó `agents/analista-financiero.md`, perfil XML en español de un agente
analista financiero y auditor de toda la plataforma. Activación manual mediante
una solicitud de auditoría; este archivo no inicia un proceso ni una tarea.
Define revisión de datos, indicadores, señales, futuros, DEX, ballenas, historial,
interfaz y operación, con evidencia reproducible y mejoras priorizadas.
Las auditorías se guardan en `reports/auditorias/`. Solo lectura operativa;
sin trades, cambios de criterios, acceso a secretos ni alteración del historial.
La primera auditoría ya se ejecutó; ver el resumen y enlace al informe abajo.

- Python 3.11+ y biblioteca estándar; proyecto en `D:\BotTradingFinalBoss`.
- `bot/scanner.py`: consultas públicas GET, selección del universo, indicadores,
  noticias y señales informativas. No carga `.env`, no necesita API keys ni
  accede a una cuenta o al motor de ejecución.
- `bot/scanner.html`: radar claro en español, lista filtrable por moneda, red,
  contrato, fuente y decisión; detalle de evidencia, riesgos y niveles.
- `bot/market_research.py`: gráficos de cuatro intervalos, open interest y flujo
  taker, GoPlus, descubrimiento, grandes transacciones BTC y tres conexiones
  opcionales. No usa `bot/research.py`, que pertenece al sistema histórico.
- `bot/signal_history.py`: observaciones y revisión de hipótesis, sin posiciones,
  fills ni P&L. Base nueva `data/scanner.history.sqlite3`, separada del trading.
- `bot/dashboard.py`: servidor local de lectura compartido con el panel histórico;
  el modo `analysis` lee el informe del buscador. Rechaza solicitudes de escritura.
- `bot/__main__.py`: comandos `scan`, `scan-status` y `scan-dashboard`, y bloqueo
  del comando de trading `run`.
- `data/scanner.json`: resultado publicado de forma atómica; `scanner.lock`
  impide dos escritores. `data/scanner.log` conserva actividad y errores.
- `scripts/install-scanner.ps1`: instalación de dos tareas ocultas de Windows,
  inicio de sesión y reinicio al fallar. Admite `-Preview` y `-Start`.

## Fuentes, cobertura y frecuencia

Binance Spot: metadatos de mercados activos y cotizaciones públicas de pares
USDT; se excluyen algunas stablecoins conocidas. Preselección por volumen de
24h >=2 millones USDT y spread <=20 bps. Por ciclo se analizan velas cerradas
15m/1h de hasta 15 líderes de subida, otros 15 pares en rotación y seguimiento
fijo, deduplicados (máximo 46 por ciclo).

Seguimiento fijo en spot y futuros: BTC, ETH, SOL, BNB, XRP, ADA, DOGE, AVAX,
LINK, DOT, LTC, TRX, SUI, TON, WLD (Worldcoin) y PEPE. WLD se añadió el 2 de octubre
de 2026 al seguimiento fijo de ambos mercados y al identificador opcional de
CoinGecko (`worldcoin-wld`), con vinculación de titulares por Worldcoin/WLD.
Las monedas principales se muestran aunque
no estén entre los ganadores; si falta un mercado o falla su análisis, la fila
permanece en ESPERAR, sin precio ni niveles inventados.

Binance Futures: solo datos públicos de perpetuos USDT activos, con cotizaciones,
velas 15m/1h y funding propios. Analiza hasta ocho líderes alcistas, siete bajistas,
quince en rotación y los fijos (máximo 46). No inferir señal de futuros desde spot.
`1000PEPEUSDT` cotiza una unidad de 1.000 PEPE y mantiene el precio de ese contrato.
Distinguir siempre universo revisado de monedas analizadas en detalle.

DEX Screener: perfiles recientes y actualizados, deduplicados por red y dirección;
hasta 10 contratos por ciclo en rotación. No es un listado completo del mercado
ni una auditoría del token. Algunas consultas carecen de datos suficientes y
el panel muestra cobertura parcial.

CoinDesk RSS: titulares de hasta seis horas, con URL y fecha; la caché también
excluye titulares que envejecen. Vinculación limitada por palabras, sin lectura
del artículo completo ni corroboración independiente. Fuente fallida impide
señales de entrada spot, long y short. Ausencia de titulares específicos no demuestra ausencia
de riesgo. No se habilitó Grok ni ninguna API de pago.

El buscador espera cinco minutos después de terminar cada ciclo; el panel
consulta los resultados cada diez segundos. No confundir actualizar el panel
con ejecutar un nuevo escaneo. Datos de más de quince minutos o un ciclo fallido
invalidan señales de entrada; el navegador también las degrada al desconectarse.

## Ampliación de investigación

Gráficos cerrados 15m/1h/4h/1d con EMA20, volumen y VWAP aproximado de velas,
anclado al inicio de la serie descargada; ventana 30/60/100 y selector por teclado.
Contexto EMA20/50 de 1h/4h/1d; 4h/1d no cambian las reglas básicas de entrada.
Futuros muestra OI, variación 1h en unidades, cuota compradora/delta taker 1h y
funding histórico. OI no determina dirección ni identifica ballenas.

GoPlus consulta la dirección exacta del DEX; campos faltantes permanecen
desconocidos. Honeypot/imposibilidad de vender explícitos causan descarte.
Solana informa autoridades, sin prueba independiente de venta. Concentración
de hasta diez holders con exclusiones por etiquetas, sin auditoría; bloqueo
de liquidez del par permanece desconocido.

Ranking por actividad, fuerza 24h frente a BTC, aceleración de volumen y cambio
de liquidez cuando existe base anterior. Es una heurística, no una probabilidad.
DEX aporta market cap/FDV del par. Muestra pública BTC: diez transacciones
pendientes más recientes, sumas de salidas >=1 millón USD; incluye posible cambio
y no atribuye dueño, compra/venta ni exchanges. No cubre todas las ballenas.

Opcionales por variables de entorno del proceso, sin cargar `.env`:
`WHALE_ALERT_API_KEY` (REST Enterprise, flujos atribuidos BTC/ETH/SOL),
`COINGECKO_DEMO_API_KEY` (valoraciones principales por ID) y `COINGLASS_API_KEY`
(desbloqueos, acceso Startup+). Ninguna está configurada por esta sesión ni se
contrató servicio. Sin claves se muestra «Sin configurar». Tras configurarlas
localmente hay que reiniciar la única tarea del scanner para heredar el entorno.
Whale Alert y calendario no se han validado con una suscripción real.

Historial: guarda análisis 30 días e hipótesis únicas por mercado/lado/vela con
niveles originales. Revisiones 1h/4h/24h toleran 15 minutos; observaciones tardías
no rellenan resultados. Si una vela alcanza ambos niveles, orden desconocido.
Excursiones con cobertura parcial, variación bruta sin costes, nunca fills ni P&L.
Bases e informes históricos de trading intactos. Detalles en `docs/RESEARCH.md`.

## Significado de las decisiones

- `SPOT_CONDICIONAL`: escenario alcista spot; requisitos de tendencia 15m/1h,
  ruptura de resistencia, volumen relativo, RSI 50–70, precio actual y liquidez.
- `LONG_CONDICIONAL`: escenario alcista de su propio contrato de futuros, con
  esos requisitos y funding reciente no excesivamente adverso.
- `SHORT_CONDICIONAL`: escenario bajista del contrato, pérdida de soporte,
  RSI 30–50 y los demás filtros, incluido funding reciente.
- Las tres señales requieren todas sus condiciones. Cada escenario muestra
  checklist con valor observado, requisito y cumplido/pendiente. El sesgo es
  tentativo; no equivale a entrada. No son órdenes ni probabilidades de beneficio.
- `ESPERAR`: condiciones incompletas, movimiento extendido o datos sin confirmar.
- `DESCARTAR`: debilidad, liquidez insuficiente u otros filtros incumplidos.
- `INVESTIGAR`: token DEX con actividad; siguen pendientes contrato, holders,
  posibilidad de venta y demás riesgos. DEX nunca recibe señal de entrada.

Los niveles de entrada, invalidación y objetivo son referencias técnicas
(2 ATR, mínimo 0,5%; objetivo 2R bruto), sin órdenes ni costes incluidos.
Las puntuaciones son heurísticas sin validación de rentabilidad, no probabilidades;
las puntuaciones spot/futuros y DEX tampoco son comparables entre sí.
En spot/futuros la puntuación es el porcentaje de requisitos reunidos.
Short usa invalidación arriba y objetivo abajo; spot/long invierten esa dirección.
El panel muestra ambos escenarios de futuros de forma independiente.
Los criterios detallados están en `docs/SCANNER.md`.

## Operación y estado verificado

Panel: **http://127.0.0.1:8765/**. Se comprobó su funcionamiento, filtros,
vista de escritorio y móvil y ausencia de errores de consola.

Las últimas tareas verificadas fueron:

- `FinalBoss-scanner`: activa, proceso oculto del buscador.
- `FinalBoss-dashboard-analysis`: activa, panel de solo análisis.
- `FinalBoss-paper` y `FinalBoss-dashboard-paper`: deshabilitadas.

Se confirmó una sola instancia del buscador y ninguna instancia `-m bot run`.
No confiar en PIDs históricos: verificar identidad del proceso antes de usar uno.
No iniciar una instancia manual si ya la administra la tarea de Windows.
El PC debe permanecer encendido, conectado y sin suspensión.

Instantánea congelada para la auditoría: **2026-09-26 10:56:05 Colombia**,
esquema 3, estado `ok`, ejecución deshabilitada y 89 filas; 483 pares spot
revisados y 39 de 40 análisis completados; 526 contratos de futuros
revisados y 44 análisis completados; 4 tokens DEX de 10 consultas.
Binance Spot y DEX parciales; Binance Futures, CoinDesk y GoPlus disponibles
en esa instantánea. Historial leído con 1.201 análisis y 13 señales.
BTC, ETH y SOL aparecen en ambos mercados. Snapshot de 6.224.830 bytes.
El panel mostró después un ciclo de las 11:02:30 con ocho DEX analizados.
Estas observaciones pertenecen a ciclos distintos; consultar el estado actual
antes de actuar, sin tratar las cifras guardadas como datos en tiempo real.

```powershell
# Lectura del estado actual, sin consultas de mercado ni órdenes:
python -m bot scan-status
Get-Content -LiteralPath data/scanner.log -Tail 20
# Iniciar tareas ya instaladas, si no están activas:
Start-ScheduledTask -TaskName 'FinalBoss-scanner'
Start-ScheduledTask -TaskName 'FinalBoss-dashboard-analysis'
# Alternativa manual, solo cuando no hay otra instancia del buscador:
python -m bot scan --once
python -m bot scan
python -m bot scan-dashboard --port 8765
# Instalar/actualizar tareas cuando sea necesario:
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/install-scanner.ps1 -Start
```

Para detener el buscador continuo, usar `Stop-ScheduledTask -TaskName
'FinalBoss-scanner'`; no hay posiciones que liquidar en este modo. Esperar a que
termine antes de reiniciar para que libere el bloqueo. No usar `resume` ni los
lanzadores históricos de trading para poner en marcha el buscador.
Las consultas de mercado necesitan acceso normal de red; un sandbox sin sockets
puede impedirlas aunque las pruebas locales pasen.

## Validación y documentos

Validación completa anterior: **318 pruebas Python y 24 JavaScript aprobadas**;
pruebas del buscador cubren bloqueo de trading, endpoints públicos, velas abiertas,
huecos, señales invalidadas, identidad del token DEX, noticias recientes y panel
sin escrituras, selección fija, separación spot/futuros, bloqueo por funding
faltante/antiguo/adverso y niveles direccionales long/short. También se probó el
escaneo con datos públicos reales de los tres mercados.
La ampliación cubre EMA/VWAP causales, OI en unidades, flujo de intervalos
cerrados, contratos/autoridades GoPlus, identidad desconocida de transacciones,
aislamiento de headers, historial persistente y horizontes faltantes. También
se comprobó el panel real en 1440px y 390px: controles del gráfico y selector
de vela, métricas de futuros, riesgos Solana/EVM y calendario sin configurar.
Se corrigió la salida JSON de `scan-status` para consolas Windows cp1252;
conserva símbolos Unicode mediante escapes JSON válidos.
Esto valida comportamiento del software, no rentabilidad de señales.

En la auditoría posterior se ejecutaron **46 pruebas Python seleccionadas y
24 JavaScript**, todas aprobadas. No se repitieron los simuladores históricos
ni el test que invoca el CLI bloqueado `run`. Las reproducciones adicionales
detectaron casos que las pruebas existentes no cubrían.

```powershell
python -m unittest discover -q
node --test tests/test_dashboard_browser.js tests/test_report_browser.js tests/test_scanner_browser.js
```

`README.md`, `docs/SCANNER.md` y `docs/RESEARCH.md` documentan la operación actual.
`PROJECT_OVERVIEW.md` y `docs/DASHBOARD.md` señalan el cambio de alcance y
conservan referencias del sistema anterior. La dirección visual actual está en
`docs/SCANNER.md`; no se ha guardado una nueva `.interface-design/system.md`.

## Auditoría del analista financiero — 26 de septiembre de 2026

Informe: [auditoría financiera y técnica](reports/auditorias/2026-09-26_105100_analista-financiero.md).
Inventario de 71 archivos con huellas y estado de revisión por componente;
el flujo actual se inspeccionó con código, muestras, panel y pruebas aisladas.
Módulos históricos e integraciones opcionales tienen cobertura parcial explícita.
Las bases operativas se leyeron mediante SQLite `mode=ro`; sin cambios en código
de producción, criterios, tareas, snapshots activos ni historial.

Se confirmaron **8 inconsistencias: 2 P1, 5 P2 y 1 P3**:

- **AF-01, P1:** el booleano de vigencia del funding no caduca a los 180 segundos;
  backend y frontend conservan una entrada condicionada hasta el TTL general.
- **AF-02, P1:** el historial toma la fecha anterior de cotización como fecha de
  señal. ACEUSDT e ICPUSDT aparecen 8,069 segundos antes del cierre de su vela.
- **AF-03, P2:** un rate limit en consultas complementarias se absorbe como error
  genérico y permite seguir consultando esa fuente.
- **AF-04, P2:** un token DEX descartado por honeypot sigue elegible en descubrimiento.
- **AF-05, P2:** se puede presentar como crecimiento de liquidez un cambio de pool.
- **AF-06, P2:** un precio positivo como `1e-10` se representa como cero.
- **AF-07, P2:** el CLI heredado `research` conserva una ruta de simulación;
  hallazgo por lectura estática, sin ejecutar el comando.
- **AF-08, P3:** algunas guías históricas presentan paper/Demo como alcance vigente.

Prioridad propuesta: corregir AF-01/02 antes de usar el historial como validación
prospectiva; después robustez, ranking e identidad de pool. El informe incluye
criterios de aceptación y límites de evidencia. No se encontró P0 en el flujo
vigente inspeccionado; no se demostró rentabilidad ni precisión predictiva.
Las correcciones siguen pendientes de una petición de implementación.

La lectura de bases históricas encontró una posición paper almacenada en `trend`
y otra en `validation`; no demuestra procesos activos ni posiciones en una cuenta.
Se conservaron intactas. No confundir esos archivos con el historial del radar.

## Historia que debe conservarse

Antes del cambio existía un motor de futuros paper/Demo con revisión diaria,
experimentos y límites de riesgo. Se detuvo dejando paper sin posiciones ni
órdenes pendientes, con STOP solicitado. Sus bases SQLite, informes, pérdidas,
operaciones y configuración histórica permanecen intactos. No borrar datos
para ocultar pérdidas ni presentar resultados anteriores como evidencia de
rentabilidad del buscador actual. Las instrucciones antiguas de ejecución son
referencia histórica y no revocan la política de solo análisis.

No leer ni copiar valores de `.env` a este contexto, informes o chats.
