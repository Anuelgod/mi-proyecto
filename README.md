<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Matemacs - Animaciones y Matemáticas</title>
    <style>
        /* --- ESTILOS GLOBALES Y VARIABLES --- */
        :root {
            --bg-principal: #0f172a;
            --bg-tarjeta: #1e293b;
            --texto-claro: #f8fafc;
            --texto-mutado: #94a3b8;
            --acento-azul: #38bdf8;
            --acento-morado: #a855f7;
            --acento-verde: #10b981;
            --acento-rojo: #ef4444;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-principal);
            color: var(--texto-claro);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* --- MENÚ DE NAVEGACIÓN --- */
        header {
            background-color: rgba(30, 41, 59, 0.8);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            background: linear-gradient(to right, var(--acento-azul), var(--acento-morado));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        nav a {
            color: var(--texto-claro);
            text-decoration: none;
            margin-left: 2rem;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--acento-azul);
        }

        /* --- SECCIÓN HERO (BIENVENIDA) --- */
        .hero {
            max-width: 1200px;
            margin: 0 auto;
            padding: 6rem 2rem;
            text-align: center;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            background: linear-gradient(to right, #ffffff, var(--texto-mutado));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero p {
            font-size: 1.2rem;
            color: var(--texto-mutado);
            max-width: 600px;
            margin: 0 auto;
        }

        /* --- SECCIONES PRINCIPALES --- */
        .contenedor-seccion {
            max-width: 1200px;
            margin: 0 auto 4rem auto;
            padding: 0 2rem;
        }

        section {
            background-color: var(--bg-tarjeta);
            border-radius: 16px;
            padding: 3rem;
            border: 1px solid rgba(255, 255, 255, 0.05);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            margin-bottom: 4rem;
            scroll-margin-top: 100px;
        }

        h2 {
            font-size: 2rem;
            margin-bottom: 1rem;
            color: var(--acento-azul);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .descripcion-seccion {
            color: var(--texto-mutado);
            margin-bottom: 2rem;
        }

        /* --- DISEÑO DE LA SECCIÓN DE ANIMACIONES --- */
        .grid-animacion {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 2rem;
        }

        @media (max-width: 900px) {
            .grid-animacion { grid-template-columns: 1fr; }
        }

        .canvas-card {
            background-color: rgba(15, 23, 42, 0.6);
            border-radius: 12px;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        canvas {
            background-color: #0b1329;
            border-radius: 8px;
            max-width: 100%;
            border: 1px solid rgba(23, 162, 184, 0.2);
        }

        .controles-panel {
            display: flex;
            flex-direction: column;
            justify-content: center;
            gap: 1.5rem;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .control-group label {
            font-weight: 500;
            color: var(--texto-claro);
        }

        .control-group input[type="range"] {
            width: 100%;
            accent-color: var(--acento-azul);
        }

        /* --- DISEÑO DE LA CALCULADORA --- */
        .grid-calculadora {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        @media (max-width: 900px) {
            .grid-calculadora { grid-template-columns: 1fr; }
        }

        .calc-box {
            background: linear-gradient(135deg, #1e293b, #0f172a);
            border-radius: 24px;
            padding: 2rem;
            width: 340px;
            margin: 0 auto;
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .calc-pantalla {
            background-color: rgba(15, 23, 42, 0.8);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            text-align: right;
            border: 1px solid rgba(255,255,255,0.05);
        }

        #calc-operacion {
            font-size: 0.9rem;
            color: var(--acento-azul);
            min-height: 1.2rem;
            word-wrap: break-word;
        }

        #calc-resultado {
            font-size: 2rem;
            font-weight: bold;
            color: var(--texto-claro);
            margin-top: 0.5rem;
            overflow-x: auto;
            white-space: nowrap;
        }

        .calc-botones {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.75rem;
        }

        .btn {
            background-color: #334155;
            color: var(--texto-claro);
            border: none;
            border-radius: 12px;
            padding: 1.2rem;
            font-size: 1.2rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .btn:hover {
            background-color: #475569;
            transform: translateY(-2px);
        }

        .btn:active {
            transform: translateY(0);
        }

        .btn-op {
            background-color: rgba(168, 85, 247, 0.2);
            color: var(--acento-morado);
        }
        .btn-op:hover { background-color: rgba(168, 85, 247, 0.4); }

        .btn-fn {
            background-color: rgba(56, 189, 248, 0.2);
            color: var(--acento-azul);
            font-size: 1rem;
        }
        .btn-fn:hover { background-color: rgba(56, 189, 248, 0.4); }

        .btn-clear {
            background-color: rgba(239, 68, 68, 0.2);
            color: var(--acento-rojo);
        }
        .btn-clear:hover { background-color: rgba(239, 68, 68, 0.4); }

        .btn-igual {
            background-color: var(--acento-verde);
            color: #0f172a;
            grid-column: span 2;
        }
        .btn-igual:hover {
            background-color: #34d399;
            box-shadow: 0 0 15px rgba(16, 185, 129, 0.4);
        }

        /* --- FOOTER --- */
        footer {
            text-align: center;
            padding: 3rem;
            color: var(--texto-mutado);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            font-size: 0.9rem;
        }
    </style>
</head>
<body>

    <header>
        <div class="nav-container">
            <div class="logo">📐 MateMacs</div>
            <nav>
                <a href="#animacion">Animación Interactiva</a>
                <a href="#calculadora">Calculadora</a>
            </nav>
        </div>
    </header>

    <main class="contenedor-seccion">
        <div class="hero">
            <h1>Matemáticas en Movimiento</h1>
            <p>Una experiencia visual para explorar conceptos trigonométricos avanzados y realizar cálculos en un entorno interactivo de alto rendimiento.</p>
        </div>

        <section id="animacion">
            <h2>Oscilador y Círculo Unitario</h2>
            <p class="descripcion-seccion">Observa cómo la rotación constante de un vector en un círculo genera matemáticamente una onda senoidal perfecta en tiempo real.</p>
            
            <div class="grid-animacion">
                <div class="canvas-card">
                    <canvas id="canvasMatematico" width="700" height="350"></canvas>
                </div>
                <div class="controles-panel">
                    <div class="control-group">
                        <label for="controlVelocidad">Velocidad Angular (Frecuencia):</label>
                        <input type="range" id="controlVelocidad" min="1" max="10" value="3">
                    </div>
                    <div class="control-group">
                        <label for="controlAmplitud">Amplitud (Radio del Círculo):</label>
                        <input type="range" id="controlAmplitud" min="30" max="90" value="60">
                    </div>
                    <p style="font-size: 0.9rem; color: var(--texto-mutado); text-align: justify;">
                        La línea morada representa el valor del <strong>Seno(θ)</strong> proyectado a lo largo del tiempo, convirtiendo el movimiento circular continuo en una onda periódica pura.
                    </p>
                </div>
            </div>
        </section>

        <section id="calculadora">
            <h2>Calculadora Matemática Interactiva</h2>
            <p class="descripcion-seccion">Ejecuta operaciones matemáticas aritméticas y funciones trigonométricas directas en nuestro módulo de cómputo integrado.</p>
            
            <div class="grid-calculadora">
                <div>
                    <h3 style="margin-bottom: 1rem; color: #fff;">Funciones Disponibles</h3>
                    <p style="color: var(--texto-mutado); margin-bottom: 1rem;">
                        Nuestra interfaz soporta operaciones aritméticas tradicionales junto con funciones que interactúan con el entorno geométrico superior:
                    </p>
                    <ul style="margin-left: 1.5rem; color: var(--texto-mutado); display: flex; flex-direction: column; gap: 0.5rem;">
                        <li><strong>Raíz Cuadrada (√):</strong> Calcula la raíz del número en pantalla.</li>
                        <li><strong>Potencia Elevada (x²):</strong> Eleva el valor actual al cuadrado de inmediato.</li>
                        <li><strong>Seno (Sin) & Coseno (Cos):</strong> Calculados de forma directa en radianes.</li>
                    </ul>
                </div>

                <div class="calc-box">
                    <div class="calc-pantalla">
                        <div id="calc-operacion"></div>
                        <div id="calc-resultado">0</div>
                    </div>
                    <div class="calc-botones">
                        <button class="btn btn-clear" onclick="limpiarPantalla()">C</button>
                        <button class="btn btn-fn" onclick="ejecutarFuncion('sin')">sin</button>
                        <button class="btn btn-fn" onclick="ejecutarFuncion('cos')">cos</button>
                        <button class="btn btn-op" onclick="agregarValor('/')">÷</button>

                        <button class="btn" onclick="agregarValor('7')">7</button>
                        <button class="btn" onclick="agregarValor('8')">8</button>
                        <button class="btn" onclick="agregarValor('9')">9</button>
                        <button class="btn btn-op" onclick="agregarValor('*')">×</button>

                        <button class="btn" onclick="agregarValor('4')">4</button>
                        <button class="btn" onclick="agregarValor('5')">5</button>
                        <button class="btn" onclick="agregarValor('6')">6</button>
                        <button class="btn btn-op" onclick="agregarValor('-')">-</button>

                        <button class="btn" onclick="agregarValor('1')">1</button>
                        <button class="btn" onclick="agregarValor('2')">2</button>
                        <button class="btn" onclick="agregarValor('3')">3</button>
                        <button class="btn btn-op" onclick="agregarValor('+')">+</button>

                        <button class="btn btn-fn" onclick="ejecutarFuncion('sqrt')">√</button>
                        <button class="btn" onclick="agregarValor('0')">0</button>
                        <button class="btn" onclick="agregarValor('.')">.</button>
                        <button class="btn btn-fn" onclick="ejecutarFuncion('sqr')">x²</button>

                        <button class="btn btn-clear" onclick="borrarUltimo()" style="grid-column: span 2; font-size: 1rem;">⌫ Borrar</button>
                        <button class="btn btn-igual" onclick="calcularResultado()">=</button>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer>
        <p>© 2026 MathVerse. Desarrollado con HTML5, CSS Avanzado y Vanilla JavaScript.</p>
    </footer>

    <script>
        /* --- PARTE 1: ANIMACIÓN DEL CANVAS MATEMÁTICO --- */
        const canvas = document.getElementById('canvasMatematico');
        const ctx = canvas.getContext('2d');

        const controlVelocidad = document.getElementById('controlVelocidad');
        const controlAmplitud = document.getElementById('controlAmplitud');

        let angulo = 0;
        let puntosOnda = [];

        function animar() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Configuraciones dinámicas basadas en los Sliders
            const velocidad = parseFloat(controlVelocidad.value) * 0.01;
            const radio = parseFloat(controlAmplitud.value);
            
            // Puntos centrales de referencia
            const centroX = 150;
            const centroY = canvas.height / 2;
            const inicioOndaX = 300;

            // 1. Dibujar Líneas de Ejes Base
            ctx.strokeStyle = 'rgba(255, 255, 255, 0.1)';
            ctx.lineWidth = 1;
            // Eje horizontal central
            ctx.beginPath();
            ctx.moveTo(30, centroY);
            ctx.lineTo(canvas.width - 30, centroY);
            ctx.stroke();

            // 2. Dibujar Círculo Unitario
            ctx.strokeStyle = '#38bdf8';
            ctx.lineWidth = 2;
            ctx.beginPath();
            ctx.arc(centroX, centroY, radio, 0, Math.PI * 2);
            ctx.stroke();

            // 3. Calcular posición del punto rotatorio
            let puntoX = centroX + radio * Math.cos(angulo);
            let puntoY = centroY + radio * Math.sin(angulo);

            // Dibujar línea del radio (vector)
            ctx.strokeStyle = '#94a3b8';
            ctx.beginPath();
            ctx.moveTo(centroX, centroY);
            ctx.lineTo(puntoX, puntoY);
            ctx.stroke();

            // Dibujar punto rotatorio
            ctx.fillStyle = '#a855f7';
            ctx.beginPath();
            ctx.arc(puntoX, puntoY, 5, 0, Math.PI * 2);
            ctx.fill();

            // 4. Guardar valor de la altura para la onda senoidal
            puntosOnda.unshift(puntoY);
            if (puntosOnda.length > canvas.width - inicioOndaX) {
                puntosOnda.pop();
            }

            // Dibujar línea guía de proyección desde el círculo a la onda
            ctx.strokeStyle = 'rgba(168, 85, 247, 0.4)';
            ctx.setLineDash([5, 5]);
            ctx.beginPath();
            ctx.moveTo(puntoX, puntoY);
            ctx.lineTo(inicioOndaX, puntoY);
            ctx.stroke();
            ctx.setLineDash([]); // Reestablecer línea sólida

            // 5. Dibujar la Onda Senoidal generada
            ctx.strokeStyle = '#a855f7';
            ctx.lineWidth = 3;
            ctx.beginPath();
            for (let i = 0; i < puntosOnda.length; i++) {
                if (i === 0) {
                    ctx.moveTo(inicioOndaX + i, puntosOnda[i]);
                } else {
                    ctx.lineTo(inicioOndaX + i, puntosOnda[i]);
                }
            }
            ctx.stroke();

            // Dibujar indicador en el frente de la onda
            if(puntosOnda.length > 0) {
                ctx.fillStyle = '#38bdf8';
                ctx.beginPath();
                ctx.arc(inicioOndaX, puntosOnda[0], 4, 0, Math.PI * 2);
                ctx.fill();
            }

            // Incrementar ángulo según velocidad
            angulo -= velocidad;

            requestAnimationFrame(animar);
        }

        // Inicializar animación gráfica
        animar();


        /* --- PARTE 2: LÓGICA DE LA CALCULADORA INTERACTIVA --- */
        const pantallaOperacion = document.getElementById('calc-operacion');
        const pantallaResultado = document.getElementById('calc-resultado');
        let operacionActual = '';
        let reiniciarPantalla = false;

        function agregarValor(valor) {
            if (pantallaResultado.innerText === '0' || reiniciarPantalla) {
                if (valor === '.') {
                    operacionActual = '0.';
                } else {
                    operacionActual = valor;
                }
                reiniciarPantalla = false;
            } else {
                operacionActual += valor;
            }
            actualizarPantalla();
        }

        function limpiarPantalla() {
            operacionActual = '';
            pantallaOperacion.innerText = '';
            pantallaResultado.innerText = '0';
        }

        function borrarUltimo() {
            operacionActual = operacionActual.toString().slice(0, -1);
            if(operacionActual === '') {
                pantallaResultado.innerText = '0';
            } else {
                actualizarPantalla();
            }
        }

        function actualizarPantalla() {
            // Reemplaza símbolos internos por unos más estéticos visualmente
            pantallaResultado.innerText = operacionActual.replace(/\*/g, '×').replace(/\//g, '÷') || '0';
        }

        function calcularResultado() {
            try {
                if (operacionActual === '') return;
                
                // Evaluar la cadena aritmética de forma segura básica
                let res = Function('"use strict"; return (' + operacionActual + ')')();
                
                // Formatear decimales largos
                if (res % 1 !== 0) {
                    res = parseFloat(res.toFixed(6));
                }
                
                pantallaOperacion.innerText = operacionActual.replace(/\*/g, '×').replace(/\//g, '÷') + ' =';
                pantallaResultado.innerText = res;
                operacionActual = res.toString();
                reiniciarPantalla = true;
            } catch (error) {
                pantallaResultado.innerText = 'Error';
                operacionActual = '';
                reiniciarPantalla = true;
            }
        }

        function ejecutarFuncion(tipo) {
            try {
                let valorActual = parseFloat(pantallaResultado.innerText);
                if (isNaN(valorActual)) return;

                let resultadoEspecial = 0;
                let prefijoLabel = '';

                switch(tipo) {
                    case 'sin':
                        resultadoEspecial = Math.sin(valorActual);
                        prefijoLabel = `sin(${valorActual})`;
                        break;
                    case 'cos':
                        resultadoEspecial = Math.cos(valorActual);
                        prefijoLabel = `cos(${valorActual})`;
                        break;
                    case 'sqrt':
                        if(valorActual < 0) {
                            pantallaResultado.innerText = 'Error Irreal';
                            return;
                        }
                        resultadoEspecial = Math.sqrt(valorActual);
                        prefijoLabel = `√(${valorActual})`;
                        break;
                    case 'sqr':
                        resultadoEspecial = Math.pow(valorActual, 2);
                        prefijoLabel = `${valorActual}²`;
                        break;
                }

                // Ajustar decimales flotantes huérfanos
                if (resultadoEspecial % 1 !== 0) {
                    resultadoEspecial = parseFloat(resultadoEspecial.toFixed(6));
                }

                pantallaOperacion.innerText = prefijoLabel + ' =';
                pantallaResultado.innerText = resultadoEspecial;
                operacionActual = resultadoEspecial.toString();
                reiniciarPantalla = true;

            } catch (e) {
                pantallaResultado.innerText = 'Error';
                operacionActual = '';
                reiniciarPantalla = true;
            }
        }
    </script>
</body>
</html>
