<!DOCTYPE html>

<html lang="pt-BR">

<head>

<meta charset="UTF-8">

<meta name="viewport"
      content="width=device-width, initial-scale=1.0">

<title>Agro Monitor</title>

<style>

/* =====================================================
   CONFIGURAÇÃO GERAL
===================================================== */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{

    min-height:100vh;

    font-family:
        Arial,
        Helvetica,
        sans-serif;

    color:white;

    background:
        radial-gradient(
            circle at 20% 20%,
            rgba(46,204,113,.18),
            transparent 30%
        ),

        radial-gradient(
            circle at 80% 80%,
            rgba(52,152,219,.15),
            transparent 30%
        ),

        linear-gradient(
            135deg,
            #04130a,
            #0a2415,
            #06140c
        );
}


/* =====================================================
   TELAS
===================================================== */

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


/* =====================================================
   INÍCIO
===================================================== */

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

    background:
        linear-gradient(
            135deg,
            #1f9d55,
            #2ecc71
        );

    box-shadow:
        0 15px 40px
        rgba(46,204,113,.25);
}

.inicio h1{

    font-size:44px;

    margin-bottom:12px;
}

.inicio p{

    color:#8eaa98;

    margin-bottom:40px;
}


/* =====================================================
   MENU
===================================================== */

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

    background:
        rgba(255,255,255,.06);

    border:
        1px solid
        rgba(255,255,255,.1);

    transition:.25s ease;
}

.menu-barra:hover{

    transform:translateY(-4px);

    background:
        rgba(46,204,113,.12);

    border-color:
        rgba(46,204,113,.4);

    box-shadow:
        0 15px 35px
        rgba(46,204,113,.12);
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

    background:
        rgba(46,204,113,.15);
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


/* =====================================================
   CONTAINER
===================================================== */

.container{

    width:100%;

    max-width:1050px;
}

.medidor-container{

    max-width:1400px;
}


/* =====================================================
   TOPO
===================================================== */

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

    background:
        rgba(255,255,255,.07);

    cursor:pointer;

    transition:.2s;
}

.voltar:hover{

    background:
        rgba(255,255,255,.15);
}

.titulo{

    font-size:25px;

    font-weight:bold;
}


/* =====================================================
   CONEXÃO ARDUINO
===================================================== */

.conexao-arduino{

    margin-bottom:20px;

    padding:16px 20px;

    border-radius:18px;

    display:flex;

    align-items:center;

    gap:15px;

    flex-wrap:wrap;

    background:
        rgba(255,255,255,.05);

    border:
        1px solid
        rgba(255,255,255,.08);
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

    box-shadow:
        0 0 12px
        rgba(46,204,113,.8);
}

.botao-arduino{

    border:none;

    padding:11px 17px;

    border-radius:12px;

    color:white;

    background:
        rgba(46,204,113,.18);

    border:
        1px solid
        rgba(46,204,113,.35);

    cursor:pointer;

    font-weight:bold;
}

.botao-arduino:hover{

    background:
        rgba(46,204,113,.3);
}

.botao-desconectar{

    background:
        rgba(255,71,87,.15);

    border-color:
        rgba(255,71,87,.3);
}


/* =====================================================
   CARDS
===================================================== */

.card{

    padding:30px;

    border-radius:25px;

    background:
        rgba(255,255,255,.05);

    border:
        1px solid
        rgba(255,255,255,.08);

    backdrop-filter:blur(15px);
}


/* =====================================================
   MEDIDOR
===================================================== */

.medidor-layout{

    display:grid;

    grid-template-columns:
        1fr 1fr;

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


/* =====================================================
   UMIDADE
===================================================== */

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

    background:
        conic-gradient(
            #2ecc71 0deg,
            #2ecc71 180deg,
            rgba(255,255,255,.06) 180deg
        );

    transition:
        background .5s;
}

.meter::before{

    content:"";

    position:absolute;

    width:265px;
    height:265px;

    border-radius:50%;

    background:
        radial-gradient(
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

    background:
        rgba(255,255,255,.07);
}

.barra-progresso{

    height:100%;

    width:50%;

    border-radius:20px;

    background:#2ecc71;

    transition:
        width .5s,
        background .3s;
}


/* =====================================================
   TEMPERATURA
===================================================== */

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

    background:
        conic-gradient(
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


/* =====================================================
   GRÁFICO
===================================================== */

.temp-chart-box{

    position:relative;

    margin:0 auto;

    width:94%;

    height:238px;

    border:
        1px solid
        rgba(255,255,255,.08);

    border-radius:20px;

    background:
        rgba(255,255,255,.025);

    padding:
        17px 20px
        12px 60px;
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


/* =====================================================
   ANÁLISES
===================================================== */

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

    grid-template-columns:
        repeat(4,1fr);

    gap:18px;
}

.info{

    padding:20px 24px;

    min-height:130px;

    border-radius:18px;

    background:
        rgba(255,255,255,.04);

    border:
        1px solid
        rgba(255,255,255,.06);
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

    background:
        rgba(52,152,219,.18);

    color:#27a9ff;

    font-size:13px;
}

.info-badge.conectado{

    background:
        rgba(46,204,113,.16);

    color:#35df73;
}

.dica{

    display:flex;

    align-items:center;

    gap:10px;

    margin-top:20px;

    padding:17px 22px;

    border-radius:17px;

    border:
        1px solid
        rgba(255,255,255,.06);

    background:
        rgba(255,255,255,.035);

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


/* =====================================================
   NOVO HISTÓRICO
===================================================== */

.historico-layout{

    width:100%;

    display:grid;

    grid-template-columns:
        1fr 1fr;

    gap:22px;
}


/* BARRAS GRANDES */

.historico-barra{

    min-height:600px;

    padding:28px;

    border-radius:28px;

    background:
        rgba(255,255,255,.05);

    border:
        1px solid
        rgba(255,255,255,.08);

    backdrop-filter:blur(15px);

    display:flex;

    flex-direction:column;
}


/* CABEÇALHO */

.historico-barra-titulo{

    display:flex;

    align-items:center;

    gap:12px;

    padding-bottom:20px;

    margin-bottom:18px;

    border-bottom:
        1px solid
        rgba(255,255,255,.08);
}

.historico-barra-icone{

    width:50px;
    height:50px;

    border-radius:15px;

    display:flex;

    align-items:center;

    justify-content:center;

    font-size:25px;

    background:
        rgba(46,204,113,.15);
}

.historico-barra-titulo h2{

    font-size:22px;

    margin-bottom:4px;
}

.historico-barra-titulo p{

    color:#819889;

    font-size:13px;
}


/* LISTA */

.lista-historico{

    flex:1;

    overflow-y:auto;

    padding-right:5px;
}


/* ITEM DO HISTÓRICO */

.historico-item{

    display:flex;

    align-items:center;

    justify-content:space-between;

    gap:15px;

    padding:17px;

    margin-bottom:10px;

    border-radius:16px;

    background:
        rgba(255,255,255,.04);

    border:
        1px solid
        rgba(255,255,255,.06);

    transition:.2s;
}

.historico-item:hover{

    background:
        rgba(255,255,255,.07);

    transform:translateX(3px);
}

.historico-hora{

    color:#819889;

    font-size:13px;
}

.historico-item strong{

    font-size:22px;
}


/* CORES */

.historico-umidade
.historico-item strong{

    color:#2ecc71;
}

.historico-temperatura
.historico-item strong{

    color:#ff9f1c;
}


/* VAZIO */

.historico-vazio{

    height:300px;

    display:flex;

    flex-direction:column;

    align-items:center;

    justify-content:center;

    text-align:center;

    color:#667c6e;

    font-size:15px;
}

.historico-vazio-icone{

    font-size:50px;

    margin-bottom:15px;
}


/* RODAPÉ DO HISTÓRICO */

.historico-atualizacao{

    margin-top:15px;

    padding-top:15px;

    border-top:
        1px solid
        rgba(255,255,255,.06);

    color:#667c6e;

    font-size:12px;

    text-align:center;
}


/* =====================================================
   CONFIGURAÇÕES
===================================================== */

.config-card{

    display:flex;

    flex-direction:column;

    gap:22px;
}

.config-item{

    padding:20px;

    border-radius:18px;

    background:
        rgba(255,255,255,.04);

    border:
        1px solid
        rgba(255,255,255,.07);
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

    border:
        1px solid
        rgba(255,255,255,.12);

    background:
        rgba(255,255,255,.06);

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

    background:
        rgba(46,204,113,.18);

    border:
        1px solid
        rgba(46,204,113,.3);

    cursor:pointer;

    font-weight:bold;
}

.botao-parar{

    background:
        rgba(255,71,87,.15);

    border-color:
        rgba(255,71,87,.3);
}

.irrigador-status{

    display:flex;

    align-items:center;

    gap:10px;

    margin-top:15px;

    padding:13px;

    border-radius:12px;

    background:
        rgba(255,255,255,.04);

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

    box-shadow:
        0 0 12px
        rgba(46,204,113,.8);
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


/* =====================================================
   RESPONSIVO
===================================================== */

@media(max-width:900px){

    .medidor-layout{

        grid-template-columns:1fr;
    }

    .analises-card{

        grid-column:auto;
    }

    .analises-grid{

        grid-template-columns:
            1fr 1fr;
    }

    .historico-layout{

        grid-template-columns:1fr;
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

    .historico-barra{

        min-height:500px;

        padding:20px;
    }

}

</style>


<style id="agro-monitor-aesthetic">
:root{
--am-bg:#031a0d;--am-panel:rgba(7,45,27,.64);--am-border:rgba(67,225,116,.20);
--am-border-hover:rgba(67,225,116,.48);--am-green:#35e878;--am-text:#f3f8f4;--am-muted:#91a99b;
}
html{background:var(--am-bg)}
body{
position:relative;overflow-x:hidden;color:var(--am-text);
background:radial-gradient(circle at 82% 42%,rgba(34,144,76,.23),transparent 31%),
radial-gradient(circle at 13% 83%,rgba(20,112,57,.18),transparent 27%),
linear-gradient(135deg,#02150a 0%,#062719 52%,#03160d 100%);
}
body::before{
content:"";position:fixed;inset:0;pointer-events:none;z-index:0;opacity:.14;
background-image:radial-gradient(circle,rgba(56,220,110,.35) 0 1.5px,transparent 2px);
background-size:38px 38px;mask-image:linear-gradient(to bottom,transparent,black 25%,black 80%,transparent);
}
#inicio{position:relative;align-items:flex-start;padding-top:18px;overflow:hidden}
#inicio::after{
content:"";position:absolute;right:-8%;bottom:-14%;width:54%;height:58%;pointer-events:none;opacity:.15;
background:repeating-linear-gradient(164deg,transparent 0 18px,rgba(58,176,76,.62) 19px 21px),
linear-gradient(160deg,transparent 0 43%,rgba(18,86,43,.9) 44% 100%);
transform:perspective(700px) rotateX(10deg);
}
.senai-brand{
position:absolute;z-index:4;top:15px;left:50%;transform:translateX(-50%);
width:min(125px,25vw);height:54px;display:flex;align-items:center;justify-content:center;
}
.senai-brand::after{
content:"";position:absolute;top:61px;left:50%;transform:translateX(-50%);
width:68vw;max-width:900px;height:2px;
background:linear-gradient(90deg,transparent,rgba(220,230,225,.48),transparent);
}
.senai-brand img{width:100%;height:auto;display:block;object-fit:contain}
.inicio{position:relative;z-index:2;max-width:820px;padding-top:112px}
.logo{
width:118px;height:118px;margin:0 auto 20px;border-radius:30px;font-size:58px;
background:linear-gradient(145deg,#10b866,#063d25);
box-shadow:0 0 45px rgba(20,220,100,.16),inset 0 0 0 1px rgba(255,255,255,.08);
}
.inicio h1{font-size:62px;line-height:1;font-weight:800;letter-spacing:-2px;margin-bottom:0}
.inicio p{font-size:21px;color:#dfe9e2;margin:22px auto 35px}
.menu{gap:14px}
.menu-barra{
min-height:112px;padding:22px 25px;border-radius:24px;
background:linear-gradient(100deg,rgba(8,51,30,.76),rgba(6,37,24,.55));
border:1px solid var(--am-border);box-shadow:0 12px 35px rgba(0,0,0,.15);
}
.menu-barra:hover{
transform:translateY(-3px);
background:linear-gradient(100deg,rgba(10,68,38,.82),rgba(7,45,27,.66));
border-color:var(--am-border-hover);box-shadow:0 16px 40px rgba(20,220,90,.10);
}
.menu-icone{width:64px;height:64px;border-radius:19px;font-size:30px;background:rgba(5,125,59,.35)}
.menu-conteudo h2{font-size:21px;margin-bottom:10px}
.menu-conteudo span{color:#94a99d;font-size:14px}
.seta{font-size:34px;color:var(--am-green)}
.tela:not(#inicio){position:relative;z-index:1;padding:28px 20px;align-items:flex-start}
.container{max-width:1120px}.medidor-container{max-width:1400px}
.topo{margin-bottom:22px}.titulo{font-size:28px;letter-spacing:-.4px}
.voltar{
padding:11px 17px;border-radius:13px;background:rgba(255,255,255,.055);
border:1px solid rgba(255,255,255,.08)
}
.voltar:hover{background:rgba(25,180,88,.13);border-color:var(--am-border)}
.card,.conexao-arduino,.historico-barra{
background:linear-gradient(135deg,rgba(8,51,30,.68),rgba(5,30,19,.62));
border:1px solid var(--am-border);box-shadow:0 15px 45px rgba(0,0,0,.16);
backdrop-filter:blur(16px)
}
.conexao-arduino{padding:17px 20px;border-radius:19px}
.botao-arduino,.botao-config{
background:rgba(19,184,91,.17);border:1px solid rgba(53,232,120,.30);
color:white;border-radius:12px;transition:.2s ease
}
.botao-arduino:hover,.botao-config:hover{
background:rgba(19,184,91,.30);border-color:rgba(53,232,120,.52);transform:translateY(-1px)
}
.card{border-radius:26px}
.sensor-panel{min-height:585px}
.sensor-heading{margin-bottom:14px}.sensor-heading h2{font-size:23px}.sensor-heading p{color:#8fa79a}
.meter{
background:conic-gradient(var(--am-green) 0deg,var(--am-green) 180deg,rgba(255,255,255,.06) 180deg);
box-shadow:0 0 50px rgba(36,220,100,.08)
}
.meter::before{background:radial-gradient(circle,#102d1c,#04150b)}
.barra{background:rgba(255,255,255,.065)}
.barra-progresso{background:linear-gradient(90deg,#16b95d,#4eea7c)}
.temperatura-meter{
background:conic-gradient(from 225deg,#ff7a00 0deg,#ff9f1c 230deg,rgba(255,255,255,.06) 230deg,rgba(255,255,255,.06) 270deg,transparent 270deg 360deg)
}
.temperatura-meter::before{background:#061a10}
.temp-chart-box{border-color:rgba(67,225,116,.14);background:rgba(255,255,255,.025)}
.analises-card{background:linear-gradient(135deg,rgba(7,49,28,.72),rgba(5,30,19,.64))}
.info{background:rgba(255,255,255,.035);border-color:rgba(67,225,116,.10);transition:.2s}
.info:hover{border-color:rgba(67,225,116,.27);background:rgba(20,100,55,.10)}
.dica{background:rgba(255,255,255,.035);border-color:rgba(67,225,116,.11)}
.config-card{padding:30px}
.config-item{
background:rgba(255,255,255,.025);border:1px solid rgba(67,225,116,.10);
border-radius:20px;padding:22px;margin-bottom:16px
}
.config-item:last-child{margin-bottom:0}
.config-item h3{font-size:19px;margin-bottom:8px}.config-item p{color:#91a79a}
.config-input,.config-select{
background:#071e12;color:white;border:1px solid rgba(67,225,116,.20);border-radius:11px
}
.config-input:focus,.config-select:focus{
outline:none;border-color:rgba(53,232,120,.60);box-shadow:0 0 0 3px rgba(53,232,120,.08)
}
.historico-layout{gap:18px}
.historico-barra{border-radius:24px;padding:25px}
.historico-barra-titulo h2{font-size:21px}
.historico-barra-titulo p,.historico-atualizacao{color:#91a79a}
.historico-item{background:rgba(255,255,255,.035);border:1px solid rgba(67,225,116,.09);border-radius:14px}
@media(max-width:800px){.inicio{padding-top:102px}.inicio h1{font-size:45px}.senai-brand{width:105px}}
@media(max-width:520px){
#inicio{padding-left:12px;padding-right:12px}.inicio{padding-top:90px}.logo{width:90px;height:90px;font-size:44px}
.inicio h1{font-size:40px}.inicio p{font-size:17px}.menu-barra{min-height:96px;padding:18px}
.menu-icone{width:54px;height:54px;flex-basis:54px}.senai-brand::after{width:88vw}
}
</style>

</head>

<body>


<!-- =====================================================
     TELA INICIAL
===================================================== -->

<section
    id="inicio"
    class="tela ativa">

<div class="senai-brand">
    <img src="senai.png" alt="SENAI">
</div>

<div class="inicio">

<div class="logo">
🌱
</div>

<h1>
Agro Monitor
</h1>

<p>
Sistema inteligente de monitoramento do solo
</p>

<div class="menu">


<div
    class="menu-barra"
    onclick="abrirTela('medidor')">

<div class="menu-icone">
💧
</div>

<div class="menu-conteudo">

<h2>
Medidor
</h2>

<span>
Acompanhe a umidade do solo
em tempo real
</span>

</div>

<div class="seta">
→
</div>

</div>


<div
    class="menu-barra"
    onclick="abrirTela('historicoTela')">

<div class="menu-icone">
📜
</div>

<div class="menu-conteudo">

<h2>
Histórico
</h2>

<span>
Veja as medições registradas
a cada minuto
</span>

</div>

<div class="seta">
→
</div>

</div>


<div
    class="menu-barra"
    onclick="abrirTela('configuracoes')">

<div class="menu-icone">
⚙️
</div>

<div class="menu-conteudo">

<h2>
Configurações
</h2>

<span>
Ajuste o sistema e o tempo de irrigação
</span>

</div>

<div class="seta">
→
</div>

</div>


</div>

</div>

</section>


<!-- =====================================================
     TELA DO MEDIDOR
===================================================== -->

<section
    id="medidor"
    class="tela">

<div class="container medidor-container">


<div class="topo">

<button
    class="voltar"
    onclick="abrirTela('inicio')">

← Voltar

</button>

<div class="titulo">
Medidor
</div>

<div></div>

</div>


<!-- CONEXÃO ARDUINO -->

<div class="conexao-arduino">

<div class="conexao-titulo">
🔌 Arduino
</div>

<div class="status-conexao">

<span
    id="pontoConexao"
    class="ponto-conexao">
</span>

<span id="textoConexao">
Arduino desconectado
</span>

</div>

<button
    id="botaoConectar"
    class="botao-arduino"
    onclick="conectarArduino()">

🔌 Conectar Arduino

</button>

<button
    id="botaoDesconectar"
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

<h2>
Umidade do Solo
</h2>

<p>
Sensor de Umidade
</p>

</div>

</div>


<div
    class="meter"
    id="meter">

<div class="valor">

<div
    class="numero"
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


<div
    class="status"
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

<div
    class="barra-progresso"
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


<div
    class="temperatura-meter"
    id="temperaturaMeter">

<div class="temperatura-valor">

<div
    class="temperatura-numero"
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

<canvas
    id="graficoTemperatura">
</canvas>

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


<div
    class="temperatura-status"
    id="temperaturaStatus">

Aguardando Arduino

</div>

</div>


<!-- ANÁLISES -->

<div class="card analises-card">

<div class="analises-titulo">

<span>
🌱
</span>

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

<div
    class="info-value"
    id="umidade">

50%

</div>

<div
    class="info-badge"
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

<div
    class="info-value"
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

<div
    class="info-value"
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

<div
    class="info-value"
    id="sensorOnline">

Offline

</div>

<div
    class="info-badge"
    id="sensorBadge">

Desconectado

</div>

</div>


</div>


<div class="dica">

<span class="dica-icon">
i
</span>

<strong>
Dica:
</strong>

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
     TELA DE CONFIGURAÇÕES
===================================================== -->

<section
    id="configuracoes"
    class="tela">

<div class="container">

<div class="topo">

<button
    class="voltar"
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

<span>
segundos
</span>

<button
    class="botao-config"
    onclick="salvarTempoIrrigacao()">

💾 Salvar

</button>

</div>

<div
    id="mensagemConfig"
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

<div
    id="contadorIrrigacao"
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

<option value="2000" selected>
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
     NOVA TELA DE HISTÓRICO
===================================================== -->

<section
    id="historicoTela"
    class="tela">

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


<div class="historico-layout">


<!-- =================================================
     BARRA ESQUERDA - UMIDADE
================================================= -->

<div
    class="historico-barra historico-umidade">

<div class="historico-barra-titulo">

<div class="historico-barra-icone">
💧
</div>

<div>

<h2>
Histórico de Umidade
</h2>

<p>
Medições registradas a cada minuto
</p>

</div>

</div>


<div
    id="historicoUmidade"
    class="lista-historico">

<div class="historico-vazio">

<div class="historico-vazio-icone">
💧
</div>

<p>
Aguardando a primeira medição...
</p>

</div>

</div>


<div class="historico-atualizacao">

Atualização automática a cada 1 minuto

</div>

</div>


<!-- =================================================
     BARRA DIREITA - TEMPERATURA
================================================= -->

<div
    class="historico-barra historico-temperatura">

<div class="historico-barra-titulo">

<div class="historico-barra-icone">
🌡️
</div>

<div>

<h2>
Histórico de Temperatura
</h2>

<p>
Medições registradas a cada minuto
</p>

</div>

</div>


<div
    id="historicoTemperatura"
    class="lista-historico">

<div class="historico-vazio">

<div class="historico-vazio-icone">
🌡️
</div>

<p>
Aguardando a primeira medição...
</p>

</div>

</div>


<div class="historico-atualizacao">

Atualização automática a cada 1 minuto

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


    const tela =
        document.getElementById(id);


    if(tela){

        tela.classList.add("ativa");

    }

}


/* =====================================================
   VARIÁVEIS
===================================================== */

let umidade = 50;

let temperatura = 25;

let leituraSensor = 0;

let valvulaArduino =
    "DESLIGADA";


/* =====================================================
   HISTÓRICO
===================================================== */

let historicoUmidade = [];

let historicoTemperatura = [];


/* =====================================================
   SERIAL
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
            .style.display =
                "none";


        document
            .getElementById("botaoDesconectar")
            .style.display =
                "block";


        document
            .getElementById("sensorOnline")
            .textContent =
                "Online";


        document
            .getElementById("sensorBadge")
            .textContent =
                "Conectado";


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
   LER SERIAL
===================================================== */

async function lerSerial(){

    if(!portaSerial)
        return;


    lendoSerial = true;


    const decoder =
        new TextDecoderStream();


    const entrada =
        portaSerial
            .readable
            .pipeThrough(decoder);


    leitorSerial =
        entrada.getReader();


    try{

        while(lendoSerial){

            const {value,done} =
                await leitorSerial.read();


            if(done)
                break;


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

    if(!linha)
        return;


    console.log(
        "Arduino:",
        linha
    );


    /*
       Formato esperado:

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
            valvulaMatch[1]
                .toUpperCase();

    }


    if(
        temperaturaMatch ||
        umidadeMatch
    ){

        atualizarMedidorReal();

    }

}


/* =====================================================
   ATUALIZAR MEDIDOR
===================================================== */

function atualizarMedidorReal(){

    umidade =
        Math.max(
            0,
            Math.min(
                100,
                umidade
            )
        );


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
        Math.round(umidade);


    umidadeTexto.textContent =
        Math.round(umidade) + "%";


    leitura.textContent =
        leituraSensor;


    let cor;


    if(umidade < 30){

        cor = "#ff4757";

        status.textContent =
            "Solo seco";

        estado.textContent =
            "Seco";

    }

    else if(umidade < 60){

        cor = "#f1c40f";

        status.textContent =
            "Umidade moderada";

        estado.textContent =
            "Moderado";

    }

    else if(umidade < 85){

        cor = "#2ecc71";

        status.textContent =
            "Solo úmido";

        estado.textContent =
            "Ideal";

    }

    else{

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
       BADGE
    ================================================= */

    const badge =
        document.getElementById(
            "umidadeBadge"
        );


    if(umidade >= 85){

        badge.textContent =
            "Muito úmido";

    }

    else if(umidade >= 60){

        badge.textContent =
            "Ideal";

    }

    else if(umidade >= 30){

        badge.textContent =
            "Moderado";

    }

    else{

        badge.textContent =
            "Seco";

    }


    /* =================================================
       TEMPERATURA
    ================================================= */

    temperaturaNumero.textContent =
        Number(temperatura).toFixed(1);


    let corTemperatura;


    if(temperatura < 20){

        corTemperatura =
            "#3498db";

        temperaturaStatus.textContent =
            "Temperatura baixa";

    }

    else if(temperatura <= 30){

        corTemperatura =
            "#2ecc71";

        temperaturaStatus.textContent =
            "Temperatura normal";

    }

    else if(temperatura <= 35){

        corTemperatura =
            "#f1c40f";

        temperaturaStatus.textContent =
            "Temperatura elevada";

    }

    else{

        corTemperatura =
            "#ff4757";

        temperaturaStatus.textContent =
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
       STATUS
    ================================================= */

    document
        .getElementById("sensorOnline")
        .textContent =
            "Online";


    document
        .getElementById("sensorBadge")
        .textContent =
            "Conectado";


    document
        .getElementById("sensorBadge")
        .classList.add("conectado");


    document
        .getElementById("dicaTexto")
        .textContent =
            "Dados recebidos diretamente do Arduino. " +
            "Temperatura: " +
            Number(temperatura).toFixed(1) +
            "°C | Umidade: " +
            Math.round(umidade) +
            "%.";

}


/* =====================================================
   HISTÓRICO
===================================================== */

function registrarHistorico(){

    /*
       IMPORTANTE:

       Aqui não existe atualização
       a cada segundo.

       Esta função é chamada somente
       uma vez a cada 60 segundos.
    */


    if(!portaSerial){

        return;

    }


    const agora =
        new Date();


    const hora =
        agora.toLocaleTimeString(
            "pt-BR",
            {
                hour:"2-digit",
                minute:"2-digit"
            }
        );


    /* =================================================
       UMIDADE
    ================================================= */

    historicoUmidade.push({

        valor:
            Math.round(umidade),

        hora:
            hora

    });


    /* =================================================
       TEMPERATURA
    ================================================= */

    historicoTemperatura.push({

        valor:
            Number(
                temperatura
            ).toFixed(1),

        hora:
            hora

    });


    /*
       Mantém somente 24 registros.
    */

    if(
        historicoUmidade.length > 24
    ){

        historicoUmidade.shift();

    }


    if(
        historicoTemperatura.length > 24
    ){

        historicoTemperatura.shift();

    }


    mostrarHistoricoUmidade();

    mostrarHistoricoTemperatura();

}


/* =====================================================
   MOSTRAR HISTÓRICO DE UMIDADE
===================================================== */

function mostrarHistoricoUmidade(){

    const elemento =
        document.getElementById(
            "historicoUmidade"
        );


    if(!elemento)
        return;


    elemento.innerHTML = "";


    if(
        historicoUmidade.length === 0
    ){

        elemento.innerHTML = `

            <div class="historico-vazio">

                <div class="historico-vazio-icone">
                    💧
                </div>

                <p>
                    Aguardando a primeira medição...
                </p>

            </div>

        `;

        return;

    }


    historicoUmidade
        .slice()
        .reverse()
        .forEach(
            function(registro){

                const item =
                    document.createElement(
                        "div"
                    );


                item.className =
                    "historico-item";


                item.innerHTML = `

                    <div>

                        <span
                            class="historico-hora">

                            ${registro.hora}

                        </span>

                    </div>

                    <strong
                        style="color:#2ecc71;">

                        ${registro.valor}%

                    </strong>

                `;


                elemento.appendChild(
                    item
                );

            }
        );

}


/* =====================================================
   MOSTRAR HISTÓRICO DE TEMPERATURA
===================================================== */

function mostrarHistoricoTemperatura(){

    const elemento =
        document.getElementById(
            "historicoTemperatura"
        );


    if(!elemento)
        return;


    elemento.innerHTML = "";


    if(
        historicoTemperatura.length === 0
    ){

        elemento.innerHTML = `

            <div class="historico-vazio">

                <div class="historico-vazio-icone">
                    🌡️
                </div>

                <p>
                    Aguardando a primeira medição...
                </p>

            </div>

        `;

        return;

    }


    historicoTemperatura
        .slice()
        .reverse()
        .forEach(
            function(registro){

                const item =
                    document.createElement(
                        "div"
                    );


                item.className =
                    "historico-item";


                item.innerHTML = `

                    <div>

                        <span
                            class="historico-hora">

                            ${registro.hora}

                        </span>

                    </div>

                    <strong
                        style="color:#ff9f1c;">

                        ${registro.valor}°C

                    </strong>

                `;


                elemento.appendChild(
                    item
                );

            }
        );

}


/* =====================================================
   ATUALIZAÇÃO DO HISTÓRICO
===================================================== */

/*
   60.000 milissegundos
   =
   1 minuto
*/

setInterval(

    function(){

        registrarHistorico();

    },

    60000

);


/* =====================================================
   DESCONECTAR ARDUINO
===================================================== */

async function desconectarArduino(){

    lendoSerial = false;


    try{

        if(leitorSerial){

            await leitorSerial.cancel();

            leitorSerial = null;

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


    portaSerial = null;


    document
        .getElementById(
            "pontoConexao"
        )
        .classList.remove(
            "conectado"
        );


    document
        .getElementById(
            "textoConexao"
        )
        .textContent =
            "Arduino desconectado";


    document
        .getElementById(
            "botaoConectar"
        )
        .style.display =
            "block";


    document
        .getElementById(
            "botaoDesconectar"
        )
        .style.display =
            "none";


    document
        .getElementById(
            "sensorOnline"
        )
        .textContent =
            "Offline";


    document
        .getElementById(
            "sensorBadge"
        )
        .textContent =
            "Desconectado";


    document
        .getElementById(
            "sensorBadge"
        )
        .classList.remove(
            "conectado"
        );


    document
        .getElementById(
            "dicaTexto"
        )
        .textContent =
            "Arduino desconectado. Conecte novamente pela porta USB para receber os dados reais.";

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


let timerIrrigacao = null;

let segundosRestantes = 0;


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

        campoTempo.value =
            tempoIrrigacao;

    }


    if(campoIntervalo){

        campoIntervalo.value =
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


    let valor =
        Number(
            campo.value
        );


    if(!valor || valor < 1){

        valor = 1;

    }


    if(valor > 3600){

        valor = 3600;

    }


    tempoIrrigacao =
        Math.round(valor);


    campo.value =
        tempoIrrigacao;


    localStorage.setItem(
        "tempoIrrigacao",
        tempoIrrigacao
    );


    const mensagem =
        document.getElementById(
            "mensagemConfig"
        );


    mensagem.textContent =
        "✓ Tempo salvo: " +
        tempoIrrigacao +
        " segundos";


    setTimeout(

        function(){

            mensagem.textContent = "";

        },

        3000

    );

}


/* =====================================================
   IRRIGAÇÃO
===================================================== */

function iniciarIrrigacao(){

    if(
        timerIrrigacao !== null
    ){

        return;

    }


    salvarTempoIrrigacao();


    segundosRestantes =
        tempoIrrigacao;


    document
        .getElementById(
            "indicadorIrrigador"
        )
        .classList.add(
            "ligado"
        );


    document
        .getElementById(
            "statusIrrigador"
        )
        .textContent =
            "Irrigador ligado";


    atualizarContadorIrrigacao();


    timerIrrigacao =
        setInterval(

            function(){

                segundosRestantes--;

                atualizarContadorIrrigacao();


                if(
                    segundosRestantes <= 0
                ){

                    pararIrrigacao();

                }

            },

            1000

        );

}


function pararIrrigacao(){

    if(
        timerIrrigacao !== null
    ){

        clearInterval(
            timerIrrigacao
        );

        timerIrrigacao = null;

    }


    segundosRestantes = 0;


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


    status.textContent =
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


    if(!contador)
        return;


    const minutos =
        Math.floor(
            segundosRestantes / 60
        );


    const segundos =
        segundosRestantes % 60;


    contador.textContent =
        String(minutos)
            .padStart(2,"0") +
        ":" +
        String(segundos)
            .padStart(2,"0");

}


/* =====================================================
   INTERVALO DO SENSOR
===================================================== */

function alterarIntervaloSensor(){

    intervaloSensor =
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
   RESTAURAR CONFIGURAÇÕES
===================================================== */

function restaurarConfiguracoes(){

    tempoIrrigacao = 30;

    intervaloSensor = 2000;


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


    mensagem.textContent =
        "✓ Configurações restauradas";


    setTimeout(

        function(){

            mensagem.textContent = "";

        },

        3000

    );

}


/* =====================================================
   INICIALIZAÇÃO
===================================================== */

carregarConfiguracoes();


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


/* =====================================================
   FIM
===================================================== */

</script>

</body>

</html>
