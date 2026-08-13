<!DOCTYPE html>
<html lang="pt-BR">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Smart Soil</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    min-height:100vh;
    font-family:Arial,Helvetica,sans-serif;
    color:white;
    background:
        radial-gradient(circle at 20% 20%,rgba(46,204,113,.18),transparent 30%),
        radial-gradient(circle at 80% 80%,rgba(52,152,219,.15),transparent 30%),
        linear-gradient(135deg,#04130a,#0a2415,#06140c);
}

.tela{
    min-height:100vh;
    display:none;
    justify-content:center;
    align-items:center;
    padding:20px;
}

.tela.ativa{
    display:flex;
}

.inicio{
    width:100%;
    max-width:720px;
    text-align:center;
}

.logo{
    width:95px;
    height:95px;
    margin:0 auto 25px;
    border-radius:30px;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:50px;
    background:linear-gradient(135deg,#1f9d55,#2ecc71);
    box-shadow:0 15px 40px rgba(46,204,113,.25);
}

.inicio h1{
    font-size:44px;
    margin-bottom:12px;
}

.inicio p{
    color:#8eaa98;
    margin-bottom:40px;
}

/* MENU */

.menu{
    display:flex;
    flex-direction:column;
    gap:15px;
}

.menu-barra{
    width:100%;
    min-height:85px;
    padding:18px 24px;
    border-radius:20px;
    display:flex;
    align-items:center;
    gap:18px;
    text-align:left;
    cursor:pointer;
    background:rgba(255,255,255,.06);
    border:1px solid rgba(255,255,255,.1);
    transition:.25s ease;
}

.menu-barra:hover{
    transform:translateY(-4px);
    background:rgba(46,204,113,.12);
    border-color:rgba(46,204,113,.4);
    box-shadow:0 15px 35px rgba(46,204,113,.12);
}

.menu-icone{
    width:52px;
    height:52px;
    flex-shrink:0;
    border-radius:15px;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:25px;
    background:rgba(46,204,113,.15);
}

.menu-conteudo{
    flex:1;
}

.menu-conteudo h2{
    font-size:19px;
    margin-bottom:5px;
}

.menu-conteudo span{
    color:#819889;
    font-size:13px;
}

.seta{
    font-size:27px;
    color:#6edc93;
}

/* CONTAINER */

.container{
    width:100%;
    max-width:1050px;
}

.medidor-container{
    max-width:1400px;
}

/* TOPO */

.topo{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:25px;
}

.voltar{
    border:none;
    padding:12px 18px;
    border-radius:12px;
    color:white;
    background:rgba(255,255,255,.07);
    cursor:pointer;
    transition:.2s;
}

.voltar:hover{
    background:rgba(255,255,255,.15);
}

.titulo{
    font-size:25px;
    font-weight:bold;
}

/* CONEXÃO ARDUINO */

.conexao-arduino{
    margin-bottom:20px;
    padding:16px 20px;
    border-radius:18px;
    display:flex;
    align-items:center;
    gap:15px;
    flex-wrap:wrap;
    background:rgba(255,255,255,.05);
    border:1px solid rgba(255,255,255,.08);
}

.conexao-titulo{
    display:flex;
    align-items:center;
    gap:8px;
    font-weight:bold;
}

.status-conexao{
    display:flex;
    align-items:center;
    gap:8px;
    flex:1;
    color:#819889;
    font-size:14px;
}

.ponto-conexao{
    width:11px;
    height:11px;
    border-radius:50%;
    background:#ff4757;
}

.ponto-conexao.conectado{
    background:#2ecc71;
    box-shadow:0 0 12px rgba(46,204,113,.8);
}

.botao-arduino{
    border:none;
    padding:11px 17px;
    border-radius:12px;
    color:white;
    background:rgba(46,204,113,.18);
    border:1px solid rgba(46,204,113,.35);
    cursor:pointer;
    font-weight:bold;
}

.botao-arduino:hover{
    background:rgba(46,204,113,.3);
}

.botao-desconectar{
    background:rgba(255,71,87,.15);
    border-color:rgba(255,71,87,.3);
}

/* CARDS */

.card{
    padding:30px;
    border-radius:25px;
    background:rgba(255,255,255,.05);
    border:1px solid rgba(255,255,255,.08);
    backdrop-filter:blur(15px);
}

/* MEDIDOR */

.medidor-layout{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:18px;
}

.sensor-panel{
    min-height:585px;
    padding:30px 34px;
    border-radius:28px;
    overflow:hidden;
}

.sensor-heading{
    display:flex;
    justify-content:center;
    align-items:center;
    gap:14px;
    margin-bottom:12px;
}

.sensor-heading-icon{
    font-size:29px;
}

.sensor-heading h2{
    margin:0;
    font-size:23px;
}

.sensor-heading p{
    margin:8px 0 0;
    color:#8ca397;
    font-size:16px;
}

/* UMIDADE */

.umidade-panel .meter{
    width:330px;
    height:330px;
    margin:26px auto 25px;
}

.meter{
    border-radius:50%;
    display:flex;
    align-items:center;
    justify-content:center;
    position:relative;
    background:conic-gradient(
        #2ecc71 0deg,
        #2ecc71 180deg,
        rgba(255,255,255,.06) 180deg
    );
    transition:background .5s;
}

.meter::before{
    content:"";
    position:absolute;
    width:265px;
    height:265px;
    border-radius:50%;
    background:radial-gradient(
        circle,
        #10291a,
        #06130b
    );
}

.valor{
    position:relative;
    z-index:2;
    text-align:center;
}

.numero{
    font-size:78px;
    font-weight:bold;
}

.porcentagem{
    margin-top:-2px;
    font-size:25px;
    color:#d7e0da;
}

.meter-caption{
    margin-top:8px;
    color:#8ca397;
    font-size:15px;
    letter-spacing:1px;
}

.status{
    text-align:center;
    font-size:26px;
    font-weight:bold;
    margin-bottom:25px;
}

.barra-titulo{
    display:flex;
    justify-content:space-between;
    color:#819889;
    font-size:14px;
    margin-bottom:10px;
}

.barra{
    width:100%;
    height:17px;
    border-radius:20px;
    overflow:hidden;
    background:rgba(255,255,255,.07);
}

.barra-progresso{
    height:100%;
    width:50%;
    border-radius:20px;
    background:#2ecc71;
    transition:width .5s,background .3s;
}

/* TEMPERATURA */

.temperatura-panel{
    display:flex;
    flex-direction:column;
}

.temperatura-meter{
    width:340px;
    height:260px;
    margin:20px auto 2px;
    border-radius:50%;
    position:relative;
    background:conic-gradient(
        from 225deg,
        #ff7a00 0deg,
        #ff9f1c 230deg,
        rgba(255,255,255,.06) 230deg,
        rgba(255,255,255,.06) 270deg,
        transparent 270deg 360deg
    );
}

.temperatura-meter::before{
    content:"";
    position:absolute;
    width:265px;
    height:265px;
    top:35px;
    left:37px;
    border-radius:50%;
    background:#071a10;
}

.temperatura-valor{
    position:relative;
    z-index:2;
    text-align:center;
    margin-top:70px;
}

.temperatura-numero{
    font-size:62px;
    font-weight:bold;
    line-height:1;
}

.temperatura-unidade{
    color:#ff9d00;
    font-size:27px;
    font-weight:bold;
    margin-top:6px;
}

.temperatura-caption{
    margin-top:8px;
    color:#8ca397;
    font-size:15px;
}

.temperatura-status{
    text-align:center;
    font-size:18px;
    font-weight:bold;
    margin-top:15px;
}

/* GRÁFICO */

.temp-chart-box{
    position:relative;
    margin:0 auto;
    width:94%;
    height:238px;
    border:1px solid rgba(255,255,255,.08);
    border-radius:20px;
    background:rgba(255,255,255,.025);
    padding:17px 20px 12px 60px;
}

.temp-chart-title{
    color:#9aaea3;
    font-size:16px;
    margin-bottom:6px;
}

.temp-chart-wrap{
    position:relative;
    height:165px;
}

#graficoTemperatura{
    width:100%;
    height:100%;
    display:block;
}

.temp-y-labels{
    position:absolute;
    left:-48px;
    top:2px;
    bottom:0;
    display:flex;
    flex-direction:column;
    justify-content:space-between;
    color:#8ca397;
    font-size:12px;
}

.temp-x-labels{
    display:flex;
    justify-content:space-between;
    color:#8ca397;
    font-size:12px;
    margin-top:2px;
}

/* ANÁLISES */

.analises-card{
    grid-column:1 / -1;
    padding:24px 34px 20px;
}

.analises-titulo{
    display:flex;
    align-items:center;
    gap:10px;
    font-size:22px;
    font-weight:bold;
    margin-bottom:20px;
}

.analises-titulo span{
    font-size:26px;
}

.analises-grid{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:18px;
}

.info{
    padding:20px 24px;
    min-height:130px;
    border-radius:18px;
    background:rgba(255,255,255,.04);
    border:1px solid rgba(255,255,255,.06);
}

.info-icon{
    font-size:28px;
    margin-bottom:12px;
}

.info-label{
    color:#708878;
    font-size:14px;
    margin-bottom:6px;
}

.info-value{
    font-size:22px;
    font-weight:bold;
}

.info-sub{
    color:#82958b;
    font-size:13px;
    margin-top:6px;
}

.info-badge{
    display:inline-block;
    margin-top:10px;
    padding:7px 16px;
    border-radius:20px;
    background:rgba(52,152,219,.18);
    color:#27a9ff;
    font-size:13px;
}

.info-badge.conectado{
    background:rgba(46,204,113,.16);
    color:#35df73;
}

.dica{
    display:flex;
    align-items:center;
    gap:10px;
    margin-top:20px;
    padding:17px 22px;
    border-radius:17px;
    border:1px solid rgba(255,255,255,.06);
    background:rgba(255,255,255,.035);
    color:#b5c1ba;
    font-size:15px;
}

.dica-icon{
    width:29px;
    height:29px;
    border-radius:50%;
    display:inline-flex;
    align-items:center;
    justify-content:center;
    background:#62df3e;
    color:#10210f;
    font-weight:bold;
}

/* HISTÓRICO */

.historico{
    width:100%;
    max-height:600px;
    overflow-y:auto;
}

.registro{
    display:flex;
    align-items:center;
    gap:15px;
    padding:18px;
    margin-bottom:12px;
    border-radius:17px;
    background:rgba(255,255,255,.04);
    border:1px solid rgba(255,255,255,.06);
}

.registro-icone{
    width:45px;
    height:45px;
    display:flex;
    justify-content:center;
    align-items:center;
    border-radius:14px;
    background:rgba(46,204,113,.12);
    font-size:21px;
}

.registro-info{
    flex:1;
}

.registro-hora{
    font-weight:bold;
    margin-bottom:5px;
}

.registro-status{
    color:#819889;
    font-size:12px;
}

.registro-valor{
    font-size:22px;
    font-weight:bold;
}

.vazio{
    padding:60px 20px;
    text-align:center;
    color:#667c6e;
}

.vazio div{
    font-size:45px;
    margin-bottom:15px;
}

/* CONFIGURAÇÕES */

.config-card{
    display:flex;
    flex-direction:column;
    gap:22px;
}

.config-item{
    padding:20px;
    border-radius:18px;
    background:rgba(255,255,255,.04);
    border:1px solid rgba(255,255,255,.07);
}

.config-item h3{
    font-size:17px;
    margin-bottom:8px;
}

.config-item p{
    color:#819889;
    font-size:12px;
    margin-bottom:15px;
}

.config-controle{
    display:flex;
    align-items:center;
    gap:12px;
    flex-wrap:wrap;
}

.config-input,
.config-select{
    padding:13px 15px;
    border-radius:12px;
    border:1px solid rgba(255,255,255,.12);
    background:rgba(255,255,255,.06);
    color:white;
    font-size:15px;
    outline:none;
}

.config-input{
    width:130px;
}

.config-select{
    background:#10291a;
}

.botao-config{
    border:none;
    padding:13px 18px;
    border-radius:12px;
    color:white;
    background:rgba(46,204,113,.18);
    border:1px solid rgba(46,204,113,.3);
    cursor:pointer;
    font-weight:bold;
}

.botao-parar{
    background:rgba(255,71,87,.15);
    border-color:rgba(255,71,87,.3);
}

.irrigador-status{
    display:flex;
    align-items:center;
    gap:10px;
    margin-top:15px;
    padding:13px;
    border-radius:12px;
    background:rgba(255,255,255,.04);
    color:#819889;
    font-size:13px;
}

.indicador-irrigador{
    width:10px;
    height:10px;
    border-radius:50%;
    background:#667c6e;
}

.indicador-irrigador.ligado{
    background:#2ecc71;
    box-shadow:0 0 12px rgba(46,204,113,.8);
}

.contador{
    margin-top:10px;
    font-size:28px;
    font-weight:bold;
    color:#2ecc71;
}

.config-salva{
    color:#2ecc71;
    font-size:12px;
    min-height:16px;
}

/* RESPONSIVO */

@media(max-width:900px){

    .medidor-layout{
        grid-template-columns:1fr;
    }

    .analises-card{
        grid-column:auto;
    }

    .analises-grid{
        grid-template-columns:1fr 1fr;
    }
}

@media(max-width:750px){

    .inicio h1{
        font-size:35px;
    }

    .analises-grid{
        grid-template-columns:1fr;
    }

    .numero{
        font-size:62px;
    }

    .titulo{
        font-size:20px;
    }
}

@media(max-width:560px){

    .sensor-panel{
        padding:22px 18px;
        min-height:auto;
    }

    .umidade-panel .meter{
        width:260px;
        height:260px;
    }

    .meter::before{
        width:205px;
        height:205px;
    }

    .temperatura-meter{
        width:290px;
        height:220px;
    }

    .temperatura-meter::before{
        width:225px;
        height:225px;
        left:32px;
        top:30px;
    }

    .dica{
        align-items:flex-start;
    }
}

</style>
</head>

<body>

<!-- =====================================================
     TELA INICIAL
===================================================== -->

<section id="inicio" class="tela ativa">

<div class="inicio">

<div class="logo">🌱</div>

<h1>Smart Soil</h1>

<p>
Sistema inteligente de monitoramento do solo
</p>

<div class="menu">

<div class="menu-barra"
     onclick="abrirTela('medidor')">

<div class="menu-icone">💧</div>

<div class="menu-conteudo">

<h2>Medidor</h2>

<span>
Acompanhe a umidade do solo
em tempo real
</span>

</div>

<div class="seta">→</div>

</div>


<div class="menu-barra"
     onclick="abrirTela('historicoTela')">

<div class="menu-icone">📜</div>

<div class="menu-conteudo">

<h2>Histórico</h2>

<span>
Veja as medições registradas
a cada minuto
</span>

</div>

<div class="seta">→</div>

</div>


<div class="menu-barra"
     onclick="abrirTela('configuracoes')">

<div class="menu-icone">⚙️</div>

<div class="menu-conteudo">

<h2>Configurações</h2>

<span>
Ajuste o sistema e o tempo de irrigação
</span>

</div>

<div class="seta">→</div>

</div>

</div>

</div>

</section>


<!-- =====================================================
     TELA DO MEDIDOR
===================================================== -->

<section id="medidor" class="tela">

<div class="container medidor-container">

<div class="topo">

<button class="voltar"
        onclick="abrirTela('inicio')">
← Voltar
</button>

<div class="titulo">
Medidor
</div>

<div></div>

</div>


<!-- =====================================================
     CONEXÃO ARDUINO
===================================================== -->

<div class="conexao-arduino">

<div class="conexao-titulo">
🔌 Arduino
</div>

<div class="status-conexao">

<span id="pontoConexao"
      class="ponto-conexao">
</span>

<span id="textoConexao">
Arduino desconectado
</span>

</div>

<button id="botaoConectar"
        class="botao-arduino"
        onclick="conectarArduino()">

🔌 Conectar Arduino

</button>

<button id="botaoDesconectar"
        class="botao-arduino botao-desconectar"
        onclick="desconectarArduino()"
        style="display:none;">

⛔ Desconectar

</button>

</div>


<div class="medidor-layout">


<!-- UMIDADE -->

<div class="card sensor-panel umidade-panel">

<div class="sensor-heading">

<div class="sensor-heading-icon">
💧
</div>

<div>

<h2>Umidade do Solo</h2>

<p>
Sensor de Umidade
</p>

</div>

</div>


<div class="meter" id="meter">

<div class="valor">

<div class="numero"
     id="numero">
50
</div>

<div class="porcentagem">
%
</div>

<div class="meter-caption">
UMIDADE
</div>

</div>

</div>


<div class="status"
     id="status">

Aguardando Arduino

</div>


<div class="barra-titulo">

<span>
0% — Seco
</span>

<span>
100% — Úmido
</span>

</div>


<div class="barra">

<div class="barra-progresso"
     id="barraProgresso">
</div>

</div>

</div>


<!-- TEMPERATURA -->

<div class="card sensor-panel temperatura-panel">

<div class="sensor-heading">

<div class="sensor-heading-icon">
🌡️
</div>

<div>

<h2>
Temperatura do Solo
</h2>

<p>
Sensor de Temperatura
</p>

</div>

</div>


<div class="temperatura-meter"
     id="temperaturaMeter">

<div class="temperatura-valor">

<div class="temperatura-numero"
     id="temperaturaNumero">

25.0

</div>

<div class="temperatura-unidade">
°C
</div>

<div class="temperatura-caption">
Temperatura Atual
</div>

</div>

</div>


<div class="temp-chart-box">

<div class="temp-chart-title">
Histórico (24h)
</div>

<div class="temp-chart-wrap">

<canvas id="graficoTemperatura"></canvas>

<div class="temp-y-labels">

<span>40°C</span>
<span>30°C</span>
<span>20°C</span>
<span>10°C</span>
<span>0°C</span>

</div>

</div>

<div class="temp-x-labels">

<span>18:00</span>
<span>00:00</span>
<span>06:00</span>
<span>12:00</span>
<span>Agora</span>

</div>

</div>


<div class="temperatura-status"
     id="temperaturaStatus">

Aguardando Arduino

</div>

</div>


<!-- ANÁLISES -->

<div class="card analises-card">

<div class="analises-titulo">

<span>🌱</span>

Análises do Solo

</div>


<div class="analises-grid">


<div class="info">

<div class="info-icon">
💧
</div>

<div class="info-label">
Umidade atual
</div>

<div class="info-value"
     id="umidade">

50%

</div>

<div class="info-badge"
     id="umidadeBadge">

Aguardando

</div>

</div>


<div class="info">

<div class="info-icon">
📊
</div>

<div class="info-label">
Leitura
</div>

<div class="info-value"
     id="leitura">

50

</div>

<div class="info-sub">
Valor do sensor
</div>

</div>


<div class="info">

<div class="info-icon">
🌱
</div>

<div class="info-label">
Estado
</div>

<div class="info-value"
     id="estado">

Aguardando

</div>

<div class="info-badge">
Solo
</div>

</div>


<div class="info">

<div class="info-icon">
📡
</div>

<div class="info-label">
Sensor
</div>

<div class="info-value"
     id="sensorOnline">

Offline
</div>

<div class="info-badge"
     id="sensorBadge">

Desconectado
</div>

</div>


</div>


<div class="dica">

<span class="dica-icon">
i
</span>

<strong>Dica:</strong>

<span id="dicaTexto">

Conecte o Arduino pela porta USB
para receber os dados reais dos sensores.

</span>

</div>

</div>

</div>

</div>

</section>


<!-- =====================================================
     CONFIGURAÇÕES
===================================================== -->

<section id="configuracoes" class="tela">

<div class="container">

<div class="topo">

<button class="voltar"
        onclick="abrirTela('inicio')">

← Voltar

</button>

<div class="titulo">
Configurações
</div>

<div></div>

</div>


<div class="card config-card">


<div class="config-item">

<h3>
💧 Tempo de irrigação
</h3>

<p>
Defina por quanto tempo o irrigador ficará ligado.
</p>

<div class="config-controle">

<input
id="tempoIrrigacao"
class="config-input"
type="number"
min="1"
max="3600"
value="30">

<span>segundos</span>

<button
class="botao-config"
onclick="salvarTempoIrrigacao()">

💾 Salvar

</button>

</div>

<div id="mensagemConfig"
     class="config-salva">
</div>

</div>


<div class="config-item">

<h3>
🚿 Controle do irrigador
</h3>

<p>
Ligue o irrigador pelo tempo configurado
ou desligue-o manualmente.
</p>

<div class="config-controle">

<button
class="botao-config"
onclick="iniciarIrrigacao()">

▶ Iniciar irrigação

</button>

<button
class="botao-config botao-parar"
onclick="pararIrrigacao()">

⏹ Parar irrigação

</button>

</div>

<div class="irrigador-status">

<span
id="indicadorIrrigador"
class="indicador-irrigador">
</span>

<span id="statusIrrigador">
Irrigador desligado
</span>

</div>

<div id="contadorIrrigacao"
     class="contador">

00:00

</div>

</div>


<div class="config-item">

<h3>
📡 Atualização do sensor
</h3>

<p>
Escolha o intervalo entre as atualizações do medidor.
</p>

<div class="config-controle">

<select
id="intervaloSensor"
class="config-select"
onchange="alterarIntervaloSensor()">

<option value="500">
0,5 segundo
</option>

<option value="1000">
1 segundo
</option>

<option value="2000"
        selected>
2 segundos
</option>

<option value="5000">
5 segundos
</option>

<option value="10000">
10 segundos
</option>

</select>

</div>

</div>


<div class="config-item">

<h3>
🔄 Restaurar configurações
</h3>

<p>
Volte o tempo de irrigação para
30 segundos e o sensor para 2 segundos.
</p>

<button
class="botao-config"
onclick="restaurarConfiguracoes()">

Restaurar configurações

</button>

</div>

</div>

</div>

</section>


<!-- =====================================================
     HISTÓRICO
===================================================== -->

<section id="historicoTela" class="tela">

<div class="container">

<div class="topo">

<button
class="voltar"
onclick="abrirTela('inicio')">

← Voltar

</button>

<div class="titulo">
Histórico
</div>

<div></div>

</div>


<div class="card">

<p style="
color:#819889;
font-size:13px;
margin-bottom:25px;
">

Uma nova leitura é registrada
automaticamente a cada 1 minuto.

</p>


<div id="listaHistorico"
     class="historico">

<div class="vazio">

<div>📊</div>

<p>
Aguardando a primeira medição...
</p>

</div>

</div>

</div>

</div>

</section>


<script>

/* =====================================================
   NAVEGAÇÃO
===================================================== */

function abrirTela(id){

    document
    .querySelectorAll(".tela")
    .forEach(function(tela){

        tela.classList.remove("ativa");

    });

    document
    .getElementById(id)
    .classList.add("ativa");

}


/* =====================================================
   VARIÁVEIS DOS SENSORES
===================================================== */

/*
   IMPORTANTE:

   Estes valores NÃO são mais aleatórios.

   Eles serão atualizados pelo Arduino.
*/

let umidade = 50;
let temperatura = 25;

let leituraSensor = 0;
let valvulaArduino = "DESLIGADA";


/* =====================================================
   CONEXÃO SERIAL
===================================================== */

let portaSerial = null;
let leitorSerial = null;
let lendoSerial = false;
let dadosRecebidos = "";


/* =====================================================
   CONECTAR ARDUINO
===================================================== */

async function conectarArduino(){

    if(!("serial" in navigator)){

        alert(
            "Seu navegador não suporta Web Serial.\n\n" +
            "Use Google Chrome ou Microsoft Edge."
        );

        return;
    }

    try{

        portaSerial =
            await navigator.serial.requestPort();

        await portaSerial.open({
            baudRate:9600
        });


        document
        .getElementById("pontoConexao")
        .classList.add("conectado");


        document
        .getElementById("textoConexao")
        .textContent =
            "Arduino conectado";


        document
        .getElementById("botaoConectar")
        .style.display="none";


        document
        .getElementById("botaoDesconectar")
        .style.display="block";


        document
        .getElementById("sensorOnline")
        .textContent="Online";


        document
        .getElementById("sensorBadge")
        .textContent="Conectado";


        document
        .getElementById("sensorBadge")
        .classList.add("conectado");


        document
        .getElementById("dicaTexto")
        .textContent =
            "Arduino conectado. Os medidores estão recebendo os valores reais dos sensores.";


        lerSerial();

    }

    catch(erro){

        console.error(erro);

        alert(
            "Não foi possível conectar ao Arduino.\n\n" +
            "Verifique se ele está conectado ao USB."
        );

    }

}


/* =====================================================
   LER PORTA SERIAL
===================================================== */

async function lerSerial(){

    if(!portaSerial) return;

    lendoSerial=true;

    const decoder =
        new TextDecoderStream();

    const entrada =
        portaSerial.readable.pipeThrough(decoder);

    leitorSerial =
        entrada.getReader();


    try{

        while(lendoSerial){

            const {value,done} =
                await leitorSerial.read();

            if(done) break;

            if(value){

                dadosRecebidos += value;

                let linhas =
                    dadosRecebidos.split("\n");

                dadosRecebidos =
                    linhas.pop();

                for(
                    const linha of linhas
                ){

                    processarDadosArduino(
                        linha.trim()
                    );

                }

            }

        }

    }

    catch(erro){

        console.error(
            "Erro na leitura serial:",
            erro
        );

    }

}


/* =====================================================
   PROCESSAR DADOS DO ARDUINO
===================================================== */

function processarDadosArduino(linha){

    if(!linha) return;


    console.log(
        "Arduino:",
        linha
    );


    /*
       O Arduino envia:

       Temperatura:25.4,
       Umidade:68,
       Sensor:694,
       Valvula:LIGADA
    */


    const temperaturaMatch =
        linha.match(
            /Temperatura\s*:\s*(-?\d+(?:[.,]\d+)?)/i
        );


    const umidadeMatch =
        linha.match(
            /Umidade\s*:\s*(\d+(?:[.,]\d+)?)/i
        );


    const sensorMatch =
        linha.match(
            /Sensor\s*:\s*(\d+)/i
        );


    const valvulaMatch =
        linha.match(
            /Valvula\s*:\s*(LIGADA|DESLIGADA)/i
        );


    if(temperaturaMatch){

        temperatura =
            parseFloat(
                temperaturaMatch[1]
                .replace(",",".")
            );

    }


    if(umidadeMatch){

        umidade =
            parseFloat(
                umidadeMatch[1]
                .replace(",",".")
            );

    }


    if(sensorMatch){

        leituraSensor =
            parseInt(
                sensorMatch[1]
            );

    }


    if(valvulaMatch){

        valvulaArduino =
            valvulaMatch[1].toUpperCase();

    }


    /*
       Só atualiza se recebeu
       dados válidos.
    */

    if(
        temperaturaMatch ||
        umidadeMatch
    ){

        atualizarMedidorReal();

    }

}


/* =====================================================
   ATUALIZAR MEDIDOR COM ARDUINO
===================================================== */

function atualizarMedidorReal(){

    /*
       Limites de segurança
    */

    umidade =
        Math.max(
            0,
            Math.min(
                100,
                umidade
            )
        );


    /* =================================================
       ELEMENTOS
    ================================================= */

    const numero =
        document.getElementById("numero");

    const umidadeTexto =
        document.getElementById("umidade");

    const leitura =
        document.getElementById("leitura");

    const estado =
        document.getElementById("estado");

    const status =
        document.getElementById("status");

    const meter =
        document.getElementById("meter");

    const barra =
        document.getElementById("barraProgresso");

    const temperaturaNumero =
        document.getElementById(
            "temperaturaNumero"
        );

    const temperaturaStatus =
        document.getElementById(
            "temperaturaStatus"
        );

    const temperaturaMeter =
        document.getElementById(
            "temperaturaMeter"
        );


    /* =================================================
       UMIDADE
    ================================================= */

    numero.textContent =
        Math.round(umidade);

    umidadeTexto.textContent =
        Math.round(umidade) + "%";

    leitura.textContent =
        leituraSensor;


    let cor;


    if(umidade < 30){

        cor="#ff4757";

        status.textContent=
            "Solo seco";

        estado.textContent=
            "Seco";

    }

    else if(umidade < 60){

        cor="#f1c40f";

        status.textContent=
            "Umidade moderada";

        estado.textContent=
            "Moderado";

    }

    else if(umidade < 85){

        cor="#2ecc71";

        status.textContent=
            "Solo úmido";

        estado.textContent=
            "Ideal";

    }

    else{

        cor="#3498db";

        status.textContent=
            "Solo muito úmido";

        estado.textContent=
            "Muito úmido";

    }


    status.style.color=cor;


    const graus =
        (umidade / 100) * 360;


    meter.style.background =
        `conic-gradient(
            ${cor} 0deg,
            ${cor} ${graus}deg,
            rgba(255,255,255,.06)
            ${graus}deg
        )`;


    barra.style.width =
        umidade + "%";

    barra.style.background =
        cor;


    /* =================================================
       BADGE DE UMIDADE
    ================================================= */

    const badge =
        document.getElementById(
            "umidadeBadge"
        );


    if(umidade >= 85){

        badge.textContent=
            "Muito úmido";

    }

    else if(umidade >= 60){

        badge.textContent=
            "Ideal";

    }

    else if(umidade >= 30){

        badge.textContent=
            "Moderado";

    }

    else{

        badge.textContent=
            "Seco";

    }


    /* =================================================
       TEMPERATURA REAL
    ================================================= */

    temperaturaNumero.textContent =
        Number(temperatura).toFixed(1);


    let corTemperatura;


    if(temperatura < 20){

        corTemperatura="#3498db";

        temperaturaStatus.textContent=
            "Temperatura baixa";

    }

    else if(temperatura <= 30){

        corTemperatura="#2ecc71";

        temperaturaStatus.textContent=
            "Temperatura normal";

    }

    else if(temperatura <= 35){

        corTemperatura="#f1c40f";

        temperaturaStatus.textContent=
            "Temperatura elevada";

    }

    else{

        corTemperatura="#ff4757";

        temperaturaStatus.textContent=
            "Temperatura alta";

    }


    temperaturaStatus.style.color =
        corTemperatura;


    let grausTemperatura =
        ((temperatura - 18) / 20) * 360;


    grausTemperatura =
        Math.max(
            0,
            Math.min(
                360,
                grausTemperatura
            )
        );


    temperaturaMeter.style.background =
        `conic-gradient(
            ${corTemperatura} 0deg,
            ${corTemperatura}
            ${grausTemperatura}deg,
            rgba(255,255,255,.06)
            ${grausTemperatura}deg
        )`;


    /* =================================================
       HISTÓRICO DO GRÁFICO
    ================================================= */

    adicionarTemperaturaHistorico(
        temperatura
    );

    desenharGraficoTemperatura();


    /*
       Atualiza indicação do sensor
    */

    document
    .getElementById("sensorOnline")
    .textContent="Online";


    document
    .getElementById("sensorBadge")
    .textContent="Conectado";


    /*
       Atualiza dica
    */

    document
    .getElementById("dicaTexto")
    .textContent =
        "Dados recebidos diretamente do Arduino pela porta USB. " +
        "Temperatura: " +
        Number(temperatura).toFixed(1) +
        "°C | Umidade: " +
        Math.round(umidade) +
        "%.";

}


/* =====================================================
   DESCONECTAR ARDUINO
===================================================== */

async function desconectarArduino(){

    lendoSerial=false;


    try{

        if(leitorSerial){

            await leitorSerial.cancel();

            leitorSerial=null;

        }

    }

    catch(erro){

        console.log(erro);

    }


    try{

        if(portaSerial){

            await portaSerial.close();

        }

    }

    catch(erro){

        console.log(erro);

    }


    portaSerial=null;


    document
    .getElementById("pontoConexao")
    .classList.remove("conectado");


    document
    .getElementById("textoConexao")
    .textContent =
        "Arduino desconectado";


    document
    .getElementById("botaoConectar")
    .style.display="block";


    document
    .getElementById("botaoDesconectar")
    .style.display="none";


    document
    .getElementById("sensorOnline")
    .textContent="Offline";


    document
    .getElementById("sensorBadge")
    .textContent="Desconectado";


    document
    .getElementById("sensorBadge")
    .classList.remove("conectado");


    document
    .getElementById("dicaTexto")
    .textContent =
        "Arduino desconectado. Conecte novamente pela porta USB para receber os dados reais.";

}


/* =====================================================
   HISTÓRICO
===================================================== */

let historico=[];
let temperaturaHistorico=[];


function adicionarTemperaturaHistorico(valor){

    temperaturaHistorico.push({

        valor:valor,

        hora:
            new Date().toLocaleTimeString(
                "pt-BR",
                {
                    hour:"2-digit",
                    minute:"2-digit"
                }
            )

    });


    if(
        temperaturaHistorico.length > 24
    ){

        temperaturaHistorico.shift();

    }

}


/* =====================================================
   GRÁFICO
===================================================== */

function desenharGraficoTemperatura(){

    const canvas =
        document.getElementById(
            "graficoTemperatura"
        );

    if(!canvas) return;


    const rect =
        canvas.getBoundingClientRect();


    const dpr =
        window.devicePixelRatio || 1;


    const w =
        Math.max(
            300,
            rect.width
        );


    const h =
        Math.max(
            140,
            rect.height
        );


    canvas.width =
        w * dpr;

    canvas.height =
        h * dpr;


    const ctx =
        canvas.getContext("2d");


    ctx.setTransform(
        dpr,
        0,
        0,
        dpr,
        0,
        0
    );


    ctx.clearRect(
        0,
        0,
        w,
        h
    );


    const top=8;
    const bottom=h-4;
    const range=40;


    ctx.strokeStyle=
        "rgba(255,255,255,.08)";

    ctx.lineWidth=1;


    for(
        let i=0;
        i<=4;
        i++
    ){

        const y =
            top+
            (bottom-top)*
            (i/4);


        ctx.beginPath();

        ctx.moveTo(
            0,
            y
        );

        ctx.lineTo(
            w,
            y
        );

        ctx.stroke();

    }


    const data =
        temperaturaHistorico.length
        ?
        temperaturaHistorico.map(
            x=>x.valor
        )
        :
        [temperatura];


    const points =
        data.map(
            function(v,i){

                return {

                    x:
                        data.length===1
                        ?
                        w/2
                        :
                        w*
                        (
                            i/
                            (data.length-1)
                        ),

                    y:
                        bottom-
                        Math.max(
                            0,
                            Math.min(
                                range,
                                v
                            )
                        )/
                        range*
                        (bottom-top)

                };

            }
        );


    if(points.length<2){

        if(points.length===1){

            const p=points[0];

            ctx.beginPath();

            ctx.arc(
                p.x,
                p.y,
                7,
                0,
                Math.PI*2
            );

            ctx.fillStyle=
                "#ff8f00";

            ctx.fill();

        }

        return;

    }


    /* ÁREA */

    ctx.beginPath();


    points.forEach(
        function(p,i){

            if(i===0){

                ctx.moveTo(
                    p.x,
                    p.y
                );

            }

            else{

                ctx.lineTo(
                    p.x,
                    p.y
                );

            }

        }
    );


    ctx.lineTo(
        points[points.length-1].x,
        bottom
    );


    ctx.lineTo(
        points[0].x,
        bottom
    );


    ctx.closePath();


    const grad =
        ctx.createLinearGradient(
            0,
            top,
            0,
            bottom
        );


    grad.addColorStop(
        0,
        "rgba(255,159,28,.32)"
    );

    grad.addColorStop(
        1,
        "rgba(255,159,28,.03)"
    );


    ctx.fillStyle=grad;
    ctx.fill();


    /* LINHA */

    ctx.beginPath();


    points.forEach(
        function(p,i){

            if(i===0){

                ctx.moveTo(
                    p.x,
                    p.y
                );

            }

            else{

                ctx.lineTo(
                    p.x,
                    p.y
                );

            }

        }
    );


    ctx.strokeStyle="#ff8f00";
    ctx.lineWidth=3;
    ctx.lineJoin="round";
    ctx.lineCap="round";

    ctx.stroke();


    /* ÚLTIMO PONTO */

    const last =
        points[points.length-1];


    ctx.beginPath();


    ctx.arc(
        last.x,
        last.y,
        8,
        0,
        Math.PI*2
    );


    ctx.fillStyle="#ff8f00";
    ctx.fill();

    ctx.lineWidth=3;
    ctx.strokeStyle="#fff";

    ctx.stroke();

}


window.addEventListener(
    "resize",
    desenharGraficoTemperatura
);


/* =====================================================
   CRIA HISTÓRICO
===================================================== */

function criarHistorico(){

    let estado;
    let icone="💧";
    let cor;


    if(umidade<30){

        estado="Solo seco";
        cor="#ff4757";

    }

    else if(umidade<60){

        estado="Umidade moderada";
        cor="#f1c40f";

    }

    else if(umidade<85){

        estado="Solo úmido";
        cor="#2ecc71";

    }

    else{

        estado="Solo muito úmido";
        cor="#3498db";

    }


    const agora=new Date();


    const hora =
        agora.toLocaleTimeString(
            "pt-BR",
            {
                hour:"2-digit",
                minute:"2-digit",
                second:"2-digit"
            }
        );


    historico.unshift({

        hora:hora,
        valor:Math.round(umidade),
        temperatura:temperatura,
        estado:estado,
        icone:icone,
        cor:cor

    });


    mostrarHistorico();

}


/* =====================================================
   MOSTRA HISTÓRICO
===================================================== */

function mostrarHistorico(){

    const lista =
        document.getElementById(
            "listaHistorico"
        );


    if(historico.length===0){

        lista.innerHTML=`
            <div class="vazio">
                <div>📊</div>
                <p>
                    Aguardando a primeira medição...
                </p>
            </div>
        `;

        return;

    }


    lista.innerHTML="";


    historico.forEach(
        function(registro){

            const item =
                document.createElement(
                    "div"
                );


            item.className="registro";


            item.innerHTML=`

                <div
                    class="registro-icone"
                    style="color:${registro.cor};"
                >
                    ${registro.icone}
                </div>

                <div class="registro-info">

                    <div class="registro-hora">
                        ${registro.hora}
                    </div>

                    <div class="registro-status">
                        ${registro.estado}
                        • Temperatura:
                        ${Number(registro.temperatura).toFixed(1)}°C
                    </div>

                </div>

                <div
                    class="registro-valor"
                    style="color:${registro.cor};"
                >
                    ${registro.valor}%
                </div>

            `;


            lista.appendChild(item);

        }
    );

}


/* =====================================================
   CONFIGURAÇÕES
===================================================== */

let tempoIrrigacao =
    Number(
        localStorage.getItem(
            "tempoIrrigacao"
        )
    ) || 30;


let intervaloSensor =
    Number(
        localStorage.getItem(
            "intervaloSensor"
        )
    ) || 2000;


let timerIrrigacao=null;
let segundosRestantes=0;


/* =====================================================
   CARREGAR CONFIGURAÇÕES
===================================================== */

function carregarConfiguracoes(){

    const campoTempo =
        document.getElementById(
            "tempoIrrigacao"
        );


    const campoIntervalo =
        document.getElementById(
            "intervaloSensor"
        );


    if(campoTempo){

        campoTempo.value=
            tempoIrrigacao;

    }


    if(campoIntervalo){

        campoIntervalo.value=
            intervaloSensor;

    }

}


/* =====================================================
   SALVAR TEMPO
===================================================== */

function salvarTempoIrrigacao(){

    const campo =
        document.getElementById(
            "tempoIrrigacao"
        );


    let valor=
        Number(campo.value);


    if(!valor || valor<1){

        valor=1;

    }


    if(valor>3600){

        valor=3600;

    }


    tempoIrrigacao=
        Math.round(valor);


    campo.value=
        tempoIrrigacao;


    localStorage.setItem(
        "tempoIrrigacao",
        tempoIrrigacao
    );


    const mensagem =
        document.getElementById(
            "mensagemConfig"
        );


    mensagem.textContent=
        "✓ Tempo salvo: "+
        tempoIrrigacao+
        " segundos";


    setTimeout(
        function(){

            mensagem.textContent="";

        },
        3000
    );

}


/* =====================================================
   IRRIGAÇÃO
===================================================== */

function iniciarIrrigacao(){

    if(timerIrrigacao!==null){

        return;

    }


    salvarTempoIrrigacao();


    segundosRestantes=
        tempoIrrigacao;


    document
    .getElementById(
        "indicadorIrrigador"
    )
    .classList.add("ligado");


    document
    .getElementById(
        "statusIrrigador"
    )
    .textContent=
        "Irrigador ligado";


    atualizarContadorIrrigacao();


    timerIrrigacao=
        setInterval(
            function(){

                segundosRestantes--;

                atualizarContadorIrrigacao();


                if(
                    segundosRestantes<=0
                ){

                    pararIrrigacao();

                }

            },
            1000
        );

}


function pararIrrigacao(){

    if(timerIrrigacao!==null){

        clearInterval(
            timerIrrigacao
        );

        timerIrrigacao=null;

    }


    segundosRestantes=0;


    const indicador =
        document.getElementById(
            "indicadorIrrigador"
        );


    const status =
        document.getElementById(
            "statusIrrigador"
        );


    indicador.classList.remove(
        "ligado"
    );


    status.textContent=
        "Irrigador desligado";


    atualizarContadorIrrigacao();

}


/* =====================================================
   CONTADOR
===================================================== */

function atualizarContadorIrrigacao(){

    const contador =
        document.getElementById(
            "contadorIrrigacao"
        );


    if(!contador) return;


    const minutos =
        Math.floor(
            segundosRestantes/60
        );


    const segundos =
        segundosRestantes%60;


    contador.textContent=
        String(minutos).padStart(2,"0")+
        ":"+
        String(segundos).padStart(2,"0");

}


/* =====================================================
   INTERVALO
===================================================== */

function alterarIntervaloSensor(){

    intervaloSensor=
        Number(
            document.getElementById(
                "intervaloSensor"
            ).value
        );


    localStorage.setItem(
        "intervaloSensor",
        intervaloSensor
    );

}


/* =====================================================
   RESTAURAR
===================================================== */

function restaurarConfiguracoes(){

    tempoIrrigacao=30;

    intervaloSensor=2000;


    localStorage.setItem(
        "tempoIrrigacao",
        tempoIrrigacao
    );


    localStorage.setItem(
        "intervaloSensor",
        intervaloSensor
    );


    carregarConfiguracoes();


    const mensagem =
        document.getElementById(
            "mensagemConfig"
        );


    mensagem.textContent=
        "✓ Configurações restauradas";


    setTimeout(
        function(){

            mensagem.textContent="";

        },
        3000
    );

}


/* =====================================================
   INICIALIZAÇÃO
===================================================== */

carregarConfiguracoes();

desenharGraficoTemperatura();


/*
   NÃO existe mais:

   Math.random()

   para temperatura ou umidade.

   O site aguarda o Arduino.
*/


/* =====================================================
   HISTÓRICO A CADA 1 MINUTO
===================================================== */

setInterval(
    function(){

        /*
           Só registra quando existe
           uma conexão com Arduino.
        */

        if(portaSerial){

            criarHistorico();

        }

    },
    60000
);


/* =====================================================
   DETECTAR DESCONEXÃO FÍSICA
===================================================== */

if("serial" in navigator){

    navigator.serial.addEventListener(
        "disconnect",
        function(event){

            if(
                portaSerial ===
                event.target
            ){

                desconectarArduino();

            }

        }
    );

}

</script>

</body>
</html>
<script>

/* =====================================================
   NAVEGAÇÃO
===================================================== */

function abrirTela(id) {

    document.querySelectorAll(".tela").forEach(function(tela) {
        tela.classList.remove("ativa");
    });

    document.getElementById(id).classList.add("ativa");
}


/* =====================================================
   VARIÁVEIS DOS SENSORES
===================================================== */

let umidade = 50;
let temperatura = 25;

let historico = [];
let temperaturaHistorico = [];


/* =====================================================
   CONEXÃO COM ARDUINO
===================================================== */

let portaArduino = null;
let leitorArduino = null;
let dadosArduino = "";
let arduinoConectado = false;


/* =====================================================
   CONECTAR ARDUINO
===================================================== */

async function conectarArduino() {

    if (!("serial" in navigator)) {

        alert(
            "Seu navegador não suporta conexão Serial.\n\n" +
            "Use o Google Chrome ou Microsoft Edge."
        );

        return;
    }

    try {

        portaArduino = await navigator.serial.requestPort();

        await portaArduino.open({
            baudRate: 9600
        });

        arduinoConectado = true;

        atualizarStatusArduino(
            "Arduino conectado"
        );

        lerDadosArduino();

    } catch (erro) {

        console.error(
            "Erro ao conectar Arduino:",
            erro
        );

        atualizarStatusArduino(
            "Arduino desconectado"
        );
    }
}


/* =====================================================
   LER DADOS DO ARDUINO
===================================================== */

async function lerDadosArduino() {

    if (!portaArduino) return;

    const decoder =
        new TextDecoderStream();

    portaArduino.readable.pipeTo(
        decoder.writable
    );

    leitorArduino =
        decoder.readable.getReader();

    try {

        while (true) {

            const { value, done } =
                await leitorArduino.read();

            if (done) {
                break;
            }

            if (value) {

                dadosArduino += value;

                let linhas =
                    dadosArduino.split("\n");

                dadosArduino =
                    linhas.pop();

                linhas.forEach(function(linha) {

                    linha =
                        linha.trim();

                    if (linha.length > 0) {

                        interpretarDadosArduino(
                            linha
                        );
                    }

                });
            }
        }

    } catch (erro) {

        console.error(
            "Erro na leitura Serial:",
            erro
        );

        arduinoConectado = false;

        atualizarStatusArduino(
            "Arduino desconectado"
        );
    }
}


/* =====================================================
   INTERPRETAR DADOS DO ARDUINO
===================================================== */

function interpretarDadosArduino(linha) {

    console.log(
        "Arduino:",
        linha
    );

    /*
       Exemplo recebido:

       Temperatura:25.3,Umidade:62,Sensor:634,Valvula:DESLIGADA
    */

    const partes =
        linha.split(",");

    let novaTemperatura = null;
    let novaUmidade = null;
    let novoSensor = null;
    let novaValvula = null;


    partes.forEach(function(parte) {

        parte = parte.trim();

        if (
            parte.startsWith(
                "Temperatura:"
            )
        ) {

            novaTemperatura =
                parseFloat(
                    parte
                        .replace(
                            "Temperatura:",
                            ""
                        )
                );
        }


        if (
            parte.startsWith(
                "Umidade:"
            )
        ) {

            novaUmidade =
                parseFloat(
                    parte
                        .replace(
                            "Umidade:",
                            ""
                        )
                );
        }


        if (
            parte.startsWith(
                "Sensor:"
            )
        ) {

            novoSensor =
                parseInt(
                    parte
                        .replace(
                            "Sensor:",
                            ""
                        )
                );
        }


        if (
            parte.startsWith(
                "Valvula:"
            )
        ) {

            novaValvula =
                parte
                    .replace(
                        "Valvula:",
                        ""
                    )
                    .trim();
        }

    });


    /*
       Só atualiza a tela se
       os valores forem válidos.
    */

    if (
        novaTemperatura !== null &&
        !isNaN(novaTemperatura)
    ) {

        temperatura =
            novaTemperatura;
    }


    if (
        novaUmidade !== null &&
        !isNaN(novaUmidade)
    ) {

        umidade =
            Math.max(
                0,
                Math.min(
                    100,
                    Math.round(
                        novaUmidade
                    )
                )
            );
    }


    /*
       Atualiza o medidor
       usando os valores reais
       do Arduino.
    */

    atualizarMedidorArduino(
        novoSensor,
        novaValvula
    );
}


/* =====================================================
   ATUALIZAR MEDIDOR COM ARDUINO
===================================================== */

function atualizarMedidorArduino(
    sensor,
    valvula
) {

    const numero =
        document.getElementById(
            "numero"
        );

    const umidadeTexto =
        document.getElementById(
            "umidade"
        );

    const leitura =
        document.getElementById(
            "leitura"
        );

    const estado =
        document.getElementById(
            "estado"
        );

    const status =
        document.getElementById(
            "status"
        );

    const meter =
        document.getElementById(
            "meter"
        );

    const barra =
        document.getElementById(
            "barraProgresso"
        );

    const temperaturaNumero =
        document.getElementById(
            "temperaturaNumero"
        );

    const temperaturaStatus =
        document.getElementById(
            "temperaturaStatus"
        );

    const temperaturaMeter =
        document.getElementById(
            "temperaturaMeter"
        );


    /* =================================================
       UMIDADE
    ================================================= */

    numero.textContent =
        umidade;

    umidadeTexto.textContent =
        umidade + "%";

    leitura.textContent =
        sensor !== null &&
        !isNaN(sensor)
            ? sensor
            : umidade;


    let cor;


    if (umidade < 30) {

        cor = "#ff4757";

        status.textContent =
            "Solo seco";

        estado.textContent =
            "Seco";

    }

    else if (umidade < 60) {

        cor = "#f1c40f";

        status.textContent =
            "Umidade moderada";

        estado.textContent =
            "Moderado";

    }

    else if (umidade < 85) {

        cor = "#2ecc71";

        status.textContent =
            "Solo úmido";

        estado.textContent =
            "Ideal";

    }

    else {

        cor = "#3498db";

        status.textContent =
            "Solo muito úmido";

        estado.textContent =
            "Muito úmido";
    }


    status.style.color =
        cor;


    const graus =
        (umidade / 100) * 360;


    meter.style.background =
        `conic-gradient(
            ${cor} 0deg,
            ${cor} ${graus}deg,
            rgba(255,255,255,.06)
            ${graus}deg
        )`;


    barra.style.width =
        umidade + "%";

    barra.style.background =
        cor;


    /* =================================================
       TEMPERATURA
    ================================================= */

    temperaturaNumero.textContent =
        temperatura.toFixed(1);


    let corTemperatura;


    if (temperatura < 20) {

        corTemperatura =
            "#3498db";

        temperaturaStatus.textContent =
            "Temperatura baixa";

    }

    else if (temperatura <= 30) {

        corTemperatura =
            "#2ecc71";

        temperaturaStatus.textContent =
            "Temperatura normal";

    }

    else if (temperatura <= 35) {

        corTemperatura =
            "#f1c40f";

        temperaturaStatus.textContent =
            "Temperatura elevada";

    }

    else {

        corTemperatura =
            "#ff4757";

        temperaturaStatus.textContent =
            "Temperatura alta";
    }


    temperaturaStatus.style.color =
        corTemperatura;


    const grausTemperatura =
        Math.max(
            0,
            Math.min(
                360,
                ((temperatura - 18) / 20) * 360
            )
        );


    temperaturaMeter.style.background =
        `conic-gradient(
            ${corTemperatura} 0deg,
            ${corTemperatura}
            ${grausTemperatura}deg,
            rgba(255,255,255,.06)
            ${grausTemperatura}deg
        )`;


    /* =================================================
       BADGE DA UMIDADE
    ================================================= */

    const badge =
        document.getElementById(
            "umidadeBadge"
        );


    if (badge) {

        if (umidade >= 85) {

            badge.textContent =
                "Muito úmido";

        }

        else if (umidade >= 60) {

            badge.textContent =
                "Ideal";

        }

        else if (umidade >= 30) {

            badge.textContent =
                "Moderado";

        }

        else {

            badge.textContent =
                "Seco";
        }
    }


    /* =================================================
       STATUS DA VÁLVULA
    ================================================= */

    const statusIrrigador =
        document.getElementById(
            "statusIrrigador"
        );

    const indicadorIrrigador =
        document.getElementById(
            "indicadorIrrigador"
        );


    if (
        valvula &&
        valvula.toUpperCase() ===
        "LIGADA"
    ) {

        if (statusIrrigador) {

            statusIrrigador.textContent =
                "Irrigador ligado pelo Arduino";
        }

        if (indicadorIrrigador) {

            indicadorIrrigador.classList.add(
                "ligado"
            );
        }

    }

    else {

        if (statusIrrigador) {

            statusIrrigador.textContent =
                "Irrigador desligado";
        }

        if (indicadorIrrigador) {

            indicadorIrrigador.classList.remove(
                "ligado"
            );
        }
    }


    /* =================================================
       GRÁFICO
    ================================================= */

    adicionarTemperaturaHistorico(
        temperatura
    );

    desenharGraficoTemperatura();


    /* =================================================
       DICA
    ================================================= */

    const dica =
        document.getElementById(
            "dicaTexto"
        );


    if (dica) {

        if (umidade < 30) {

            dica.textContent =
                "O solo está seco. A irrigação é necessária.";

        }

        else if (umidade < 60) {

            dica.textContent =
                "A umidade está moderada. Continue monitorando.";

        }

        else if (umidade < 85) {

            dica.textContent =
                "O solo está em ótimas condições para as plantas.";

        }

        else {

            dica.textContent =
                "O solo está muito úmido. Evite excesso de irrigação.";
        }
    }
}


/* =====================================================
   STATUS DA CONEXÃO
===================================================== */

function atualizarStatusArduino(texto) {

    const elemento =
        document.getElementById(
            "statusArduino"
        );

    const badge =
        document.getElementById(
            "badgeArduino"
        );


    if (elemento) {

        elemento.textContent =
            texto;
    }


    if (badge) {

        if (
            texto ===
            "Arduino conectado"
        ) {

            badge.textContent =
                "Conectado";

            badge.classList.add(
                "conectado"
            );

        }

        else {

            badge.textContent =
                "Desconectado";

            badge.classList.remove(
                "conectado"
            );
        }
    }
}


/* =====================================================
   GRÁFICO DE TEMPERATURA
===================================================== */

function adicionarTemperaturaHistorico(valor) {

    temperaturaHistorico.push({

        valor: valor,

        hora:
            new Date().toLocaleTimeString(
                "pt-BR",
                {
                    hour: "2-digit",
                    minute: "2-digit"
                }
            )
    });


    if (
        temperaturaHistorico.length >
        24
    ) {

        temperaturaHistorico.shift();
    }
}


function desenharGraficoTemperatura() {

    const canvas =
        document.getElementById(
            "graficoTemperatura"
        );

    if (!canvas) return;


    const rect =
        canvas.getBoundingClientRect();


    const dpr =
        window.devicePixelRatio || 1;


    const w =
        Math.max(
            300,
            rect.width
        );


    const h =
        Math.max(
            140,
            rect.height
        );


    canvas.width =
        w * dpr;

    canvas.height =
        h * dpr;


    const ctx =
        canvas.getContext("2d");


    ctx.setTransform(
        dpr,
        0,
        0,
        dpr,
        0,
        0
    );


    ctx.clearRect(
        0,
        0,
        w,
        h
    );


    const top = 8;
    const bottom = h - 4;
    const range = 40;


    ctx.strokeStyle =
        "rgba(255,255,255,.08)";

    ctx.lineWidth = 1;


    for (
        let i = 0;
        i <= 4;
        i++
    ) {

        const y =
            top +
            (bottom - top) *
            (i / 4);


        ctx.beginPath();

        ctx.moveTo(
            0,
            y
        );

        ctx.lineTo(
            w,
            y
        );

        ctx.stroke();
    }


    const data =
        temperaturaHistorico.length
            ? temperaturaHistorico.map(
                x => x.valor
            )
            : [temperatura];


    const points =
        data.map(
            function(v, i) {

                return {

                    x:
                        data.length === 1
                            ? w / 2
                            : w *
                              (
                                  i /
                                  (data.length - 1)
                              ),

                    y:
                        bottom -
                        Math.max(
                            0,
                            Math.min(
                                range,
                                v
                            )
                        ) /
                        range *
                        (bottom - top)
                };
            }
        );


    if (
        points.length < 2
    ) return;


    /* Área */

    ctx.beginPath();


    points.forEach(
        function(p, i) {

            if (i === 0) {

                ctx.moveTo(
                    p.x,
                    p.y
                );

            } else {

                ctx.lineTo(
                    p.x,
                    p.y
                );
            }
        }
    );


    ctx.lineTo(
        points[
            points.length - 1
        ].x,
        bottom
    );


    ctx.lineTo(
        points[0].x,
        bottom
    );


    ctx.closePath();


    const grad =
        ctx.createLinearGradient(
            0,
            top,
            0,
            bottom
        );


    grad.addColorStop(
        0,
        "rgba(255,159,28,.32)"
    );


    grad.addColorStop(
        1,
        "rgba(255,159,28,.03)"
    );


    ctx.fillStyle =
        grad;

    ctx.fill();


    /* Linha */

    ctx.beginPath();


    points.forEach(
        function(p, i) {

            if (i === 0) {

                ctx.moveTo(
                    p.x,
                    p.y
                );

            } else {

                ctx.lineTo(
                    p.x,
                    p.y
                );
            }
        }
    );


    ctx.strokeStyle =
        "#ff8f00";

    ctx.lineWidth = 3;

    ctx.lineJoin =
        "round";

    ctx.lineCap =
        "round";

    ctx.stroke();


    /* Último ponto */

    const last =
        points[
            points.length - 1
        ];


    ctx.beginPath();


    ctx.arc(
        last.x,
        last.y,
        8,
        0,
        Math.PI * 2
    );


    ctx.fillStyle =
        "#ff8f00";

    ctx.fill();


    ctx.lineWidth = 3;

    ctx.strokeStyle =
        "#fff";

    ctx.stroke();
}


window.addEventListener(
    "resize",
    desenharGraficoTemperatura
);


/* =====================================================
   ATUALIZAÇÃO AUTOMÁTICA
===================================================== */

/*
   IMPORTANTE:

   Não usamos mais Math.random()
   para temperatura e umidade.

   Os valores agora vêm exclusivamente
   do Arduino pela porta USB/Serial.
*/

function atualizarMedidor() {

    if (!arduinoConectado) {

        return;
    }

}


/* =====================================================
   INICIALIZAÇÃO
===================================================== */

desenharGraficoTemperatura();

atualizarStatusArduino(
    "Arduino desconectado"
);

</script>

</body>
</html># smart-soil
