<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dashboard Flota Vehicular - Dolmen SA ESP</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Roboto', sans-serif; }
  body { background: #e8e8e8; padding: 20px; }
  .dashboard-container { max-width: 1280px; margin: 0 auto; background: #fff; box-shadow: 0 2px 12px rgba(0,0,0,0.15); border-radius: 6px; overflow: hidden; }
  .dash-header { background: #1C1C1B; color: #FFCC00; text-align: center; padding: 14px 16px 10px; }
  .dash-header h1 { font-size: 20px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; }
  .dash-header p { font-size: 12px; color: #CCCCCC; margin-top: 3px; font-weight: 400; }
  .kpi-bar { background: #2a2a29; display: flex; gap: 12px; padding: 12px 16px; align-items: center; flex-wrap: wrap; }
  .kpi-btn { background: #EB8020; color: #fff; border: none; padding: 9px 16px; font-size: 11px; font-weight: 700; border-radius: 4px; text-align: center; min-width: 140px; cursor: default; text-transform: uppercase; letter-spacing: 0.5px; }
  .kpi-btn span { display: block; font-size: 18px; font-weight: 700; margin-top: 3px; letter-spacing: 0; text-transform: none; }
  .kpi-btn small { display: block; font-size: 9px; font-weight: 400; opacity: 0.9; margin-top: 2px; text-transform: none; }
  .kpi-fecha { margin-left: auto; color: #CCCCCC; font-size: 12px; }
  .kpi-fecha strong { color: #FFCC00; font-weight: 500; }
  .filters { background: #f7f6f1; padding: 10px 16px; display: flex; gap: 12px; flex-wrap: wrap; align-items: flex-end; border-bottom: 2px solid #FFCC00; }
  .filter-group { display: flex; flex-direction: column; gap: 3px; }
  .filter-group label { font-size: 10px; color: #1C1C1B; font-weight: 700; text-transform: uppercase; letter-spacing: 0.4px; }
  .filter-group select { font-size: 11px; padding: 5px 8px; border: 1px solid #CCCCCC; border-radius: 3px; background: #fff; min-width: 130px; color: #1C1C1B; font-family: 'Roboto', sans-serif; cursor: pointer; }
  .filter-group select:focus { outline: 2px solid #FFCC00; border-color: #EB8020; }
  .btn-clear { background: #1C1C1B; color: #FFCC00; border: none; padding: 6px 12px; font-size: 11px; font-weight: 700; border-radius: 3px; cursor: pointer; align-self: flex-end; text-transform: uppercase; font-family: 'Roboto', sans-serif; }
  .btn-clear:hover { background: #333; }
  .metrics-row { display: flex; gap: 10px; padding: 12px 16px; background: #fff; flex-wrap: wrap; }
  .metric-card { background: #f7f6f1; border-left: 3px solid #FFCC00; border-radius: 0 4px 4px 0; padding: 9px 14px; flex: 1; min-width: 140px; }
  .metric-card .label { font-size: 10px; color: #666; font-weight: 700; text-transform: uppercase; letter-spacing: 0.4px; }
  .metric-card .value { font-size: 18px; font-weight: 700; color: #1C1C1B; margin-top: 3px; }
  .charts-row { display: flex; gap: 0; padding: 0 16px 12px; background: #fff; }
  .chart-box { flex: 1; min-width: 0; }
  .chart-title-row { display: flex; align-items: stretch; margin-bottom: 8px; }
  .chart-title-row h3 { font-size: 11px; font-weight: 700; padding: 7px 14px; letter-spacing: 1px; text-transform: uppercase; flex: 1; display: flex; align-items: center; color: #fff; }
  .h3-naranja { background: #EB8020; }
  .h3-amarillo { background: #c9a000; }
  .btn-ver-todo { background: #1C1C1B; color: #FFCC00; border: none; padding: 0 13px; font-size: 10px; font-weight: 700; cursor: pointer; white-space: nowrap; text-transform: uppercase; font-family: 'Roboto', sans-serif; }
  .btn-ver-todo:hover { background: #333; }
  .bottom-row { display: flex; gap: 10px; padding: 0 16px 16px; background: #fff; }
  .details-box { flex: 0 0 215px; border: 1px solid #e0e0e0; border-top: 3px solid #EB8020; border-radius: 0 0 4px 4px; padding: 11px; }
  .details-box h4 { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.5px; color: #1C1C1B; margin-bottom: 9px; }
  .details-box table { width: 100%; font-size: 11px; }
  .details-box td { padding: 3px 2px; color: #333; vertical-align: top; }
  .details-box td:first-child { color: #666; font-weight: 500; width: 55%; }
  .pie-box { flex: 0 0 195px; border: 1px solid #e0e0e0; border-top: 3px solid #FFCC00; border-radius: 0 0 4px 4px; padding: 11px; }
  .pie-box h4 { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.5px; color: #1C1C1B; margin-bottom: 9px; text-align: center; }
  .obs-box { flex: 1; border: 1px solid #e0e0e0; border-top: 3px solid #1C1C1B; border-radius: 0 0 4px 4px; padding: 11px; background: #fafaf8; }
  .obs-box h4 { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 0.5px; color: #1C1C1B; margin-bottom: 9px; }
  .obs-box p { font-size: 11.5px; color: #444; line-height: 1.6; }
  .modal-overlay { display: none; position: fixed; inset: 0; background: rgba(28,28,27,0.65); z-index: 1000; align-items: center; justify-content: center; }
  .modal-overlay.visible { display: flex; }
  .modal-box { background: #fff; border-radius: 4px; width: 560px; max-width: 96vw; max-height: 82vh; display: flex; flex-direction: column; box-shadow: 0 8px 32px rgba(0,0,0,0.3); }
  .modal-header { background: #EB8020; color: #fff; padding: 12px 18px; display: flex; align-items: center; justify-content: space-between; border-radius: 4px 4px 0 0; }
  .modal-header h3 { font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; }
  .modal-close { background: none; border: none; color: #fff; font-size: 20px; cursor: pointer; line-height: 1; font-family: 'Roboto', sans-serif; }
  .modal-close:hover { opacity: 0.7; }
  .modal-body { overflow-y: auto; flex: 1; }
  .modal-table { width: 100%; border-collapse: collapse; font-size: 11.5px; }
  .modal-table thead th { background: #f7f6f1; color: #1C1C1B; font-weight: 700; padding: 9px 11px; border-bottom: 2px solid #EB8020; text-align: left; position: sticky; top: 0; font-size: 10px; text-transform: uppercase; letter-spacing: 0.3px; }
  .modal-table thead th.num { text-align: right; }
  .modal-table tbody tr:nth-child(even) { background: #fafaf8; }
  .modal-table tbody tr:hover { background: #fff3e0; }
  .modal-table tbody td { padding: 7px 11px; border-bottom: 1px solid #eee; color: #333; }
  .modal-table tbody td.num { text-align: right; font-weight: 700; color: #1C1C1B; }
  .modal-table tbody td.rank { text-align: center; color: #999; font-weight: 500; width: 32px; font-size: 10px; }
  .bar-mini { height: 8px; border-radius: 2px; display: inline-block; vertical-align: middle; background: #EB8020; }
  .modal-footer { padding: 9px 18px; border-top: 1px solid #e0e0e0; font-size: 10px; color: #888; font-weight: 500; text-align: right; background: #f7f6f1; border-radius: 0 0 4px 4px; text-transform: uppercase; letter-spacing: 0.3px; }
  .badge-top { font-size: 9px; font-weight: 700; padding: 2px 7px; border-radius: 2px; margin-left: 6px; vertical-align: middle; text-transform: uppercase; }
  .badge-1 { background: #EB8020; color: #fff; }
  .badge-2 { background: #c9a000; color: #fff; }
  .badge-3 { background: #e0e0e0; color: #555; }
</style>
</head>
<body>

<div class="dashboard-container">
  <div class="dash-header">
    <h1>Vehículos</h1>
    <p>Dashboard de actividades SIG VEHÍCULOS</p>
  </div>

  <div class="kpi-bar">
    <div class="kpi-btn">Actividades<span id="kpi-act">—</span><small>total actividades</small></div>
    <div class="kpi-btn">Vehículos<span id="kpi-veh">—</span><small>total vehículos</small></div>
    <div class="kpi-btn">Proyección<span id="kpi-proy">—</span><small>6 meses</small></div>
    <div class="kpi-fecha">A la fecha de: <strong id="kpi-fecha"></strong></div>
  </div>

  <div class="filters">
    <div class="filter-group"><label>Centro de costos</label><select id="f-proceso"></select></div>
    <div class="filter-group"><label>Mes</label><select id="f-mes"><option value="Enero">Enero</option></select></div>
    <div class="filter-group"><label>Tipo vehículo</label><select id="f-tipo"></select></div>
    <div class="filter-group"><label>Placa</label><select id="f-placa"></select></div>
    <button class="btn-clear" onclick="clearFilters()">Limpiar filtros</button>
  </div>

  <div class="metrics-row">
    <div class="metric-card"><div class="label">Total actividades</div><div class="value" id="m-act">—</div></div>
    <div class="metric-card"><div class="label">Costos</div><div class="value" id="m-cost">—</div></div>
    <div class="metric-card"><div class="label">Placa seleccionada</div><div class="value" id="m-placa">—</div></div>
    <div class="metric-card"><div class="label">Total vehículos</div><div class="value" id="m-veh">—</div></div>
  </div>

  <div class="charts-row">
    <div class="chart-box">
      <div class="chart-title-row">
        <h3 class="h3-naranja">KM Recorridos</h3>
        <button class="btn-ver-todo" onclick="openModal()">Ver todos ▼</button>
      </div>
      <div style="position:relative;width:100%;height:320px;"><canvas id="chartKm"></canvas></div>
    </div>
    <div class="chart-box" style="margin-left:14px;">
      <div class="chart-title-row"><h3 class="h3-amarillo">Galones Consumidos</h3></div>
      <div style="position:relative;width:100%;height:320px;"><canvas id="chartGal"></canvas></div>
    </div>
  </div>

  <div class="bottom-row">
    <div class="details-box">
      <h4>Detalles</h4>
      <table>
        <tr><td>Conductor asignado</td><td id="d-conductor">----</td></tr>
        <tr><td>Tipo vehículo</td><td id="d-tipo">----</td></tr>
        <tr><td>Km recorrido</td><td id="d-km">----</td></tr>
        <tr><td>Galones consumidos</td><td id="d-gal">----</td></tr>
        <tr><td>Rendimiento real</td><td id="d-rend">----</td></tr>
        <tr><td>Costo mensual</td><td id="d-costo">----</td></tr>
        <tr><td>Ubicación</td><td id="d-loc">----</td></tr>
        <tr><td>Estado</td><td id="d-estado">----</td></tr>
      </table>
    </div>
    <div class="pie-box">
      <h4>Tipos de vehículos</h4>
      <div style="position:relative;width:100%;height:140px;"><canvas id="chartPie"></canvas></div>
      <div id="pie-legend" style="margin-top:8px;font-size:10px;"></div>
    </div>
    <div class="obs-box">
      <h4>Observación</h4>
      <p id="obs-text">Haga clic en una barra de la gráfica o seleccione una placa para ver el análisis del vehículo, incluyendo los municipios visitados y las observaciones del mes.</p>
    </div>
  </div>
</div>

<div class="modal-overlay" id="modalKm" role="dialog" aria-modal="true">
  <div class="modal-box">
    <div class="modal-header">
      <h3>KM Recorridos — Listado completo</h3>
      <button class="modal-close" onclick="closeModal()">✕</button>
    </div>
    <div class="modal-body">
      <table class="modal-table">
        <thead><tr><th class="rank">#</th><th>Placa</th><th>Tipo</th><th>Conductor</th><th class="num">KM Recorridos</th><th style="width:90px;">Relativo</th></tr></thead>
        <tbody id="modal-tbody"></tbody>
      </table>
    </div>
    <div class="modal-footer" id="modal-footer"></div>
  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/chartjs-plugin-datalabels/2.2.0/chartjs-plugin-datalabels.min.js"></script>
<script>
Chart.register(ChartDataLabels);

const RAW = [{"placa":"ENZ337","tipo":"4X4","combustible":61.49,"km":1835.65,"kmGalon":29.85,"costos":725260,"observaciones":"Recorridos Atlántico/Viajes Barranquilla - Maicao","proceso":"Servicios Administrativos","localidad":"Barranquilla","conductor":"Luis Viloria","estado":"Operativo"},{"placa":"EUZ476","tipo":"CANASTA","combustible":40.71,"km":440.87,"kmGalon":10.83,"costos":425738,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Soledad","conductor":"Estiver Garcia","estado":"Operativo"},{"placa":"FRX606","tipo":"4X4","combustible":32.39,"km":645.09,"kmGalon":19.92,"costos":349163,"observaciones":"Viaje Puerto Wilches - Cimitarra/Recorridos Santander","proceso":"IU","localidad":"Cimitarra","conductor":"José Vides","estado":"Operativo"},{"placa":"FRY530","tipo":"4X4","combustible":56.39,"km":1026.89,"kmGalon":18.21,"costos":624500,"observaciones":"Recorridos Santander","proceso":"IU","localidad":"Barbosa","conductor":"Kevin Camacho","estado":"Operativo"},{"placa":"GZV986","tipo":"4X4","combustible":51.08,"km":870.87,"kmGalon":17.05,"costos":563921,"observaciones":"Recorridos Santander","proceso":"IU","localidad":"San Vicente de Chucuri","conductor":"Christian Serrano","estado":"Operativo - Pendiente reparación de defensa delantera"},{"placa":"GZW253","tipo":"4X4","combustible":52.92,"km":984.28,"kmGalon":18.6,"costos":584236,"observaciones":"Viaje Puerto Wilches - San Vicente de Chucurí/Recorridos Santander","proceso":"IU","localidad":"San Vicente de Chucuri","conductor":"José León","estado":"Operativo - Panoramico trasero partido"},{"placa":"GZW292","tipo":"4X4","combustible":26.66,"km":445.19,"kmGalon":16.7,"costos":248933,"observaciones":"Viajes Uribia - Maicao/Recorridos Uribia","proceso":"IU","localidad":"Uribia","conductor":"Juan Roys","estado":"Operativo"},{"placa":"HBL335","tipo":"ESTACA","combustible":17.87,"km":491.14,"kmGalon":27.48,"costos":185690,"observaciones":"Recorridos Ciénaga/Viaje Ciénaga - Fundación","proceso":"IU","localidad":"Cienaga","conductor":"Michael Castellar","estado":"Operativo"},{"placa":"HBL339","tipo":"ESTACA","combustible":19.66,"km":597.26,"kmGalon":30.38,"costos":205005,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Soledad","conductor":"Dorly Gutierrez","estado":"Operativo"},{"placa":"HBL341","tipo":"ESTACA","combustible":9.6,"km":274.05,"kmGalon":28.55,"costos":100078,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Soledad","conductor":"Sin conductor","estado":"Operativo"},{"placa":"HBS065","tipo":"ESTACA","combustible":35.06,"km":904.48,"kmGalon":25.8,"costos":366746,"observaciones":"Recorridos Atlántico","proceso":"IU","localidad":"Tubara","conductor":"Brayan Merino","estado":"Operativo"},{"placa":"HXL508","tipo":"ESTACA","combustible":43.64,"km":998.97,"kmGalon":22.89,"costos":455002,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Malambo","conductor":"Luis Mejía","estado":"Operativo. Pendiente duplicado de placa."},{"placa":"HXL518","tipo":"ESTACA","combustible":69.88,"km":1208.46,"kmGalon":17.29,"costos":685041,"observaciones":"Viaje Pailitas - Astrea/Recorridos Cesar/Recorridos Magdalena/Viaje Pailitas - Guamal","proceso":"IU","localidad":"Pailitas","conductor":"Harold Nieto","estado":"Operativo"},{"placa":"HXL519","tipo":"ESTACA","combustible":32,"km":1105.7,"kmGalon":34.55,"costos":300000,"observaciones":"Recorridos Dibulla - Mingueo - Palomino/Recorridos Guajira","proceso":"IU","localidad":"Dibulla","conductor":"Dairo Villero","estado":"Operativo"},{"placa":"HXL522","tipo":"ESTACA","combustible":28.95,"km":890.72,"kmGalon":30.77,"costos":304952,"observaciones":"Viaje San Vicente de Chucurí - Soledad","proceso":"AU","localidad":"Soledad","conductor":"Sin conductor","estado":"En taller por reparación de estaca."},{"placa":"IEP642","tipo":"ESTACA","combustible":29.47,"km":703.11,"kmGalon":23.86,"costos":308638,"observaciones":"Recorridos Atlántico","proceso":"IU","localidad":"Malambo","conductor":"Julien Vargas","estado":"Operativo"},{"placa":"IEP643","tipo":"ESTACA","combustible":45.14,"km":1322.53,"kmGalon":29.3,"costos":480839,"observaciones":"Recorridos Santa Catalina","proceso":"IU","localidad":"Santa catalina","conductor":"Julio Hernandez","estado":"Operativo"},{"placa":"IEP644","tipo":"ESTACA","combustible":26.21,"km":634.06,"kmGalon":24.19,"costos":272304,"observaciones":"Recorridos Ciénaga/Viaje Ciénaga - Plato","proceso":"AU","localidad":"Cienaga","conductor":"Moises Ochoa","estado":"Operativo"},{"placa":"IET807","tipo":"ESTACA","combustible":11.64,"km":169.97,"kmGalon":14.6,"costos":121349,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Sabanagrande","conductor":"Sin conductor","estado":"Fuga en tanque de combustible"},{"placa":"IET808","tipo":"ESTACA","combustible":33.76,"km":552.35,"kmGalon":16.36,"costos":353333,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Soledad","conductor":"Manuel Pua","estado":"Operativo"},{"placa":"IET809","tipo":"ESTACA","combustible":29.2,"km":344.79,"kmGalon":11.81,"costos":315360,"observaciones":"Recorridos Maicao","proceso":"IU","localidad":"Maicao","conductor":"Edgar Diaz","estado":"Operativo"},{"placa":"ISP641","tipo":"ESTACA","combustible":17.38,"km":341.78,"kmGalon":19.67,"costos":181169,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Soledad","conductor":"Sin conductor","estado":"Operativo - Pendiente duplicado de placa."},{"placa":"JRZ866","tipo":"VAN","combustible":50.45,"km":1199.97,"kmGalon":23.79,"costos":812329,"observaciones":"Recorridos Atlántico - Seguimiento proyecto Aeropuerto Ernesto Cortissoz","proceso":"Servicios Administrativos","localidad":"Barranquilla","conductor":"Fabio Aníbal","estado":"Operativo"},{"placa":"KYX309","tipo":"4X4","combustible":90.81,"km":2358.51,"kmGalon":25.97,"costos":1019774,"observaciones":"Viajes Barranquilla - Cienaga/Barranquilla - Maicao/Barranquilla Santa Catalina/Barranquilla - Sitionuevo","proceso":"Servicios Administrativos","localidad":"Barranquilla","conductor":"Laureano Ripoll","estado":"Operativo"},{"placa":"KZV968","tipo":"CANASTA","combustible":183.04,"km":585.85,"kmGalon":3.2,"costos":1940650,"observaciones":"Recorridos Guajira","proceso":"IU","localidad":"Maicao","conductor":"Wilmer Carrillo","estado":"Operativo"},{"placa":"KZV970","tipo":"CANASTA","combustible":53.86,"km":240.62,"kmGalon":4.47,"costos":564202,"observaciones":"Traslado Mnto PTVO Soledad - Recorridos Atlántico","proceso":"IU","localidad":"Sabanagrande","conductor":"Gustavo Perez","estado":"Operativo"},{"placa":"LLU812","tipo":"4X4","combustible":55,"km":1381.88,"kmGalon":25.13,"costos":602563,"observaciones":"Recorridos Magdalena - Cesar - Sucre","proceso":"IU","localidad":"Plato","conductor":"Daniel Nuñez","estado":"Operativo"},{"placa":"LPZ218","tipo":"CANASTA","combustible":32.8,"km":479.52,"kmGalon":14.62,"costos":360403,"observaciones":"Viaje Cáqueza - La Calera/Recorridos La Calera","proceso":"IU","localidad":"La Calera","conductor":"Sin conductor","estado":"Operativo"},{"placa":"LPZ219","tipo":"CANASTA","combustible":112.24,"km":1283.92,"kmGalon":11.44,"costos":1220079,"observaciones":"Recorridos Santander","proceso":"IU","localidad":"Barbosa","conductor":"Eduar Matiz","estado":"Operativo"},{"placa":"LWQ586","tipo":"VAN","combustible":16.53,"km":598.29,"kmGalon":36.19,"costos":200142,"observaciones":"Recorridos Atlántico/ Viajes Barranquilla - Ciénaga","proceso":"Direccion General","localidad":"Barranquilla","conductor":"Luis Viloria","estado":"Operativo"},{"placa":"LWW701","tipo":"4X4","combustible":46.46,"km":1128.91,"kmGalon":24.3,"costos":485466,"observaciones":"Recorridos Sitionuevo - Cerro de San Antonio - Piñón","proceso":"IU","localidad":"Sabanagrande/Satelite","conductor":"Roberto Miranda","estado":"Operativo"},{"placa":"MHW422","tipo":"ESTACA","combustible":26.44,"km":814.97,"kmGalon":30.82,"costos":276303,"observaciones":"Recorridos Atlántico/ Viaje Soledad - Ciénaga","proceso":"AU","localidad":"Soledad","conductor":"Pedro Sánchez","estado":"Operativo"},{"placa":"MHX980","tipo":"ESTACA","combustible":25.85,"km":532.4,"kmGalon":20.6,"costos":270793,"observaciones":"Recorridos Atlántico","proceso":"IU","localidad":"Santo Tomas","conductor":"Yerwin Paz","estado":"Operativo"},{"placa":"MHY540","tipo":"ESTACA","combustible":34.39,"km":990.79,"kmGalon":28.81,"costos":359893,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Soledad","conductor":"Brayann Valera","estado":"Operativo"},{"placa":"NBK698","tipo":"VAN","combustible":3.18,"km":0.06,"kmGalon":0.02,"costos":50000,"observaciones":"Sin programación","proceso":"UT SEVIMAG","localidad":"Sevimag","conductor":"Sin conductor","estado":"Operativo"},{"placa":"NBK699","tipo":"ESTACA","combustible":13.4,"km":277.51,"kmGalon":20.71,"costos":150000,"observaciones":"Recorridos Barbosa","proceso":"AU","localidad":"Cienaga","conductor":"Carlos Ramirez","estado":"Operativo"},{"placa":"NUL090","tipo":"4X4","combustible":27.6,"km":535.3,"kmGalon":19.39,"costos":292480,"observaciones":"Recorridos Puerto Wilches","proceso":"IU","localidad":"Puerto Wilches","conductor":"Wilson Ortiz","estado":"Operativo"},{"placa":"NUM225","tipo":"4X4","combustible":0,"km":88.6,"kmGalon":0,"costos":0,"observaciones":"Recorridos Cáqueza","proceso":"IU","localidad":"Cáqueza","conductor":"Nelson Ramirez","estado":"Operativo"},{"placa":"OQR551","tipo":"ESTACA","combustible":29.92,"km":1177.26,"kmGalon":39.35,"costos":317194,"observaciones":"Recorridos Cesar - Magdalena/Viaje Pailitas - Cimitarra","proceso":"IU","localidad":"Pailitas","conductor":"Harold Nieto","estado":"Operativo"},{"placa":"OQR554","tipo":"ESTACA","combustible":35.6,"km":957.98,"kmGalon":26.91,"costos":384480,"observaciones":"Recorridos Maicao/Viaje Maicao - La Jagua Del Pilar","proceso":"IU","localidad":"Maicao","conductor":"Alberto Altahona","estado":"Operativo"},{"placa":"OQR557","tipo":"ESTACA","combustible":16.38,"km":406.59,"kmGalon":24.82,"costos":170384,"observaciones":"Recorridos Ciénaga/Viajes Ciénaga - Soledad","proceso":"AU","localidad":"Soledad","conductor":"Pedro Medina","estado":"Operativo"},{"placa":"OQR558","tipo":"ESTACA","combustible":34.86,"km":831.09,"kmGalon":23.84,"costos":365040,"observaciones":"Viaje Fundación - El Retén/Fundación - El Difícil/Recorridos Fundación","proceso":"IU","localidad":"Fundacion","conductor":"Gilberto Saurith","estado":"Operativo"},{"placa":"OQR559","tipo":"ESTACA","combustible":22.76,"km":746.42,"kmGalon":32.8,"costos":237267,"observaciones":"Recorridos Atlántico","proceso":"AU","localidad":"Malambo","conductor":"Rafael Gonzalez","estado":"Operativo"},{"placa":"POV151","tipo":"4X4","combustible":5.79,"km":188.69,"kmGalon":32.59,"costos":63268,"observaciones":"Recorridos La Calera","proceso":"IU","localidad":"La Calera","conductor":"Diego Velasquez","estado":"Operativo"},{"placa":"PWN875","tipo":"ESTACA","combustible":15.96,"km":246.7,"kmGalon":15.46,"costos":166394,"observaciones":"Recorridos Atlántico","proceso":"IU","localidad":"Santo Tomas","conductor":"Yerwin Paz","estado":"Operativo"},{"placa":"WGX358","tipo":"CANASTA","combustible":85.93,"km":548.17,"kmGalon":6.38,"costos":898749,"observaciones":"Recorridos Atlántico","proceso":"IU","localidad":"Malambo","conductor":"Estiver Garcia","estado":"Operativo"},{"placa":"WGX366","tipo":"CANASTA","combustible":26.61,"km":83.44,"kmGalon":3.14,"costos":280081,"observaciones":"Recorridos Atlántico","proceso":"IU","localidad":"Sabanagrande","conductor":"Gustavo Perez","estado":"Pendiente reparación del vaso"}];

let chartKm=null, chartGal=null, chartPie=null, currentFiltered=[...RAW];
const COLOR_KM='#EB8020', COLOR_GAL='#FFCC00';
const PIE_COLORS=['#EB8020','#FFCC00','#1C1C1B','#c9a000','#f0a050','#e6b800'];

function fmt(n){ return Math.round(n).toLocaleString('es-CO'); }
function fmtCOP(n){ return '$'+Math.round(n).toLocaleString('es-CO'); }

function makeGradient(ctx, chartArea, hexColor){
  if(!chartArea) return hexColor;
  const grad=ctx.createLinearGradient(chartArea.left,0,chartArea.right,0);
  const r=parseInt(hexColor.slice(1,3),16),g=parseInt(hexColor.slice(3,5),16),b=parseInt(hexColor.slice(5,7),16);
  const rd=Math.max(0,r-40),gd=Math.max(0,g-40),bd=Math.max(0,b-40);
  grad.addColorStop(0,`rgb(${rd},${gd},${bd})`);
  grad.addColorStop(1,`rgb(${r},${g},${b})`);
  return grad;
}

function setSelect(el,options,selectedVal){
  el.innerHTML='';
  options.forEach(o=>{ const opt=document.createElement('option'); opt.value=o.val; opt.textContent=o.label; if(o.val===selectedVal) opt.selected=true; el.appendChild(opt); });
}

function rebuildFilters(){
  const fP=document.getElementById('f-proceso'),fT=document.getElementById('f-tipo'),fPl=document.getElementById('f-placa');
  const sP=fP.value,sT=fT.value,sPl=fPl.value;
  const byP=sP?RAW.filter(r=>r.proceso===sP):RAW;
  const tiposDisp=[...new Set(byP.map(r=>r.tipo))].sort();
  const tVal=tiposDisp.includes(sT)?sT:'';
  const byT=tVal?byP.filter(r=>r.tipo===tVal):byP;
  const placasDisp=[...new Set(byT.map(r=>r.placa))].sort();
  const pVal=placasDisp.includes(sPl)?sPl:'';
  setSelect(fT,[{val:'',label:'Lista (Todos)'},...tiposDisp.map(t=>({val:t,label:t}))],tVal);
  setSelect(fPl,[{val:'',label:'Lista placa'},...placasDisp.map(p=>({val:p,label:p}))],pVal);
  updateDash();
}

function getFiltered(){
  const p=document.getElementById('f-proceso').value,t=document.getElementById('f-tipo').value,pl=document.getElementById('f-placa').value;
  return RAW.filter(r=>(!p||r.proceso===p)&&(!t||r.tipo===t)&&(!pl||r.placa===pl));
}

function buildBarChart(canvasId,labels,values,unit,baseColor,clickCb){
  const canvas=document.getElementById(canvasId);
  const maxVal=Math.max(...values,1);
  return new Chart(canvas,{
    type:'bar',
    data:{ labels, datasets:[{ label:unit, data:values, backgroundColor:baseColor, borderRadius:3 }] },
    options:{
      indexAxis:'y', responsive:true, maintainAspectRatio:false,
      layout:{ padding:{ right:65 } },
      animation:{
        onComplete:function(){
          const ca=this.chartArea; if(!ca) return;
          this.data.datasets[0].backgroundColor=makeGradient(canvas.getContext('2d'),ca,baseColor);
          this.update('none');
        }
      },
      plugins:{
        legend:{ display:false },
        tooltip:{ enabled:true, callbacks:{ label:ctx=>fmt(ctx.raw)+' '+unit } },
        datalabels:{
          anchor:'end', align:'end', color:'#1C1C1B',
          font:{ size:10, family:'Roboto', weight:'700' },
          formatter:(val)=>unit==='km'?fmt(val):val.toFixed(1),
          clip:false
        }
      },
      scales:{
        x:{ max:maxVal*1.2, ticks:{ font:{size:10,family:'Roboto'}, callback:v=>unit==='km'?fmt(v):v.toFixed(0) }, grid:{ color:'rgba(0,0,0,0.05)' } },
        y:{ ticks:{ font:{size:10,family:'Roboto',weight:'500'} } }
      },
      onClick:clickCb
    }
  });
}

function updateDash(){
  const data=getFiltered(); currentFiltered=data;
  const totalVeh=[...new Set(data.map(r=>r.placa))].length;
  const totalCost=data.reduce((s,r)=>s+r.costos,0);
  const placaSel=document.getElementById('f-placa').value;
  document.getElementById('kpi-act').textContent=data.length;
  document.getElementById('kpi-veh').textContent=totalVeh;
  document.getElementById('kpi-proy').textContent=fmtCOP(totalCost*6);
  document.getElementById('m-act').textContent=data.length;
  document.getElementById('m-cost').textContent=fmtCOP(totalCost);
  document.getElementById('m-placa').textContent=placaSel||'—';
  document.getElementById('m-veh').textContent=totalVeh;
  const top10km=[...data].sort((a,b)=>b.km-a.km).slice(0,10);
  const top10gal=[...data].sort((a,b)=>b.combustible-a.combustible).slice(0,10);
  document.querySelector('#chartKm').parentElement.style.height=Math.max(top10km.length*40+60,160)+'px';
  document.querySelector('#chartGal').parentElement.style.height=Math.max(top10gal.length*40+60,160)+'px';
  if(chartKm) chartKm.destroy();
  chartKm=buildBarChart('chartKm',top10km.map(r=>r.placa),top10km.map(r=>r.km),'km',COLOR_KM,(e,els)=>{ if(els.length) showDetail(top10km[els[0].index]); });
  if(chartGal) chartGal.destroy();
  chartGal=buildBarChart('chartGal',top10gal.map(r=>r.placa),top10gal.map(r=>r.combustible),'gal',COLOR_GAL,(e,els)=>{ if(els.length) showDetail(top10gal[els[0].index]); });
  const tipoCount={};
  data.forEach(r=>{ tipoCount[r.tipo]=(tipoCount[r.tipo]||0)+1; });
  const tipos=Object.keys(tipoCount);
  if(chartPie) chartPie.destroy();
  chartPie=new Chart(document.getElementById('chartPie'),{
    type:'pie',
    data:{ labels:tipos, datasets:[{ data:tipos.map(t=>tipoCount[t]), backgroundColor:PIE_COLORS.slice(0,tipos.length) }] },
    options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{display:false}, datalabels:{display:false}, tooltip:{callbacks:{label:ctx=>ctx.label+': '+ctx.raw}} } }
  });
  document.getElementById('pie-legend').innerHTML=tipos.map((t,i)=>`<span style="display:inline-flex;align-items:center;gap:4px;margin-right:8px;margin-bottom:3px;"><span style="width:10px;height:10px;border-radius:2px;background:${PIE_COLORS[i]};display:inline-block;border:1px solid rgba(0,0,0,0.1);"></span><span style="color:#333;font-weight:500;font-size:10px;">${t}: ${tipoCount[t]}</span></span>`).join('');
  if(placaSel){ const v=data.find(r=>r.placa===placaSel); if(v) showDetail(v); }
}

function showDetail(v){
  document.getElementById('d-conductor').textContent=v.conductor;
  document.getElementById('d-tipo').textContent=v.tipo;
  document.getElementById('d-km').textContent=fmt(v.km)+' km';
  document.getElementById('d-gal').textContent=v.combustible.toFixed(2)+' gal';
  document.getElementById('d-rend').textContent=v.kmGalon.toFixed(2)+' km/gal';
  document.getElementById('d-costo').textContent=fmtCOP(v.costos);
  document.getElementById('d-loc').textContent=v.localidad;
  const esT=v.estado&&(v.estado.toLowerCase().includes('taller')||v.estado.toLowerCase().includes('fuga'));
  document.getElementById('d-estado').innerHTML=esT?`<span style="color:#c0392b;font-weight:700;">${v.estado}</span>`:`<span style="color:#1a7a4a;font-weight:500;">${v.estado}</span>`;
  document.getElementById('obs-text').textContent=v.observaciones||'Sin observaciones registradas.';
}

function openModal(){
  const sorted=[...currentFiltered].sort((a,b)=>b.km-a.km);
  const maxKm=sorted.length>0?sorted[0].km:1;
  document.getElementById('modal-tbody').innerHTML=sorted.map((v,i)=>{
    const pct=Math.round((v.km/maxKm)*75);
    const badgeMap={0:'<span class="badge-top badge-1">Top 1</span>',1:'<span class="badge-top badge-2">Top 2</span>',2:'<span class="badge-top badge-3">Top 3</span>'};
    return `<tr${i===0?' style="background:#fff3e0;"':''}>
      <td class="rank">${i+1}</td>
      <td><strong>${v.placa}</strong>${i<3?badgeMap[i]:''}</td>
      <td style="color:#666;">${v.tipo}</td>
      <td style="color:#555;">${v.conductor}</td>
      <td class="num">${fmt(v.km)} km</td>
      <td><span class="bar-mini" style="width:${pct}px;"></span></td>
    </tr>`;
  }).join('');
  const totalKm=sorted.reduce((s,r)=>s+r.km,0);
  document.getElementById('modal-footer').textContent=`${sorted.length} vehículos · Total: ${fmt(totalKm)} km recorridos`;
  document.getElementById('modalKm').classList.add('visible');
}

function closeModal(){ document.getElementById('modalKm').classList.remove('visible'); }
document.getElementById('modalKm').addEventListener('click',function(e){ if(e.target===this) closeModal(); });

function clearFilters(){
  document.getElementById('f-proceso').value='';
  document.getElementById('f-tipo').value='';
  document.getElementById('f-placa').value='';
  rebuildFilters();
  ['d-conductor','d-tipo','d-km','d-gal','d-rend','d-costo','d-loc','d-estado'].forEach(id=>document.getElementById(id).textContent='----');
  document.getElementById('obs-text').textContent='Haga clic en una barra de la gráfica o seleccione una placa para ver el análisis del vehículo, incluyendo los municipios visitados y las observaciones del mes.';
}

const procesosAll=[...new Set(RAW.map(r=>r.proceso))].sort();
const fpEl=document.getElementById('f-proceso');
[{val:'',label:'Listado (Todos)'},...procesosAll.map(p=>({val:p,label:p}))].forEach(o=>{ const opt=document.createElement('option'); opt.value=o.val; opt.textContent=o.label; fpEl.appendChild(opt); });
['f-proceso','f-tipo','f-placa'].forEach(id=>document.getElementById(id).addEventListener('change',rebuildFilters));
document.getElementById('kpi-fecha').textContent=new Date().toLocaleDateString('es-CO',{day:'2-digit',month:'long',year:'numeric'});
rebuildFilters();
</script>
</body>
</html>
