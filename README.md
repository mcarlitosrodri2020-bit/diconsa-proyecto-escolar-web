<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Diconsa El Águila</title>

<style>
body {
    margin: 0;
    font-family: 'Courier New', monospace;
    background: black;
    color: #00ffcc;
    overflow-x: hidden;
}

/* FONDO MATRIX */
canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
}

/* HEADER */
header {
    text-align: center;
    padding: 30px 15px;
}

h1 {
    font-size: 32px;
    text-shadow: 0 0 10px #00ffcc;
}

p {
    font-size: 16px;
    color: white;
}

/* CONTENEDOR */
.container {
    width: 95%;
    max-width: 800px;
    margin: auto;
}

/* TARJETAS */
.card {
    background: rgba(0,0,0,0.75);
    border: 1px solid #00ffcc;
    border-radius: 15px;
    padding: 20px;
    margin: 25px 0;
    box-shadow: 0 0 15px #00ffcc;
    text-align: center;
}

/* TITULOS */
h2 {
    color: #00ffcc;
    margin-bottom: 10px;
}

/* IMAGEN */
.card img {
    width: 100%;
    max-width: 300px;
    border-radius: 10px;
    margin-top: 10px;
}

/* VIDEO RESPONSIVE */
.video {
    position: relative;
    width: 100%;
    padding-bottom: 56.25%;
    margin-top: 15px;
}

.video iframe {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    border-radius: 10px;
    box-shadow: 0 0 25px #00ffcc;
}

/* BOTONES */
.botones {
    margin-top: 15px;
}

.botones a {
    display: inline-block;
    margin: 10px;
    padding: 10px 20px;
    border: 1px solid #00ffcc;
    color: #00ffcc;
    text-decoration: none;
    border-radius: 20px;
    transition: 0.3s;
}

.botones a:hover {
    background: #00ffcc;
    color: black;
}

/* FOOTER */
footer {
    padding: 20px;
}

/* CONTENIDO FOOTER */
.footer-content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 10px;
}

/* LOGO */
.logo-footer {
    width: 60px;
    height: auto;
    filter: drop-shadow(0 0 8px #00ffcc);
}
</style>
</head>

<body>

<canvas id="matrix"></canvas>

<header>
    <h1>Diconsa El Águila</h1>
    <p>Acceso a productos básicos con tecnología social</p>
</header>

<div class="container">

<div class="card">
    <h2>¿Quiénes somos?</h2>
    <p>
        Diconsa es una empresa del gobierno mexicano que garantiza productos básicos 
        a bajo costo en comunidades rurales.
    </p>
</div>

<div class="card">
    <h2>+24,000 tiendas</h2>
    <img src="img/foto.jpg" alt="Tienda Diconsa">
</div>

<div class="card">
    <h2>Video</h2>

    <div class="video">
        <iframe 
            src="https://www.youtube.com/embed/LszXSx8UPRo?rel=0"
            title="Video Diconsa"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen>
        </iframe>
    </div>

</div>

<div class="card">
    <h2>Visítanos</h2>
    <div class="botones">
        <a href="https://www.diconsa.com.mx" target="_blank">Página Oficial</a>
        <a href="https://maps.app.goo.gl/r5hC7DCMNXEjav1V6" target="_blank">Ubicación</a>
    </div>
</div>

</div>

<footer>
    <div class="footer-content">
        <span>
            © 2026 Diconsa - Proyecto Escolar - Submódulo 2: Programación - 
            Integrantes: Alex Joaquín, Carlos Manuel, 6to semestre F. Matemático, 
            Tabatab N°1 El Águila
        </span>

        <img src="img/logo.jpg
    " alt="Logo" class="logo-footer">
    </div>
</footer>

<!-- EFECTO MATRIX -->
<script>
const canvas = document.getElementById("matrix");
const ctx = canvas.getContext("2d");

function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}

resizeCanvas();

const letras = "01DICONSA";
const fontSize = 14;
let columnas = canvas.width / fontSize;
let drops = Array(Math.floor(columnas)).fill(1);

function draw() {
    ctx.fillStyle = "rgba(0,0,0,0.05)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = "#00ffcc";
    ctx.font = fontSize + "px monospace";

    drops.forEach((y, i) => {
        const text = letras[Math.floor(Math.random() * letras.length)];
        ctx.fillText(text, i * fontSize, y * fontSize);

        if (y * fontSize > canvas.height && Math.random() > 0.975) {
            drops[i] = 0;
        }
        drops[i]++;
    });
}

setInterval(draw, 33);

window.addEventListener("resize", () => {
    resizeCanvas();
    columnas = canvas.width / fontSize;
    drops = Array(Math.floor(columnas)).fill(1);
});
</script>

</body>
</html>
