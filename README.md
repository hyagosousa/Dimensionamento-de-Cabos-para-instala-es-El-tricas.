<!DOCTYPE html>    body {
        font-family: 'Inter', system-ui, -apple-system, sans-serif;
        background-color: var(--bg-dark);
        color: var(--text-main);
        margin: 0;
        padding: 20px;
    }

    .container {
        max-width: 1050px;
        margin: 0 auto;
        background: var(--card-bg);
        padding: 35px;
        border-radius: 16px;
        box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.4), 0 8px 10px -6px rgba(0, 0, 0, 0.4);
        border: 1px solid var(--border);
    }

    .header {
        text-align: center;
        border-bottom: 2px solid var(--border);
        padding-bottom: 20px;
        margin-bottom: 30px;
    }

    .header h1 {
        margin: 0;
        font-size: 1.8rem;
        color: var(--text-main);
        letter-spacing: -0.5px;
    }

    .header h1 span {
        color: var(--accent);
    }

    .header p {
        color: var(--text-muted);
        margin-top: 8px;
        font-size: 0.95rem;
    }

    .form-grid {
        display: grid;
        grid-template-columns: 2fr 1fr 1fr 1fr auto;
        gap: 12px;
        margin-bottom: 25px;
        align-items: end;
    }

    @media(max-width: 850px) {
        .form-grid {
            grid-template-columns: 1fr;
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
        padding: 11px 14px;
        background-color: #0b0f19;
        border: 1px solid var(--border);
        color: var(--text-main);
        border-radius: 8px;
        box-sizing: border-box;
        font-size: 0.95rem;
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
        padding: 11px 20px;
        border-radius: 8px;
        cursor: pointer;
        font-weight: 700;
        font-size: 0.95rem;
        transition: background 0.2s, transform 0.1s;
    }

    button:hover {
        background-color: var(--accent-hover);
    }

    button:active {
        transform: scale(0.98);
    }

    .btn-remover {
        background-color: rgba(239, 68, 68, 0.15);
        color: var(--danger);
        border: 1px solid rgba(239, 68, 68, 0.3);
        padding: 8px 12px;
        font-size: 0.85rem;
    }

    .btn-remover:hover {
        background-color: var(--danger);
        color: white;
    }

    .acoes-topo {
        display: flex;
        justify-content: flex-end;
        margin-bottom: 15px;
    }

    .btn-exportar {
        background-color: #3b82f6;
        color: white;
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .btn-exportar:hover {
        background-color: #2563eb;
    }

    .table-responsive {
        width: 100%;
        overflow-x: auto;
        -webkit-overflow-scrolling: touch;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 15px;
        white-space: nowrap;
    }

    th, td {
        border: 1px solid var(--border);
        padding: 14px;
        text-align: center;
        font-size: 0.9rem;
    }

    th {
        background-color: #111827;
        color: var(--text-muted);
        text-transform: uppercase;
        font-size: 0.75rem;
        letter-spacing: 0.8px;
    }

    tr:nth-child(even) {
        background-color: rgba(255, 255, 255, 0.01);
    }

    .resumo-container {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 20px;
        margin-top: 35px;
    }

    .card-resumo {
        background: #111827;
        padding: 20px;
        border-radius: 10px;
        border: 1px solid var(--border);
        border-left: 4px solid var(--accent);
    }

    .card-resumo h3 {
        margin: 0 0 8px 0;
        font-size: 0.8rem;
        color: var(--text-muted);
        text-transform: uppercase;
        letter-spacing: 0.5px;
    }

    .card-resumo p {
        margin: 0;
        font-size: 1.5rem;
        font-weight: bold;
        color: var(--text-main);
    }

    .footer-suporte {
        text-align: center;
        margin-top: 30px;
        padding-top: 20px;
        border-top: 1px solid var(--border);
        font-size: 0.85rem;
        color: var(--text-muted);
    }

    .footer-suporte a {
        color: var(--accent);
        text-decoration: none;
        font-weight: bold;
    }

    @media print {
        body {
            background: white;
            color: black;
            padding: 0;
        }
        .container {
            box-shadow: none;
            border: none;
            background: white;
            width: 100%;
            max-width: 100%;
            padding: 0;
        }
        .form-grid, .acoes-topo, .btn-remover, th:last-child, td:last-child {
            display: none !important;
        }
        .header h1 { color: #000; }
        .header h1 span { color: #059669; }
        .card-resumo {
            background: #f8fafc;
            border: 1px solid #cbd5e1;
            border-left: 4px solid #059669;
        }
        .card-resumo h3 { color: #475569; }
        .card-resumo p { color: #0f172a; }
        th { background-color: #e2e8f0; color: #334155; }
        th, td { border-color: #cbd5e1; color: #1e293b; }
        .footer-suporte { color: #475569; border-top: 1px solid #cbd5e1; }
        .footer-suporte a { color: #059669; }
    }
</style>
