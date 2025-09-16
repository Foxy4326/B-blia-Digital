<!DOCTYPE html>
<html lang="pt-BR" id="html">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="mobile-web-app-capable" content="yes">
    <title>📖 Minha Bíblia Pro</title>
    <link rel="manifest" href="data:application/json;base64,eyJuYW1lIjoiTWluaGEgQsOtYmxpYSBQcm8iLCJzaG9ydF9uYW1lIjoiQsOtYmxpYSBQcm8iLCJzdGFydF91cmwiOiIvIiwiZGlzcGxheSI6InN0YW5kYWxvbmUiLCJiYWNrZ3JvdW5kX2NvbG9yIjoiIzJjM2U1MCIsInRoZW1lX2NvbG9yIjoiIzJjM2U1MCIsImRlc2NyaXB0aW9uIjoiTGVpYSBlIG91dmEgYSDCqWJsaWEgU2FncmFkYSBjb20gZmF2b3JpdG9zIGUgbW9kbyBlc2N1cm8uIiwiaWNvbnMiOlt7InNyYyI6Ii9pY29ucy9pY29uLTE5Mi5wbmciLCJzaXplcyI6IjE5MngxOTIiLCJ0eXBlIjoiaW1hZ2UvcG5nIn0seyJzcmMiOiIvaWNvbnMvaWNvbi01MTIucG5nIiwic2l6ZXMiOiI1MTJ4NTEyIiwidHlwZSI6ImltYWdlL3BuZyJ9XX0=">
    <style>
        :root {
            --bg: #ffffff;
            --text: #333333;
            --bg-sec: #f8f9fa;
            --header-bg: #2c3e50;
            --header-text: #ffffff;
            --btn-primary: #2980b9;
            --btn-success: #27ae60;
            --btn-warning: #f39c12;
            --btn-danger: #e74c3c;
            --border: #ddd;
            --shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        [data-theme="dark"] {
            --bg: #121212;
            --text: #e0e0e0;
            --bg-sec: #1e1e1e;
            --header-bg: #1a1a1a;
            --header-text: #ffffff;
            --border: #333;
            --shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--bg);
            color: var(--text);
            line-height: 1.6;
            transition: background 0.3s, color 0.3s;
        }

        .container {
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background: var(--bg-sec);
            border-radius: 16px;
            box-shadow: var(--shadow);
            transition: background 0.3s;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-bottom: 20px;
            border-bottom: 2px solid var(--border);
            margin-bottom: 25px;
        }

        header .header-left h1 {
            color: var(--header-text);
            font-size: 1.8rem;
        }

        header .header-right {
            display: flex;
            gap: 10px;
        }

        header button {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--header-text);
            padding: 5px 10px;
            border-radius: 8px;
            transition: background 0.3s;
        }

        header button:hover {
            background: rgba(255,255,255,0.1);
        }

        .controls {
            display: flex;
            gap: 12px;
            margin-bottom: 30px;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
        }

        .controls select, .controls button {
            padding: 12px;
            font-size: 16px;
            border: 2px solid var(--border);
            border-radius: 8px;
            background: var(--bg);
            color: var(--text);
            min-width: 180px;
            transition: all 0.3s;
        }

        .controls button {
            background: var(--btn-primary);
            color: white;
        }

        .controls button:hover {
            background: #3498db;
        }

        .controls button:disabled,
        .controls select:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .resultado {
            background: var(--bg);
            padding: 30px;
            border-radius: 12px;
            min-height: 300px;
            font-size: 18px;
            line-height: 1.8;
            text-align: justify;
            border: 1px solid var(--border);
        }

        .resultado h2 {
            color: var(--text);
            margin-bottom: 20px;
            text-align: center;
        }

        .resultado .versiculo {
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px dashed var(--border);
            position: relative;
        }

        .resultado .versiculo:last-child {
            border-bottom: none;
        }

        .resultado .numero {
            font-weight: bold;
            color: #e67e22;
            margin-right: 8px;
        }

        .resultado .favoritar {
            position: absolute;
            top: 5px;
            right: 5px;
            background: none;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            color: #ddd;
            transition: color 0.3s;
        }

        .resultado .favoritar:hover {
            color: gold;
        }

        .resultado .error {
            color: var(--btn-danger);
            font-weight: bold;
            text-align: center;
        }

        .voz-controls {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: center;
            gap: 12px;
            margin-top: 20px;
            padding: 15px;
            background: var(--bg);
            border-radius: 10px;
            border: 1px solid var(--border);
        }

        .btn-voz {
            padding: 10px 16px;
            font-size: 14px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s;
        }

        #btn-ler { background: var(--btn-success); color: white; }
        #btn-ler-versiculo { background: #8e44ad; color: white; }
        #btn-pausar { background: var(--btn-warning); color: white; }
        #btn-parar { background: var(--btn-danger); color: white; }

        .btn-voz:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .btn-voz:hover:not(:disabled) {
            filter: brightness(1.1);
            transform: translateY(-2px);
        }

        #voz-controls label {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
            color: var(--text);
        }

        #voz-controls input[type="range"] {
            width: 80px;
        }

        /* MODAL FAVORITOS */
        .modal {
            display: none;
            position: fixed;
            z-index: 100;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            overflow: auto;
        }

        .modal-content {
            background: var(--bg);
            margin: 10% auto;
            padding: 30px;
            width: 90%;
            max-width: 600px;
            border-radius: 12px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
            position: relative;
        }

        .close {
            position: absolute;
            right: 20px;
            top: 15px;
            font-size: 2rem;
            cursor: pointer;
            color: var(--text);
        }

        #lista-favoritos {
            margin-top: 20px;
        }

        #lista-favoritos .favorito-item {
            padding: 15px;
            background: var(--bg-sec);
            margin-bottom: 10px;
            border-radius: 8px;
            position: relative;
        }

        #lista-favoritos .favorito-item button.remover {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--btn-danger);
            color: white;
            border: none;
            border-radius: 4px;
            padding: 5px 10px;
            cursor: pointer;
        }

        footer {
            margin-top: 40px;
            text-align: center;
            color: #95a5a6;
            font-size: 14px;
        }

        footer a {
            color: #3498db;
            text-decoration: none;
        }

        footer a:hover {
            text-decoration: underline;
        }

        @media (max-width: 600px) {
            .controls {
                flex-direction: column;
                align-items: stretch;
            }

            .controls select, .controls button {
                width: 100%;
            }

            .header-right {
                gap: 5px;
            }

            header button {
                font-size: 1.3rem;
                padding: 5px;
            }
        }
    </style>
</head>
<body id="body">
    <div class="container" id="container">
        <header>
            <div class="header-left">
                <h1>📖 Minha Bíblia Pro</h1>
            </div>
            <div class="header-right">
                <button id="btn-toggle-tema" title="Alternar tema">🌙</button>
                <button id="btn-favoritos" title="Meus Favoritos">⭐</button>
            </div>
        </header>

        <div class="controls">
            <select id="livro">
                <option value="">Selecione um livro</option>
            </select>
            <select id="capitulo" disabled>
                <option value="">Selecione um capítulo</option>
            </select>
            <button id="buscarBtn" disabled>Carregar Capítulo</button>
        </div>

        <div id="resultado" class="resultado">
            <!-- Resultado aparecerá aqui -->
        </div>

        <!-- CONTROLES DE VOZ -->
        <div id="voz-controls" class="voz-controls" style="display: none;">
            <button id="btn-ler" class="btn-voz">▶️ Ouvir Tudo</button>
            <button id="btn-ler-versiculo" class="btn-voz">⏭️ Ler por Versículo</button>
            <button id="btn-pausar" class="btn-voz" disabled>⏸️ Pausar</button>
            <button id="btn-parar" class="btn-voz" disabled>⏹️ Parar</button>
            <label>
                Velocidade:
                <input type="range" id="velocidade" min="0.5" max="2" step="0.1" value="1">
                <span id="valor-velocidade">1x</span>
            </label>
        </div>

        <!-- MODAL DE FAVORITOS -->
        <div id="modal-favoritos" class="modal">
            <div class="modal-content">
                <span class="close">&times;</span>
                <h2>Meus Favoritos</h2>
                <div id="lista-favoritos">
                    <p>Nenhum favorito salvo.</p>
                </div>
            </div>
        </div>

        <footer>
            <p>© 2025 Minha Bíblia Pro | Dados por <a href="https://bible-api.com" target="_blank">Bible API</a></p>
        </footer>
    </div>

    <script>
        // ========== CONFIGURAÇÕES GLOBAIS ==========
        let utterance = null;
        let isPaused = false;
        let leituraPorVersiculo = false;
        let versiculosParaLer = [];
        let indiceVersiculoAtual = 0;
        let synth = window.speechSynthesis;

        // Elementos
        const selectLivro = document.getElementById('livro');
        const selectCapitulo = document.getElementById('capitulo');
        const btnBuscar = document.getElementById('buscarBtn');
        const resultadoDiv = document.getElementById('resultado');
        const vozControls = document.getElementById('voz-controls');
        const btnLer = document.getElementById('btn-ler');
        const btnLerVersiculo = document.getElementById('btn-ler-versiculo');
        const btnPausar = document.getElementById('btn-pausar');
        const btnParar = document.getElementById('btn-parar');
        const velocidadeInput = document.getElementById('velocidade');
        const valorVelocidade = document.getElementById('valor-velocidade');
        const btnToggleTema = document.getElementById('btn-toggle-tema');
        const btnFavoritos = document.getElementById('btn-favoritos');
        const modalFavoritos = document.getElementById('modal-favoritos');
        const listaFavoritos = document.getElementById('lista-favoritos');
        const spanClose = document.querySelector('.close');

        // Lista de livros
        const livrosBiblia = [
            { nome: "Gênesis", cap: 50 }, { nome: "Êxodo", cap: 40 }, { nome: "Levítico", cap: 27 },
            { nome: "Números", cap: 36 }, { nome: "Deuteronômio", cap: 34 }, { nome: "Josué", cap: 24 },
            { nome: "Juízes", cap: 21 }, { nome: "Rute", cap: 4 }, { nome: "1 Samuel", cap: 31 },
            { nome: "2 Samuel", cap: 24 }, { nome: "1 Reis", cap: 22 }, { nome: "2 Reis", cap: 25 },
            { nome: "1 Crônicas", cap: 29 }, { nome: "2 Crônicas", cap: 36 }, { nome: "Esdras", cap: 10 },
            { nome: "Neemias", cap: 13 }, { nome: "Ester", cap: 10 }, { nome: "Jó", cap: 42 },
            { nome: "Salmos", cap: 150 }, { nome: "Provérbios", cap: 31 }, { nome: "Eclesiastes", cap: 12 },
            { nome: "Cantares", cap: 8 }, { nome: "Isaías", cap: 66 }, { nome: "Jeremias", cap: 52 },
            { nome: "Lamentações", cap: 5 }, { nome: "Ezequiel", cap: 48 }, { nome: "Daniel", cap: 12 },
            { nome: "Oséias", cap: 14 }, { nome: "Joel", cap: 3 }, { nome: "Amós", cap: 9 },
            { nome: "Obadias", cap: 1 }, { nome: "Jonas", cap: 4 }, { nome: "Miquéias", cap: 7 },
            { nome: "Naum", cap: 3 }, { nome: "Habacuque", cap: 3 }, { nome: "Sofonias", cap: 3 },
            { nome: "Ageu", cap: 2 }, { nome: "Zacarias", cap: 14 }, { nome: "Malaquias", cap: 4 },
            { nome: "Mateus", cap: 28 }, { nome: "Marcos", cap: 16 }, { nome: "Lucas", cap: 24 },
            { nome: "João", cap: 21 }, { nome: "Atos", cap: 28 }, { nome: "Romanos", cap: 16 },
            { nome: "1 Coríntios", cap: 16 }, { nome: "2 Coríntios", cap: 13 }, { nome: "Gálatas", cap: 6 },
            { nome: "Efésios", cap: 6 }, { nome: "Filipenses", cap: 4 }, { nome: "Colossenses", cap: 4 },
            { nome: "1 Tessalonicenses", cap: 5 }, { nome: "2 Tessalonicenses", cap: 3 },
            { nome: "1 Timóteo", cap: 6 }, { nome: "2 Timóteo", cap: 4 }, { nome: "Tito", cap: 3 },
            { nome: "Filemom", cap: 1 }, { nome: "Hebreus", cap: 13 }, { nome: "Tiago", cap: 5 },
            { nome: "1 Pedro", cap: 5 }, { nome: "2 Pedro", cap: 3 }, { nome: "1 João", cap: 5 },
            { nome: "2 João", cap: 1 }, { nome: "3 João", cap: 1 }, { nome: "Judas", cap: 1 },
            { nome: "Apocalipse", cap: 22 }
        ];

        // ========== INICIALIZAÇÃO ==========
        function init() {
            carregarLivros();
            carregarTema();
            carregarFavoritos();
            registrarServiceWorker();
            setupEventos();
        }

        // ========== EVENTOS ==========
        function setupEventos() {
            // Livro selecionado
            selectLivro.addEventListener('change', function() {
                const livroSelecionado = livrosBiblia.find(l => l.nome === this.value);
                selectCapitulo.innerHTML = '<option value="">Selecione um capítulo</option>';
                selectCapitulo.disabled = !livroSelecionado;

                if (livroSelecionado) {
                    for (let i = 1; i <= livroSelecionado.cap; i++) {
                        const option = document.createElement('option');
                        option.value = i;
                        option.textContent = `Capítulo ${i}`;
                        selectCapitulo.appendChild(option);
                    }
                }
                btnBuscar.disabled = true;
            });

            // Capítulo selecionado
            selectCapitulo.addEventListener('change', function() {
                btnBuscar.disabled = !this.value;
            });

            // Buscar capítulo
            btnBuscar.addEventListener('click', buscarCapitulo);

            // Velocidade de voz
            velocidadeInput.addEventListener('input', function() {
                valorVelocidade.textContent = this.value + 'x';
                if (utterance) utterance.rate = parseFloat(this.value);
            });

            // Botões de voz
            btnLer.addEventListener('click', () => lerTextoCompleto());
            btnLerVersiculo.addEventListener('click', () => lerPorVersiculo());
            btnPausar.addEventListener('click', pausarOuRetomar);
            btnParar.addEventListener('click', pararLeitura);

            // Tema
            btnToggleTema.addEventListener('click', alternarTema);

            // Favoritos
            btnFavoritos.addEventListener('click', mostrarFavoritos);
            spanClose.addEventListener('click', () => modalFavoritos.style.display = 'none');
            window.addEventListener('click', (e) => {
                if (e.target == modalFavoritos) modalFavoritos.style.display = 'none';
            });
        }

        // ========== BUSCA DE CAPÍTULO ==========
        async function buscarCapitulo() {
            const livro = selectLivro.value;
            const capitulo = selectCapitulo.value;
            const referencia = `${livro} ${capitulo}`;

            resultadoDiv.innerHTML = '<p>Carregando...</p>';
            vozControls.style.display = 'none';

            try {
                const response = await fetch(`https://bible-api.com/${encodeURIComponent(referencia)}?translation=almeida`);
                if (!response.ok) throw new Error('Capítulo não encontrado.');

                const data = await response.json();
                exibirCapitulo(data);
                toggleVozControls();
            } catch (error) {
                resultadoDiv.innerHTML = `<p class="error">Erro: ${error.message}</p>`;
            }
        }

        function exibirCapitulo(data) {
            let texto = `<h2>${data.reference}</h2><hr>`;
            data.verses.forEach((verso, index) => {
                texto += `
                    <div class="versiculo" data-index="${index}">
                        <span class="numero">${verso.chapter}:${verso.verse}</span>
                        ${verso.text}
                        <button class="favoritar" data-ref="${data.reference}" data-verse="${verso.verse}" data-text="${encodeURIComponent(verso.text)}" title="Adicionar aos favoritos">☆</button>
                    </div>
                `;
            });
            resultadoDiv.innerHTML = texto;

            // Adiciona evento aos botões de favorito
            document.querySelectorAll('.favoritar').forEach(btn => {
                btn.addEventListener('click', function() {
                    const ref = this.getAttribute('data-ref');
                    const verse = this.getAttribute('data-verse');
                    const text = decodeURIComponent(this.getAttribute('data-text'));
                    adicionarFavorito(`${ref}:${verse}`, text);
                    this.textContent = '★';
                    this.style.color = 'gold';
                    this.title = 'Remover dos favoritos';
                    this.removeEventListener('click', arguments.callee);
                });
            });
        }

        // ========== VOZ ==========
        function lerTextoCompleto() {
            pararLeitura();
            leituraPorVersiculo = false;
            const texto = limparTexto(resultadoDiv.innerText);
            if (!texto) return alert('Nenhum texto para ler.');
            falarTexto(texto);
        }

        function lerPorVersiculo() {
            pararLeitura();
            leituraPorVersiculo = true;
            versiculosParaLer = Array.from(document.querySelectorAll('.versiculo')).map(el => el.innerText);
            indiceVersiculoAtual = 0;
            lerProximoVersiculo();
        }

        function lerProximoVersiculo() {
            if (indiceVersiculoAtual >= versiculosParaLer.length) {
                resetarControlesVoz();
                return;
            }

            const texto = limparTexto(versiculosParaLer[indiceVersiculoAtual]);
            utterance = new SpeechSynthesisUtterance(texto);
            utterance.lang = 'pt-BR';
            utterance.rate = parseFloat(velocidadeInput.value);

            utterance.onend = () => {
                indiceVersiculoAtual++;
                if (indiceVersiculoAtual < versiculosParaLer.length) {
                    setTimeout(lerProximoVersiculo, 500); // pequena pausa
                } else {
                    resetarControlesVoz();
                }
            };

            utterance.onerror = resetarControlesVoz;

            btnLer.disabled = true;
            btnLerVersiculo.disabled = true;
            btnPausar.disabled = false;
            btnParar.disabled = false;

            synth.speak(utterance);
        }

        function falarTexto(texto) {
            synth.cancel();
            utterance = new SpeechSynthesisUtterance(texto);
            utterance.lang = 'pt-BR';
            utterance.rate = parseFloat(velocidadeInput.value);

            utterance.onend = resetarControlesVoz;
            utterance.onerror = resetarControlesVoz;

            btnLer.disabled = true;
            btnLerVersiculo.disabled = true;
            btnPausar.disabled = false;
            btnParar.disabled = false;

            synth.speak(utterance);
        }

        function pausarOuRetomar() {
            if (isPaused) {
                synth.resume();
                isPaused = false;
                btnPausar.textContent = '⏸️ Pausar';
            } else {
                synth.pause();
                isPaused = true;
                btnPausar.textContent = '▶️ Retomar';
            }
        }

        function pararLeitura() {
            synth.cancel();
            resetarControlesVoz();
        }

        function resetarControlesVoz() {
            btnLer.disabled = false;
            btnLerVersiculo.disabled = false;
            btnPausar.disabled = true;
            btnParar.disabled = true;
            btnPausar.textContent = '⏸️ Pausar';
            isPaused = false;
            leituraPorVersiculo = false;
        }

        function limparTexto(texto) {
            return texto.replace(/(▶️ Ouvir Tudo|⏭️ Ler por Versículo|⏸️ Pausar|⏹️ Parar|Velocidade:.*?2x)/g, '').trim();
        }

        function toggleVozControls() {
            const texto = resultadoDiv.innerText;
            if (texto && !texto.includes('Carregando...') && !texto.includes('Erro:')) {
                vozControls.style.display = 'flex';
            } else {
                vozControls.style.display = 'none';
                pararLeitura();
            }
        }

        // ========== FAVORITOS ==========
        function adicionarFavorito(referencia, texto) {
            let favoritos = JSON.parse(localStorage.getItem('favoritos') || '[]');
            if (!favoritos.some(f => f.ref === referencia)) {
                favoritos.push({ ref: referencia, text: texto });
                localStorage.setItem('favoritos', JSON.stringify(favoritos));
                alert('Adicionado aos favoritos!');
            }
            carregarFavoritos();
        }

        function carregarFavoritos() {
            const favoritos = JSON.parse(localStorage.getItem('favoritos') || '[]');
            listaFavoritos.innerHTML = favoritos.length === 0 ?
                '<p>Nenhum favorito salvo.</p>' :
                favoritos.map((fav, index) => `
                    <div class="favorito-item">
                        <strong>${fav.ref}</strong>
                        <p>${fav.text}</p>
                        <button class="remover" data-index="${index}">🗑️ Remover</button>
                    </div>
                `).join('');

            document.querySelectorAll('.remover').forEach(btn => {
                btn.addEventListener('click', function() {
                    removerFavorito(this.getAttribute('data-index'));
                });
            });
        }

        function removerFavorito(index) {
            let favoritos = JSON.parse(localStorage.getItem('favoritos') || '[]');
            favoritos.splice(index, 1);
            localStorage.setItem('favoritos', JSON.stringify(favoritos));
            carregarFavoritos();
        }

        function mostrarFavoritos() {
            carregarFavoritos();
            modalFavoritos.style.display = 'block';
        }

        // ========== MODO ESCURO ==========
        function alternarTema() {
            const html = document.getElementById('html');
            const temaAtual = html.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
            html.setAttribute('data-theme', temaAtual);
            localStorage.setItem('tema', temaAtual);
            btnToggleTema.textContent = temaAtual === 'dark' ? '☀️' : '🌙';
        }

        function carregarTema() {
            const temaSalvo = localStorage.getItem('tema') || 'light';
            document.getElementById('html').setAttribute('data-theme', temaSalvo);
            btnToggleTema.textContent = temaSalvo === 'dark' ? '☀️' : '🌙';
        }

        // ========== PWA - SERVICE WORKER ==========
        function registrarServiceWorker() {
            if ('serviceWorker' in navigator) {
                const sw = `
                    const CACHE_NAME = 'biblia-pro-v1';
                    const urlsToCache = [
                        '/',
                        '/index.html'
                    ];

                    self.addEventListener('install', event => {
                        event.waitUntil(
                            caches.open(CACHE_NAME)
                                .then(cache => cache.addAll(urlsToCache))
                        );
                    });

                    self.addEventListener('fetch', event => {
                        event.respondWith(
                            caches.match(event.request)
                                .then(response => response || fetch(event.request))
                        );
                    });
                `;

                const blob = new Blob([sw], {type: 'application/javascript'});
                const swURL = URL.createObjectURL(blob);

                window.addEventListener('load', () => {
                    navigator.serviceWorker.register(swURL)
                        .then(reg => console.log('SW registrado com sucesso:', reg))
                        .catch(err => console.log('Falha ao registrar SW:', err));
                });
            }
        }

        // ========== UTILS ==========
        function carregarLivros() {
            livrosBiblia.forEach(livro => {
                const option = document.createElement('option');
                option.value = livro.nome;
                option.textContent = livro.nome;
                selectLivro.appendChild(option);
            });
        }

        // Inicializa tudo
        init();
    </script>
</body>
</html>
