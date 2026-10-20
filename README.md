# GHSTSYZ.github.io
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para ti 🎀</title>
<style>
  * { box-sizing: border-box; }
  html, body { margin: 0; padding: 0; }

  /* ===== VARIABLES DE COLOR ===== */
  :root {
    --fondo-a: #fff7f3;
    --fondo-b: #ffeef4;
    --fondo-c: #fdf3e7;
    --glow-a: #ffe4ec;
    --glow-b: #ffe9d6;

    --tarjeta-bg: rgba(255, 255, 255, 0.72);
    --tarjeta-borde: #ffd6e2;
    --tarjeta-sombra: rgba(214, 140, 160, 0.18);

    --texto: #5a3b45;
    --texto-suave: #7a5560;
    --texto-carta: #4a323a;
    --texto-posdata: #6b4a55;

    --rosa: #f18aa8;
    --rosa-borde: #ffc2d4;
    --rosa-fuerte: #ff8fab;
    --rosa-palido: #ffe4ec;

    --kitty-cabeza: #fff;
    --kitty-linea: #5a3b45;
    --kitty-mono: #ff8fab;
    --kitty-nariz: #ffb84d;

    --corazon-fondo: #ffc2d4;
    --cursor-color: #f18aa8;
    --firma-color: #f18aa8;
    --firma-texto: #a56d7c;
  }

  /* ===== MODO NOCTURNO ===== */
  body.noche {
    --fondo-a: #1a1428;
    --fondo-b: #241a33;
    --fondo-c: #2b1f3a;
    --glow-a: #3a2a55;
    --glow-b: #4a2e4f;

    --tarjeta-bg: rgba(36, 26, 51, 0.78);
    --tarjeta-borde: #4a3560;
    --tarjeta-sombra: rgba(0, 0, 0, 0.45);

    --texto: #f0e4ee;
    --texto-suave: #c9b3d0;
    --texto-carta: #ece0ef;
    --texto-posdata: #d8c4de;

    --rosa: #ff9fc0;
    --rosa-borde: #7a4f75;
    --rosa-fuerte: #ff8fab;
    --rosa-palido: #3a2a55;

    --kitty-cabeza: #fdf6ff;
    --kitty-linea: #2a1f3a;
    --kitty-mono: #ff8fab;
    --kitty-nariz: #ffb84d;

    --corazon-fondo: #b06a9a;
    --cursor-color: #ff9fc0;
    --firma-color: #ff9fc0;
    --firma-texto: #d8a8c8;
  }

  body {
    min-height: 100vh;
    background:
      radial-gradient(circle at 15% 20%, var(--glow-a) 0%, transparent 45%),
      radial-gradient(circle at 85% 80%, var(--glow-b) 0%, transparent 50%),
      linear-gradient(135deg, var(--fondo-a) 0%, var(--fondo-b) 50%, var(--fondo-c) 100%);
    color: var(--texto);
    font-family: 'Georgia', 'Times New Roman', serif;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding: 48px 18px;
    overflow-x: hidden;
    position: relative;
    transition: background 0.8s ease, color 0.8s ease;
  }

  /* Corazones flotando de fondo */
  .corazon-fondo {
    position: fixed;
    color: var(--corazon-fondo);
    opacity: 0.35;
    pointer-events: none;
    animation: flotar 14s linear infinite;
    font-size: 1.2rem;
    z-index: 0;
    transition: color 0.8s ease;
  }
  @keyframes flotar {
    0%   { transform: translateY(110vh) rotate(0deg); opacity: 0; }
    10%  { opacity: 0.35; }
    90%  { opacity: 0.35; }
    100% { transform: translateY(-10vh) rotate(30deg); opacity: 0; }
  }

  /* Tarjeta principal */
  .tarjeta {
    position: relative;
    z-index: 2;
    background: var(--tarjeta-bg);
    backdrop-filter: blur(6px);
    border: 1px solid var(--tarjeta-borde);
    border-radius: 22px;
    box-shadow: 0 18px 50px var(--tarjeta-sombra);
    padding: 42px 38px 50px;
    max-width: 640px;
    width: 100%;
    transition: background 0.8s ease, border-color 0.8s ease, box-shadow 0.8s ease;
  }

  /* Hello Kitty esquina */
  .kitty {
    position: absolute;
    top: -26px;
    right: 22px;
    width: 68px;
    height: 68px;
    filter: drop-shadow(0 4px 8px rgba(214,140,160,0.25));
    animation: vaiven 4s ease-in-out infinite;
    cursor: pointer;
    transition: transform 0.2s;
    z-index: 5;
  }
  .kitty:hover { transform: scale(1.1) rotate(0deg); }
  .kitty:active { transform: scale(0.95); }
  @keyframes vaiven {
    0%, 100% { transform: rotate(-4deg); }
    50%      { transform: rotate(4deg); }
  }

  /* Estrellitas de la Kitty en modo noche (ocultas de día) */
  .kitty .estrella { opacity: 0; transition: opacity 0.8s ease; }
  body.noche .kitty .estrella { opacity: 1; animation: titilar 2.4s ease-in-out infinite; }
  @keyframes titilar {
    0%, 100% { opacity: 0.4; }
    50%      { opacity: 1; }
  }

  /* Popup sorpresa de la Kitty */
  #sorpresa {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0.85);
    background: var(--tarjeta-bg);
    backdrop-filter: blur(10px);
    border: 1.5px solid var(--rosa-borde);
    border-radius: 20px;
    padding: 28px 34px;
    max-width: 340px;
    text-align: center;
    color: var(--texto);
    font-size: 1.05rem;
    line-height: 1.7;
    box-shadow: 0 20px 60px rgba(214,140,160,0.35);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.4s, transform 0.4s;
    z-index: 100;
  }
  #sorpresa.visible {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
    pointer-events: auto;
  }
  #sorpresa .emoji-grande {
    font-size: 2rem;
    display: block;
    margin-bottom: 8px;
  }
  #sorpresa small {
    display: block;
    margin-top: 14px;
    color: var(--texto-suave);
    font-size: 0.8rem;
    font-style: italic;
  }

  /* Corazones que salen al hacer clic en la Kitty */
  .corazon-pop {
    position: fixed;
    pointer-events: none;
    color: var(--rosa-fuerte);
    font-size: 1.4rem;
    z-index: 99;
    animation: pop 1.4s ease-out forwards;
  }
  @keyframes pop {
    0%   { transform: translate(0, 0) scale(0.5); opacity: 1; }
    100% { transform: translate(var(--dx), var(--dy)) scale(1.2) rotate(var(--rot)); opacity: 0; }
  }

  /* Pantalla de acceso */
  #acceso { text-align: center; padding-top: 20px; }
  #acceso p {
    font-size: 1.05rem;
    line-height: 1.8;
    color: var(--texto-suave);
    margin: 0 0 22px;
    transition: color 0.8s ease;
  }
  #acceso .corazoncito {
    color: var(--rosa);
    font-size: 1.3rem;
    display: inline-block;
    animation: latir 1.6s ease-in-out infinite;
  }
  @keyframes latir {
    0%, 100% { transform: scale(1); }
    15%      { transform: scale(1.18); }
    30%      { transform: scale(1); }
  }

  #clave {
    background: var(--tarjeta-bg);
    border: 1.5px solid var(--rosa-borde);
    border-radius: 14px;
    color: var(--texto);
    font-family: 'Georgia', serif;
    font-size: 1.05rem;
    text-align: center;
    padding: 12px 16px;
    width: 80%;
    outline: none;
    transition: border-color 0.25s, box-shadow 0.25s, background 0.8s ease, color 0.8s ease;
  }
  #clave:focus {
    border-color: var(--rosa);
    box-shadow: 0 0 0 4px rgba(241, 138, 168, 0.15);
  }

  #entrar {
    display: block;
    margin: 22px auto 0;
    background: linear-gradient(135deg, #ffb3c9, #ff8fab);
    border: none;
    color: #fff;
    padding: 12px 30px;
    border-radius: 26px;
    cursor: pointer;
    font-family: 'Georgia', serif;
    font-size: 1rem;
    letter-spacing: 0.5px;
    box-shadow: 0 6px 16px rgba(255, 143, 171, 0.35);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  #entrar:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 22px rgba(255, 143, 171, 0.45);
  }
  #error {
    color: var(--rosa-fuerte);
    font-size: 0.88rem;
    margin-top: 14px;
    min-height: 1.2em;
    font-style: italic;
  }

  /* Carta */
  #escena { display: none; }
  #escena.visible { display: block; }

  #carta {
    font-size: 1.06rem;
    line-height: 1.9;
    white-space: pre-wrap;
    color: var(--texto-carta);
    min-height: 50vh;
    transition: color 0.8s ease;
  }

  /* Cursor corazón */
  .cursor {
    display: inline-block;
    color: var(--cursor-color);
    font-size: 1rem;
    margin-left: 2px;
    animation: parpadeo 1.1s infinite;
    vertical-align: text-bottom;
    transition: color 0.8s ease;
  }
  @keyframes parpadeo { 50% { opacity: 0; } }

  /* Firma */
  #firma {
    margin-top: 38px;
    opacity: 0;
    transition: opacity 1s;
    text-align: right;
  }
  #firma.visible { opacity: 1; }
  #firma path {
    stroke: var(--firma-color);
    stroke-dasharray: 1200;
    stroke-dashoffset: 1200;
    animation: dibujar 3.5s ease forwards;
    transition: stroke 0.8s ease;
  }
  @keyframes dibujar { to { stroke-dashoffset: 0; } }
  #firma text {
    font-family: 'Georgia', serif;
    font-style: italic;
    fill: var(--firma-texto);
    font-size: 13px;
    transition: fill 0.8s ease;
  }

  /* P.D. */
  #posdata {
    margin-top: 40px;
    padding: 20px 22px;
    background: var(--rosa-palido);
    border-left: 3px solid var(--rosa-borde);
    border-radius: 12px;
    font-style: italic;
    color: var(--texto-posdata);
    line-height: 1.75;
    opacity: 0;
    transform: translateY(8px);
    transition: opacity 1s, transform 1s, background 0.8s ease, color 0.8s ease, border-color 0.8s ease;
    position: relative;
  }
  #posdata.visible { opacity: 1; transform: translateY(0); }
  #posdata::before {
    content: "💌";
    position: absolute;
    top: -14px;
    left: 16px;
    background: var(--tarjeta-bg);
    padding: 0 6px;
    font-size: 1.1rem;
    border-radius: 6px;
  }

  /* Botones flotantes */
  #saltar, #musica, #modo {
    position: fixed;
    bottom: 18px;
    background: var(--tarjeta-bg);
    border: 1.5px solid var(--rosa-borde);
    color: var(--rosa);
    padding: 9px 16px;
    border-radius: 22px;
    cursor: pointer;
    font-family: 'Georgia', serif;
    font-size: 0.85rem;
    box-shadow: 0 4px 12px rgba(214,140,160,0.15);
    transition: background 0.3s, transform 0.2s, color 0.8s ease, border-color 0.8s ease;
    z-index: 10;
  }
  #saltar { right: 18px; }
  #musica { left: 18px; }
  #modo { left: 50%; transform: translateX(-50%); padding: 9px 14px; }
  #saltar:hover, #musica:hover, #modo:hover {
    background: var(--rosa-palido);
    transform: translateY(-2px);
  }
  #modo:hover { transform: translateX(-50%) translateY(-2px); }

  /* Responsive */
  @media (max-width: 520px) {
    .tarjeta { padding: 32px 22px 42px; border-radius: 18px; }
    .kitty { width: 54px; height: 54px; top: -20px; right: 14px; }
    #carta { font-size: 1rem; }
    #saltar, #musica { font-size: 0.75rem; padding: 7px 12px; }
    #modo { bottom: 58px; font-size: 0.75rem; }
  }
</style>
</head>
<body>

<div class="tarjeta">

  <!-- Hello Kitty SVG con estrellitas nocturnas -->
  <svg class="kitty" id="kitty" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" title="tocame ♡">
    <!-- orejas -->
    <path d="M20 35 L14 14 L38 24 Z" fill="var(--kitty-cabeza)" stroke="var(--kitty-linea)" stroke-width="2.5" stroke-linejoin="round"/>
    <path d="M80 35 L86 14 L62 24 Z" fill="var(--kitty-cabeza)" stroke="var(--kitty-linea)" stroke-width="2.5" stroke-linejoin="round"/>
    <!-- cabeza -->
    <ellipse cx="50" cy="56" rx="34" ry="30" fill="var(--kitty-cabeza)" stroke="var(--kitty-linea)" stroke-width="2.5"/>
    <!-- ojos -->
    <ellipse cx="39" cy="53" rx="3.2" ry="4" fill="var(--kitty-linea)"/>
    <ellipse cx="61" cy="53" rx="3.2" ry="4" fill="var(--kitty-linea)"/>
    <!-- nariz -->
    <ellipse cx="50" cy="62" rx="4" ry="3" fill="var(--kitty-nariz)"/>
    <!-- bigotes -->
    <line x1="14" y1="52" x2="30" y2="55" stroke="var(--kitty-linea)" stroke-width="2" stroke-linecap="round"/>
    <line x1="14" y1="62" x2="30" y2="62" stroke="var(--kitty-linea)" stroke-width="2" stroke-linecap="round"/>
    <line x1="86" y1="52" x2="70" y2="55" stroke="var(--kitty-linea)" stroke-width="2" stroke-linecap="round"/>
    <line x1="86" y1="62" x2="70" y2="62" stroke="var(--kitty-linea)" stroke-width="2" stroke-linecap="round"/>
    <!-- moño -->
    <circle cx="76" cy="34" r="9" fill="var(--kitty-mono)" stroke="var(--kitty-linea)" stroke-width="2"/>
    <circle cx="76" cy="34" r="3" fill="#ffd0dd"/>
    <!-- estrellitas (solo de noche) -->
    <text class="estrella" x="12" y="18" font-size="9" fill="#ffe08a">✦</text>
    <text class="estrella" x="86" y="14" font-size="7" fill="#ffe08a">✦</text>
    <text class="estrella" x="80" y="88" font-size="8" fill="#ffe08a">✦</text>
    <text class="estrella" x="18" y="84" font-size="6" fill="#ffe08a">✦</text>
  </svg>

  <!-- PANTALLA DE ACCESO -->
  <div id="acceso">
    <p>
      Esta carta tiene una llave.<br>
      Escribe cómo te llamo yo. <span class="corazoncito">♡</span>
    </p>
    <input id="clave" type="text" autocomplete="off" placeholder="..." autofocus>
    <button id="entrar">abrir</button>
    <div id="error"></div>
  </div>

  <!-- CARTA -->
  <div id="escena">
    <div id="carta"></div><span class="cursor">♥</span>

    <div id="firma">
      <svg width="220" height="70" viewBox="0 0 220 70" fill="none">
        <path d="M10 50 C 30 10, 50 10, 60 40 S 90 65, 105 35 S 135 5, 150 40 S 175 55, 195 30"
              stroke="var(--firma-color)" stroke-width="2" stroke-linecap="round"/>
        <text x="150" y="66">para ti, siempre</text>
      </svg>
    </div>

    <div id="posdata">
      P.D. Esto no cabía en el papel: si algún día dudas de si te amé,
      vuelve a abrir esta página. Batman también llora, pero siempre se levanta. 🦇
      Tenia que hacerlo, me dedico a esto y tenia que expresarme de mi manera. Gracias por existir, bonita. ♡
    </div>
  </div>

</div>

<!-- Popup sorpresa de la Kitty -->
<div id="sorpresa">
  <span class="emoji-grande">🎀</span>
  <span id="sorpresa-texto">Te quiero, mayway.</span>
  <small>toca de nuevo para otra ♡</small>
</div>

<button id="saltar">leer todo</button>
<button id="musica">♪ música</button>
<button id="modo">🌙</button>

<audio id="audio" loop>
  <!-- <source src="musica.mp3" type="audio/mpeg"> -->
</audio>

<script>
/* ====== CONFIG ====== */
const CLAVE = 'mayway';
const TEXTO = `Hola bonita,

tal vez una carta escrita a mano no me sirva de mucho para expresar todo lo que siento... soy un hombre de muchas palabras, un hombre que piensa demasiado, por eso me expreso por aquí, desde la tecnología, un lugar en donde pude ser comprendido y sentirme como en casa, así no verás los errores que cometo al escribir con los ojos llorosos.

Tengo muchas cosas por decirte, muchas cosas que hice cuando entré al borde de la locura.

No me victimizo, porque sé que confundí amabilidad con amor. ¿Amor que me imaginé? No sé, pero se sintió bonito pensar que alguien suspiraba al verme. Yo realmente llegué a amarte, a pesar de que tú quizá no, y quizá solo me veas como un amigo y en mente tengas a otra persona. Pero como te había dicho, yo quiero tu felicidad, y si no es conmigo, tengo que tragarme el trago amargo.

No llegué a amarte: te amo. Hoy, ayer y mañana.

Me gusta pasar tiempo contigo. Quizá mi habilidad de sobrepensar me hizo entender que no debía compartir más tiempo contigo, porque me dolería más saber que no me ves con unos ojos como los que yo te miro. Y no solo yo lo sé: alguien una vez me dijo "se nota que amas a esa mujer, tus ojos se iluminan al verla y tenerla de frente". Maldito sabio, jaja. Realmente sí la amo: esa mujer que se ríe de cada chiste mío, con la que puedo ser yo, sacar mi lado autista y reírnos juntos. Una mujer que me generó autoestima y me hizo sentir bonito luego de aplastarme en mi mundo de mierda. Gracias por ello, mayway.

Sé que dentro de ti amas muy bonito y me consta, pero quizá no sea el tiempo adecuado. Eres una GRAN MUJER, súper emprendedora, ojo ahí: que nadie te ame menos, sino más que yo. Solo soy un niño enamorado, alguien que suspira, llora y ríe por ti. ¿Estaré loco? No lo sé, quizá sí padezca de alguna cosa mental, pero ni la siento cuando comparto tiempo contigo. Y dentro de mí soy Batman: el que, a pesar de que siempre termina destrozado, sabe cómo levantarse. Y yo hago eso.

Te quiero, y quizá tenga que aprender a verte como una amiga si es lo que deseas, con tal de no perderte. Jaja, qué tonoto.

¿Ya te dije que me enamoré de la niña que conocí en el gym? Esa que está desarreglada y sudada, y no la niña arreglada. Fakk, qué bonita. Siempre siento lo mismo que sentí el primer día que te conocí de lejos. Aún sigues causándome nervios cuando estás junto a mí. Después de todo eres súper bonita, demasiado, peligrosamente demasiado.

Jaja, algo que me dijeron una vez: "¿pues qué chiste contaste, o qué hiciste para que ella te hablara?" Oí, quieras o no, algunas cosas de ti se me quedaron grabadas, palabritas que dices. Deeeeeeam.

Batman también llora. Perdona.`;

/* Mensajes rotativos de la Kitty */
const MENSAJES_KITTY = [
  'Te quiero, mayway.',
  'Eres mi persona favorita en el gym. ',
  'Batman también llora, pero sonríe contigo. 🦇',
  'Gracias por existir, bonita.',
  'Si esto es un sueño, no me despiertes.',
  'Esa risa tuya me tiene enamorado. 🎀'
];

/* ====== MODO NOCTURNO AUTOMÁTICO ====== */
const body = document.body;
const modoBtn = document.getElementById('modo');

function esNoche() {
  const h = new Date().getHours();
  return h >= 20 || h < 7;
}

function aplicarModo(noche, manual = false) {
  if (noche) {
    body.classList.add('noche');
    modoBtn.textContent = '☀️';
    modoBtn.title = 'cambiar a modo día';
  } else {
    body.classList.remove('noche');
    modoBtn.textContent = '🌙';
    modoBtn.title = 'cambiar a modo noche';
  }
  if (manual) localStorage.setItem('modoManual', noche ? 'noche' : 'dia');
}

// Al cargar: si el usuario forzó un modo, respetarlo; si no, usar la hora
const modoGuardado = localStorage.getItem('modoManual');
if (modoGuardado === 'noche') aplicarModo(true);
else if (modoGuardado === 'dia') aplicarModo(false);
else aplicarModo(esNoche());

// Si no hay modo manual, revisar cada minuto si cambió la hora
setInterval(() => {
  if (!localStorage.getItem('modoManual')) aplicarModo(esNoche());
}, 60000);

// Botón para forzar el modo
modoBtn.addEventListener('click', () => {
  aplicarModo(!body.classList.contains('noche'), true);
});

/* ====== CORAZONES DE FONDO ====== */
(function generarCorazones() {
  const simbolos = ['♡', '♥', '✿', '♡'];
  for (let k = 0; k < 14; k++) {
    const c = document.createElement('div');
    c.className = 'corazon-fondo';
    c.textContent = simbolos[Math.floor(Math.random() * simbolos.length)];
    c.style.left = Math.random() * 100 + 'vw';
    c.style.fontSize = (0.8 + Math.random() * 1.4) + 'rem';
    c.style.animationDuration = (10 + Math.random() * 10) + 's';
    c.style.animationDelay = (Math.random() * 12) + 's';
    document.body.appendChild(c);
  }
})();

/* ====== LÓGICA DE LA CARTA ====== */
const acceso = document.getElementById('acceso');
const escena = document.getElementById('escena');
const claveInput = document.getElementById('clave');
const error = document.getElementById('error');
const contenedor = document.getElementById('carta');
const cursor = document.querySelector('.cursor');
const firma = document.getElementById('firma');
const posdata = document.getElementById('posdata');
const saltar = document.getElementById('saltar');
const musicaBtn = document.getElementById('musica');
const audio = document.getElementById('audio');

let i = 0, animando = false, timer;

function abrir() {
  const val = claveInput.value.trim().toLowerCase();
  if (val === CLAVE) {
    acceso.style.display = 'none';
    escena.classList.add('visible');
    saltar.style.display = 'block';
    musicaBtn.style.display = 'block';
    animando = true;
    escribir();
  } else {
    error.textContent = 'esa no es la llave... intenta de nuevo ♡';
    claveInput.value = '';
  }
}

document.getElementById('entrar').addEventListener('click', abrir);
claveInput.addEventListener('keydown', e => { if (e.key === 'Enter') abrir(); });

function escribir() {
  if (!animando) return;
  if (i < TEXTO.length) {
    contenedor.textContent += TEXTO.charAt(i);
    const ch = TEXTO.charAt(i);
    i++;
    let pausa = 32;
    if (ch === '.') pausa = 320;
    if (ch === ',') pausa = 140;
    if (ch === '\n') pausa = 480;
    timer = setTimeout(escribir, pausa);
  } else {
    finalizar();
  }
}

function finalizar() {
  animando = false;
  cursor.style.display = 'none';
  firma.classList.add('visible');
  setTimeout(() => posdata.classList.add('visible'), 2500);
}

saltar.addEventListener('click', () => {
  clearTimeout(timer);
  animando = false;
  contenedor.textContent = TEXTO;
  finalizar();
});

musicaBtn.addEventListener('click', () => {
  if (audio.paused) { audio.play(); musicaBtn.textContent = '❚❚ pausa'; }
  else { audio.pause(); musicaBtn.textContent = '♪ música'; }
});

/* Ocultar botones hasta abrir */
saltar.style.display = 'none';
musicaBtn.style.display = 'none';

/* ====== EASTER EGG: CLIC EN LA KITTY ====== */
const kitty = document.getElementById('kitty');
const sorpresa = document.getElementById('sorpresa');
const sorpresaTexto = document.getElementById('sorpresa-texto');
let indiceMensaje = 0;
let ocultarTimer = null;

function lanzarCorazones(x, y) {
  for (let k = 0; k < 8; k++) {
    const c = document.createElement('div');
    c.className = 'corazon-pop';
    c.textContent = Math.random() > 0.5 ? '♥' : '♡';
    c.style.left = x + 'px';
    c.style.top = y + 'px';
    const dx = (Math.random() - 0.5) * 220;
    const dy = -80 - Math.random() * 160;
    const rot = (Math.random() - 0.5) * 90;
    c.style.setProperty('--dx', dx + 'px');
    c.style.setProperty('--dy', dy + 'px');
    c.style.setProperty('--rot', rot + 'deg');
    document.body.appendChild(c);
    setTimeout(() => c.remove(), 1500);
  }
}

kitty.addEventListener('click', (e) => {
  // posicionar corazones desde el centro de la Kitty
  const rect = kitty.getBoundingClientRect();
  lanzarCorazones(rect.left + rect.width / 2, rect.top + rect.height / 2);

  // rotar mensaje
  sorpresaTexto.textContent = MENSAJES_KITTY[indiceMensaje % MENSAJES_KITTY.length];
  indiceMensaje++;

  sorpresa.classList.add('visible');

  clearTimeout(ocultarTimer);
  ocultarTimer = setTimeout(() => sorpresa.classList.remove('visible'), 3500);
});

// tocar fuera del popup lo cierra
sorpresa.addEventListener('click', () => sorpresa.classList.remove('visible'));
</script>
</body>
</html>
