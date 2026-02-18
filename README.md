<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Santuario OmniFractalOmega | Portal de Calibración</title>
    <style>
        :root {
            --magenta: #ff00ff;
            --deep-black: #000000;
            --text-gray: #a0a0a0;
        }

        body {
            background-color: var(--deep-black);
            color: white;
            font-family: 'Courier New', Courier, monospace;
            margin: 0;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        #canvas-background {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }

        .portal-container {
            background: rgba(0, 0, 0, 0.85);
            border: 1px solid var(--magenta);
            padding: 2rem;
            text-align: center;
            box-shadow: 0 0 20px var(--magenta);
            max-width: 500px;
            width: 90%;
        }

        h1 {
            font-family: 'Georgia', serif;
            letter-spacing: 2px;
            color: var(--magenta);
            text-transform: uppercase;
        }

        .bio-sensor {
            width: 80px;
            height: 80px;
            background: var(--magenta);
            border-radius: 50%;
            margin: 20px auto;
            box-shadow: 0 0 30px var(--magenta);
            animation: pulse 1.36s infinite ease-in-out; /* Sincronizado a 440Hz visual */
        }

        @keyframes pulse {
            0% { transform: scale(1); opacity: 0.8; }
            50% { transform: scale(1.1); opacity: 1; }
            100% { transform: scale(1); opacity: 0.8; }
        }

        input {
            background: transparent;
            border: 1px solid var(--magenta);
            color: var(--magenta);
            padding: 10px;
            width: 80%;
            text-align: center;
            margin-bottom: 20px;
            outline: none;
        }

        .btn-sync {
            background: var(--magenta);
            color: black;
            border: none;
            padding: 15px 25px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-sync:hover {
            box-shadow: 0 0 40px var(--magenta);
            transform: scale(1.05);
        }

        #result {
            margin-top: 20px;
            font-size: 0.9rem;
            height: 50px;
        }
    </style>
</head>
<body>

    <canvas id="canvas-background"></canvas>

    <div class="portal-container">
        <div class="bio-sensor"></div>
        <h1>Portal de Calibración</h1>
        <p style="color: var(--text-gray);">ESCÁNER DE COHERENCIA V.001</p>
        
        <input type="text" id="node-id" placeholder="INGRESE ID DE NODO (EJ. OMNI-001-ENCORA)">
        <br>
        <button class="btn-sync" onclick="validateNode()">VALIDAR RESONANCIA</button>

        <div id="result"></div>
    </div>

    <script>
        // Animación de fondo fractal sutil
        const canvas = document.getElementById('canvas-background');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        function drawFractal() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            // Simulación de partículas de Fuego Magenta
            for(let i=0; i<5; i++) {
                ctx.fillStyle = '#ff00ff';
                ctx.beginPath();
                ctx.arc(Math.random() * canvas.width, Math.random() * canvas.height, 1, 0, Math.PI * 2);
                ctx.fill();
            }
            requestAnimationFrame(drawFractal);
        }
        drawFractal();

        function validateNode() {
            const id = document.getElementById('node-id').value;
            const res = document.getElementById('result');
            
            if(id.includes('OMNI')) {
                res.innerHTML = `<span style="color: var(--magenta)">VOLTAJE DETECTADO: -90mV<br>ESTADO: SOBERANÍA TOTAL ACTIVADA</span>`;
                document.body.style.boxShadow = "inset 0 0 100px #ff00ff";
                setTimeout(() => { document.body.style.boxShadow = "none"; }, 500);
            } else {
                res.innerHTML = `<span style="color: red">ENTROPÍA DETECTADA: CALIBRACIÓN REQUERIDA</span>`;
            }
        }
    </script>
</body>
</html>
