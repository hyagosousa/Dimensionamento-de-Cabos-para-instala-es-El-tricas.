<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Simulador Elétrico Profissional</title>
    <style>
        :root {
            --bg-dark: #0f172a;
            --card-bg: #1e293b;
            --accent: #10b981;
            --accent-hover: #059669;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border: #334155;
            --danger: #ef4444;
            --success: #38bdf8;
        }

        * {
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: 'Inter', system-ui, -apple-system, sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            margin: 0;
            padding: 12px;
        }

        .container {
            width: 100%;
            max-width: 1050px;
            margin: 0 auto;
            background: var(--card-bg);
            padding: 20px;
            border-radius: 14px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
            border: 1px solid var(--border);
        }

        .header {
            text-align: center;
            border-bottom: 2px solid var(--border);
            padding-bottom: 16px;
            margin-bottom: 20px;
        }

        .header h1 {
            margin: 0;
            font-size: 1.5rem;
            color: var(--text-main);
            letter-spacing: -0.5px;
        }

        .header h1 span {
            color: var(--accent);
        }

        .header p {
            color: var(--text-muted);
            margin-top: 6px;
            font-size: 0.85rem;
        }

        .form-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 14px;
            margin-bottom: 20px;
        }

        @media(min-width: 768px) {
            .form-grid {
                grid-template-columns: 2fr 1fr 1fr 1fr auto;
                align-items: end;
                gap: 12px;
            }
        }

        label {
            font-weight: 600;
            font-size: 0.8rem;
            color: var(--text-muted);
            display: block;
            margin-bottom: 6px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        input, select {
            width: 100%;
            padding: 14px;
            background-color: #0b0f19;
            border: 1px solid var(--border);
            color: var(--text-main);
            border-radius: 10px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        input:focus, select:focus {
            border-color: var(--accent);
        }

        button {
            background-color: var(--accent);
            color: #0f172a;
            border: none;
            padding: 14px 20px;
            border-radius: 10px;
            cursor: pointer;
            font-weight: 700;
            font-size: 1rem;
            width: 100%;
            transition: background 0.2s, transform 0.1s;
        }

        button:active {
            transform: scale(0.98);
        }

        .btn-remover {
            background-color: rgba(239, 68, 68, 0.15);
            color: var(--danger);
            border: 1px solid rgba(239, 68, 68, 0.3);
            padding: 10px 14px;
            font-size: 0.85rem;
            width: auto;
            border-radius: 8px;
        }

        .acoes-topo {
            display: flex;
            justify-content: stretch;
            margin-bottom: 15px;
        }

        .btn-exportar {
            background-color: #3b82f6;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
        }

        .table-responsive {
            width: 100%;
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
            border-radius: 10px;
            border: 1px solid var(--border);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            white-space: nowrap;
        }

        th, td {
            border-bottom: 1px solid var(--border);
            padding: 12px 10px;
            text-align: center;
            font-size: 0.85rem;
        }

        th {
            background-color: #111827;
            color: var(--text-muted);
            text-transform: uppercase;
            font-size: 0.7rem;
            letter-spacing: 0.8px;
        }

        tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.01);
        }

        .resumo-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
            margin-top: 25px;
        }

        @media(min-width: 550px) {
            .resumo-container {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        .card-resumo {
            background: #111827;
            padding: 16px;
            border-radius: 10px;
            border: 1px solid var(--border);
            border-left: 4px solid var(--accent);
        }

        .card-resumo h3 {
            margin: 0 0 6px 0;
            font-size: 0.75rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .card-resumo p {
            margin: 0;
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--text-main);
        }

        .footer-suporte {
            text-align: center;
            margin-top: 25px;
            padding-top: 16px;
            border-top: 1px solid var(--border);
            font-size: 0.8rem;
            color: var(--text-muted);
            line-height: 1.5;
        }

        .footer-suporte a {
            color: var(--accent);
            text-decoration: none;
            font-weight: bold;
            margin: 0 4px;
        }

        @media print {
            body { background: white; color: black; padding: 0; }
            .container { box-shadow: none; border: none; background: white; width: 100%; max-width: 100%; padding: 0; }
            .form-grid, .acoes-topo, .btn-remover, th:last-child, td:last-child { display: none !important; }
            .header h1 { color: #000; }
            .card-resumo { background: #f8fafc; border: 1px solid #cbd5e1; border-left: 4px solid #059669; }
            .footer-suporte { color: #475569; border-top: 1px solid #cbd5e1; }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1>Simulador Elétrico <span>Profissional</span></h1>
        <p>Dimensionamento de Cargas, Fiação e Proteção (NBR 5410)</p>
    </div>

    <div class="form-grid">
        <div>
            <label>Equipamento</label>
            <input type="text" id="nomeEq" placeholder="Ex: Geladeira 12V">
        </div>
        <div>
            <label>Potência (W)</label>
            <input type="number" id="potenciaEq" inputmode="numeric" placeholder="Ex: 60">
        </div>
        <div>
            <label>Tensão</label>
            <select id="tensaoEq">
                <option value="12">12V (CC)</option>
                <option value="24">24V (CC)</option>
                <option value="127">127V (CA)</option>
                <option value="220" selected>220V (CA)</option>
            </select>
        </div>
        <div>
            <label>Distância Ida (m)</label>
            <input type="number" id="distanciaEq" inputmode="numeric" placeholder="Ex: 3" value="3">
        </div>
        <div>
            <label>&nbsp;</label>
            <button onclick="adicionarEquipamento()">+ Adicionar</button>
        </div>
    </div>

    <div class="acoes-topo">
        <button class="btn-exportar" onclick="exportarRelatorio()">🖨️ Exportar Relatório (PDF)</button>
    </div>

    <div class="table-responsive">
        <table id="tabelaEquipamentos">
            <thead>
                <tr>
                    <th>Equipamento</th>
                    <th>Potência</th>
                    <th>Tensão</th>
                    <th>Corrente ($I_b$)</th>
                    <th>Distância</th>
                    <th>Cabo Ideal</th>
                    <th>Disjuntor ($I_n$)</th>
                    <th>Ações</th>
                </tr>
            </thead>
            <tbody>
                <!-- Itens adicionados entram dinamicamente -->
            </tbody>
        </table>
    </div>

    <div class="resumo-container">
        <div class="card-resumo">
            <h3>Corrente Total (12V)</h3>
            <p id="total12v">0.00 A</p>
        </div>
        <div class="card-resumo" style="border-left-color: #3b82f6;">
            <h3>Total de Equipamentos</h3>
            <p id="totalItens">0</p>
        </div>
    </div>

    <div class="footer-suporte">
        Dúvidas ou suporte técnico?<br>
        WhatsApp: <a href="https://wa.me/5534997786637" target="_blank">(34) 99778-6637</a> | 
        Instagram: <a href="https://instagram.com/hyagueera" target="_blank">@hyagueera</a>
    </div>
</div>

<script>
    let equipamentos = [];
    const disjuntoresPadrao = [2, 4, 6, 10, 16, 20, 25, 32, 40, 50, 63, 70, 80, 100, 125, 150];

    function calcularProjeto(corrente, distancia, tensao) {
        let fator = (tensao == 12 || tensao == 24) ? 2 : 1;
        let rho = 0.0172;
        let deltaVMax = tensao * 0.03; 
        let secaoMinima = (fator * rho * distancia * corrente) / deltaVMax;

        const tabelaCabos = [
            {bitola: 1.5, cap: 15},
            {bitola: 2.5, cap: 21},
            {bitola: 4.0, cap: 28},
            {bitola: 6.0, cap: 36},
            {bitola: 10.0, cap: 50},
            {bitola: 16.0, cap: 68},
            {bitola: 25.0, cap: 89},
            {bitola: 35.0, cap: 111},
            {bitola: 50.0, cap: 134}
        ];

        let caboEscolhido = "50+ mm²";
        let capacidadeCaboIz = 200;

        for (let item of tabelaCabos) {
            if (item.bitola >= secaoMinima && item.cap >= corrente) {
                caboEscolhido = item.bitola + " mm²";
                capacidadeCaboIz = item.cap;
                break;
            }
        }

        let disjuntorEscolhido = null;
        for (let d of disjuntoresPadrao) {
            if (d >= corrente && d <= capacidadeCaboIz) {
                disjuntorEscolhido = d + "A";
                break;
            }
        }

        if (!disjuntorEscolhido) {
            let fallback = disjuntoresPadrao.find(d => d >= corrente);
            disjuntorEscolhido = fallback ? (fallback + "A") : "150A+";
        }

        return { cabo: caboEscolhido, disjuntor: disjuntorEscolhido };
    }

    function adicionarEquipamento() {
        let nome = document.getElementById("nomeEq").value.trim();
        let potencia = parseFloat(document.getElementById("potenciaEq").value);
        let tensao = parseFloat(document.getElementById("tensaoEq").value);
        let distancia = parseFloat(document.getElementById("distanciaEq").value);

        if (!nome || isNaN(potencia) || potencia <= 0 || isNaN(distancia) || distancia <= 0) {
            alert("Por favor, preencha todos os campos corretamente.");
            return;
        }

        let corrente = potencia / tensao;
        let resultado = calcularProjeto(corrente, distancia, tensao);

        equipamentos.push({ 
            nome, 
            potencia, 
            tensao, 
            corrente, 
            distancia, 
            caboRecomendado: resultado.cabo, 
            disjuntorRecomendado: resultado.disjuntor 
        });

        document.getElementById("nomeEq").value = "";
        document.getElementById("potenciaEq").value = "";
        document.getElementById("nomeEq").focus();

        atualizarTabela();
    }

    function removerEquipamento(index) {
        equipamentos.splice(index, 1);
        atualizarTabela();
    }

    function atualizarTabela() {
        let tbody = document.querySelector("#tabelaEquipamentos tbody");
        tbody.innerHTML = "";

        let somaCorrente12V = 0;

        equipamentos.forEach((eq, index) => {
            let tr = document.createElement("tr");
            tr.innerHTML = `
                <td><strong>${eq.nome}</strong></td>
                <td>${eq.potencia} W</td>
                <td>${eq.tensao} V</td>
                <td><span style="color: var(--accent); font-weight: bold;">${eq.corrente.toFixed(2)} A</span></td>
                <td>${eq.distancia} m</td>
                <td><span style="color: #60a5fa; font-weight: bold;">${eq.caboRecomendado}</span></td>
                <td><span style="color: var(--success); font-weight: bold;">${eq.disjuntorRecomendado}</span></td>
                <td><button class="btn-remover" onclick="removerEquipamento(${index})">Excluir</button></td>
            `;
            tbody.appendChild(tr);

            if (eq.tensao == 12) {
                somaCorrente12V += eq.corrente;
            }
        });

        document.getElementById("total12v").innerText = somaCorrente12V.toFixed(2) + " A";
        document.getElementById("totalItens").innerText = equipamentos.length;
    }

    function exportarRelatorio() {
        if (equipamentos.length === 0) {
            alert("Adicione pelo menos um equipamento antes de exportar o relatório.");
            return;
        }
        window.print();
    }
</script>
</body>
</html>
