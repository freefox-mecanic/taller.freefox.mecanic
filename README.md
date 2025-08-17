[README.md](https://github.com/user-attachments/files/21824215/README.md)
# Create a complete static website for "Mecánica Real" and zip it for download

import os
import zipfile
from textwrap import dedent

base_dir = "/mnt/data/mecanica-real"
assets_dir = os.path.join(base_dir, "assets")
os.makedirs(assets_dir, exist_ok=True)

# -------------------------
# index.html
# -------------------------
index_html = dedent("""
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Mecánica Real | Taller mecánico en Navarra</title>
  <meta name="description" content="Mecánica Real: taller mecánico en Navarra. Mantenimiento, diagnosis, frenos, neumáticos y más. Atención rápida y honesta. Tel: 747 404 236." />
  <meta name="keywords" content="taller mecánico, Navarra, mecánica, frenos, neumáticos, diagnosis, mantenimiento, coche" />
  <meta name="author" content="Mecánica Real" />
  <link rel="icon" href="assets/favicon.svg" type="image/svg+xml">
  <meta property="og:title" content="Mecánica Real | Taller mecánico en Navarra" />
  <meta property="og:description" content="Mantenimiento, diagnosis, frenos y neumáticos. Atención rápida y honesta." />
  <meta property="og:type" content="website" />
  <meta property="og:image" content="assets/og-cover.jpg" />
  <meta property="og:url" content="https://tudominio.com" />
  <meta name="theme-color" content="#ff5a1f" />
  <link rel="preload" href="styles.css" as="style">
  <link rel="stylesheet" href="styles.css">
  <script defer src="script.js"></script>
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "AutoRepair",
    "name": "Mecánica Real",
    "image": "https://tudominio.com/assets/og-cover.jpg",
    "telephone": "+34 747404236",
    "address": {
      "@type": "PostalAddress",
      "addressLocality": "Navarra",
      "addressCountry": "ES"
    },
    "url": "https://tudominio.com",
    "openingHours": "Mo-Fr 09:00-14:00,16:00-19:00",
    "priceRange": "€€"
  }
  </script>
</head>
<body>
  <header class="topbar">
    <div class="container bar">
      <a href="#" class="brand" aria-label="Mecánica Real - Inicio">
        <img src="assets/logo.svg" alt="Logo Mecánica Real" class="logo">
        <span>Mecánica Real</span>
      </a>
      <nav id="nav" class="nav">
        <a href="#servicios">Servicios</a>
        <a href="#por-que">¿Por qué nosotros?</a>
        <a href="#opiniones">Opiniones</a>
        <a href="#contacto">Contacto</a>
        <a class="cta" href="tel:+34747404236">Llámanos</a>
      </nav>
      <button id="menuBtn" class="menu" aria-label="Abrir menú">☰</button>
    </div>
  </header>

  <section class="hero">
    <div class="container hero-wrap">
      <div class="hero-text">
        <h1>Tu coche a punto, sin sorpresas</h1>
        <p>Mantenimiento rápido y honesto en Navarra: revisiones, diagnosis, frenos y neumáticos. Pide cita y lo tendrás listo en tiempo récord.</p>
        <div class="actions">
          <a class="btn primary" href="tel:+34747404236">📞 747 404 236</a>
          <a class="btn ghost" href="#contacto">Pedir cita</a>
        </div>
        <ul class="badges">
          <li>✔ Garantía en mano de obra</li>
          <li>✔ Presupuesto previo</li>
          <li>✔ Repuestos de calidad</li>
        </ul>
      </div>
      <div class="hero-media">
        <img src="assets/hero-car.jpg" alt="Taller mecánico trabajando en un coche">
      </div>
    </div>
  </section>

  <section id="servicios" class="section">
    <div class="container">
      <h2>Servicios principales</h2>
      <div class="grid cards">
        <article class="card">
          <h3>Revisiones y aceite</h3>
          <p>Cambio de aceite y filtros, revisión general y puesta a punto para viajar seguro.</p>
        </article>
        <article class="card">
          <h3>Diagnosis electrónica</h3>
          <p>Lectura de errores OBD-II y reparación de averías eléctricas y sensores.</p>
        </article>
        <article class="card">
          <h3>Frenos</h3>
          <p>Pastillas, discos y líquido de frenos. Seguridad y rendimiento al máximo.</p>
        </article>
        <article class="card">
          <h3>Neumáticos</h3>
          <p>Montaje, equilibrado y alineado. Las mejores marcas a buen precio.</p>
        </article>
        <article class="card">
          <h3>Pre-ITV</h3>
          <p>Comprobamos tu vehículo para que pase la ITV a la primera.</p>
        </article>
        <article class="card">
          <h3>Climatización</h3>
          <p>Carga de A/A, diagnosis de fugas y mantenimiento del sistema.</p>
        </article>
      </div>
    </div>
  </section>

  <section id="por-que" class="section alt">
    <div class="container why">
      <div>
        <h2>Honestos, rápidos y profesionales</h2>
        <p>Somos un taller de confianza: te explicamos cada reparación y te damos opciones claras. Sin sorpresas.</p>
        <ul class="checks">
          <li>✔ Citas rápidas</li>
          <li>✔ Piezas de calidad</li>
          <li>✔ Garantía escrita</li>
        </ul>
      </div>
      <img src="assets/workbench.jpg" alt="Mesa de trabajo de taller mecánico">
    </div>
  </section>

  <section id="opiniones" class="section">
    <div class="container">
      <h2>Opiniones reales</h2>
      <div class="grid reviews">
        <blockquote>
          “Me lo dejaron perfecto y a buen precio. Repetiré.”
          <footer>— Laura G.</footer>
        </blockquote>
        <blockquote>
          “Rápidos y muy claros con el presupuesto. 10/10.”
          <footer>— Miguel P.</footer>
        </blockquote>
        <blockquote>
          “Atención de 10 y sin esperas eternas. Recomendado.”
          <footer>— Ainhoa L.</footer>
        </blockquote>
      </div>
    </div>
  </section>

  <section id="contacto" class="section alt">
    <div class="container">
      <h2>Pide cita</h2>
      <p>Rellena el formulario y te llamamos. También puedes escribir por WhatsApp o llamar al <a href="tel:+34747404236">747 404 236</a>.</p>
      <form id="contactForm" action="https://formspree.io/f/XXXXXXXX" method="POST" class="form">
        <div class="row">
          <label>Nombre
            <input type="text" name="nombre" required placeholder="Tu nombre" />
          </label>
          <label>Teléfono
            <input type="tel" name="telefono" required placeholder="Tu teléfono" />
          </label>
        </div>
        <label>Servicio
          <select name="servicio" required>
            <option value="">Selecciona…</option>
            <option>Revisión</option>
            <option>Diagnosis</option>
            <option>Frenos</option>
            <option>Neumáticos</option>
            <option>Otro</option>
          </select>
        </label>
        <label>Mensaje
          <textarea name="mensaje" rows="4" placeholder="Cuéntanos brevemente"></textarea>
        </label>
        <input type="hidden" name="_subject" value="Nueva cita desde la web" />
        <button class="btn primary" type="submit">Enviar</button>
        <p class="form-note">Al enviar aceptas nuestra <a href="#aviso">política de privacidad</a>.</p>
      </form>
      <div class="contact-extras">
        <a class="whatsapp" href="https://wa.me/34747404236" target="_blank" rel="noopener">WhatsApp directo</a>
        <a class="ghost" href="mailto:info@tudominio.com">info@tudominio.com</a>
      </div>
    </div>
  </section>

  <footer class="footer">
    <div class="container foot">
      <div class="col">
        <a href="#" class="brand mini">
          <img src="assets/logo.svg" alt="Logo Mecánica Real" class="logo small">
          <span>Mecánica Real</span>
        </a>
        <p>Navarra, España<br> Tel: <a href="tel:+34747404236">747 404 236</a></p>
      </div>
      <div class="col">
        <h4>Horario</h4>
        <p>Lunes a Viernes<br> 9:00–14:00 y 16:00–19:00</p>
      </div>
      <div class="col">
        <h4>Redes</h4>
        <p><a href="#">Google Maps</a> · <a href="#">Facebook</a> · <a href="#">Instagram</a></p>
      </div>
    </div>
    <div class="legal" id="aviso">
      © <span id="year"></span> Mecánica Real. Todos los derechos reservados. | Aviso legal y privacidad.
    </div>
  </footer>
</body>
</html>
""")

# -------------------------
# styles.css
# -------------------------
styles_css = dedent("""
/* Paleta: naranja principal, negro, blanco, acento rojo */
:root{
  --orange:#ff5a1f;
  --black:#0f1115;
  --white:#ffffff;
  --red:#e11d48;
  --gray:#f5f6f8;
}

*{box-sizing:border-box}
html,body{margin:0;padding:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Inter,Arial,sans-serif;color:var(--black);background:var(--white)}

.container{max-width:1100px;margin:0 auto;padding:0 16px}
.topbar{position:sticky;top:0;background:rgba(255,255,255,.9);backdrop-filter:saturate(1.2) blur(6px);border-bottom:1px solid #eee;z-index:50}
.bar{display:flex;align-items:center;justify-content:space-between;height:64px}
.brand{display:flex;align-items:center;gap:10px;font-weight:800;text-decoration:none;color:var(--black)}
.logo{height:32px;width:32px}
.logo.small{height:24px;width:24px}
.nav{display:flex;gap:18px;align-items:center}
.nav a{color:var(--black);text-decoration:none;font-weight:600}
.nav .cta{background:var(--red);color:var(--white);padding:10px 14px;border-radius:999px}
.menu{display:none;border:0;background:transparent;font-size:22px}

.hero{background:linear-gradient(180deg,#fff, #fff2ec 60%, #fff);padding:48px 0 32px;border-bottom:1px solid #ffe3d8}
.hero-wrap{display:grid;grid-template-columns:1.1fr .9fr;gap:28px;align-items:center}
.hero-text h1{font-size:42px;line-height:1.05;margin:0 0 12px}
.hero-text p{font-size:18px;color:#333;margin:0 0 18px}
.actions{display:flex;gap:12px;margin-bottom:10px}
.btn{display:inline-block;border:2px solid var(--black);padding:12px 16px;border-radius:12px;text-decoration:none;font-weight:700}
.btn.primary{background:var(--orange);border-color:var(--orange);color:#111}
.btn.ghost{background:transparent}
.badges{display:flex;gap:14px;flex-wrap:wrap;padding:0;margin:10px 0 0;list-style:none}
.hero-media img{width:100%;height:auto;border-radius:16px;box-shadow:0 10px 30px rgba(255,90,31,.25)}

.section{padding:56px 0}
.section.alt{background:var(--gray)}
h2{font-size:30px;margin:0 0 20px}
.grid.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.card{background:#fff;border:1px solid #eee;border-radius:14px;padding:18px;box-shadow:0 8px 18px rgba(0,0,0,.03)}
.card h3{margin:0 0 8px}

.why{display:grid;grid-template-columns:1.1fr .9fr;gap:22px;align-items:center}
.why img{width:100%;border-radius:14px;border:1px solid #eee}
.checks{padding-left:0;list-style:none;display:grid;gap:6px}

.grid.reviews{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
blockquote{background:#fff;border-left:6px solid var(--orange);margin:0;padding:14px 16px;border-radius:8px;border:1px solid #eee;box-shadow:0 8px 18px rgba(0,0,0,.03)}
blockquote footer{margin-top:8px;color:#555}

.form{display:grid;gap:12px;background:#fff;border:1px solid #eee;border-radius:14px;padding:18px}
.form .row{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.form label{display:grid;gap:6px;font-weight:600}
input,select,textarea{padding:12px 10px;border-radius:10px;border:1px solid #ddd;font:inherit}
.form-note{font-size:12px;color:#555}
.contact-extras{margin-top:12px;display:flex;gap:10px;flex-wrap:wrap}
.whatsapp{display:inline-block;background:#25D366;color:#fff;text-decoration:none;padding:10px 12px;border-radius:10px}

.footer{background:var(--black);color:#cbd5e1}
.foot{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;padding:24px 0}
.footer a{color:#e2e8f0}
.footer .brand{color:#e2e8f0}
.legal{text-align:center;border-top:1px solid rgba(255,255,255,.1);padding:12px 0;color:#94a3b8;font-size:14px}

@media (max-width: 900px){
  .hero-wrap{grid-template-columns:1fr}
  .grid.cards{grid-template-columns:1fr 1fr}
  .grid.reviews{grid-template-columns:1fr}
  .why{grid-template-columns:1fr}
  .nav{display:none;position:absolute;right:16px;top:64px;background:#fff;border:1px solid #eee;border-radius:12px;flex-direction:column;padding:12px}
  .menu{display:block}
}
""")

# -------------------------
# script.js
# -------------------------
script_js = dedent("""
document.getElementById('year').textContent = new Date().getFullYear();

const menuBtn = document.getElementById('menuBtn');
const nav = document.getElementById('nav');
menuBtn.addEventListener('click', () => {
  if (nav.style.display === 'flex') {
    nav.style.display = 'none';
  } else {
    nav.style.display = 'flex';
  }
});

// Cliente-ligero para Formspree (muestra alertas)
const form = document.getElementById('contactForm');
if (form) {
  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    const data = new FormData(form);
    try {
      const r = await fetch(form.action, { method:'POST', body:data, headers:{ 'Accept': 'application/json' } });
      if (r.ok) {
        alert('¡Gracias! Te contactamos en breve.');
        form.reset();
      } else {
        alert('No se pudo enviar. Prueba de nuevo o llámanos.');
      }
    } catch(err){
      alert('Error de conexión. Inténtalo más tarde.');
    }
  });
}
""")

# -------------------------
# Simple SVG logo placeholder
# -------------------------
logo_svg = dedent("""
<svg xmlns="http://www.w3.org/2000/svg" width="256" height="256" viewBox="0 0 256 256">
  <defs>
    <linearGradient id="g" x1="0" x2="1" y1="0" y2="1">
      <stop offset="0" stop-color="#ff5a1f"/>
      <stop offset="1" stop-color="#e11d48"/>
    </linearGradient>
  </defs>
  <rect width="256" height="256" rx="36" fill="url(#g)"/>
  <g fill="#fff">
    <path d="M78 176h100a10 10 0 0 0 9.5-6.9l16-48A10 10 0 0 0 194 110H62a10 10 0 0 0-9.5 11.1l16 48A10 10 0 0 0 78 176z"/>
    <circle cx="96" cy="188" r="18"/>
    <circle cx="160" cy="188" r="18"/>
    <text x="128" y="88" text-anchor="middle" font-size="34" font-weight="800" font-family="Arial, Helvetica, sans-serif">MR</text>
  </g>
</svg>
""")

# -------------------------
# Placeholder images (small solid-color JPGs)
# -------------------------
from PIL import Image, ImageDraw, ImageFont

def placeholder(path, text, color=(255, 90, 31)):
    img = Image.new("RGB", (1200, 800), color=color)
    d = ImageDraw.Draw(img)
    # Basic text placement
    try:
        font = ImageFont.truetype("DejaVuSans-Bold.ttf", 56)
    except:
        font = ImageFont.load_default()
    w, h = d.textsize(text, font=font)
    d.rectangle([(0,0),(1199,60)], fill=(15,17,21))
    d.text(((1200-w)//2, (800-h)//2), text, fill=(255,255,255), font=font)
    img.save(path, "JPEG", quality=85)

placeholder(os.path.join(assets_dir, "hero-car.jpg"), "Mecánica Real - Tu coche a punto", (255, 234, 226))
placeholder(os.path.join(assets_dir, "workbench.jpg"), "Banco de trabajo - Mecánica Real", (245, 246, 248))
placeholder(os.path.join(assets_dir, "og-cover.jpg"), "Mecánica Real", (255, 90, 31))

# -------------------------
# Favicon
# -------------------------
with open(os.path.join(assets_dir, "favicon.svg"), "w", encoding="utf-8") as f:
    f.write("""<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 64 64'><rect width='64' height='64' rx='10' fill='#ff5a1f'/><path d='M16 36h32l6-16H10z' fill='#fff'/></svg>""")

# Write the rest of files
with open(os.path.join(base_dir, "index.html"), "w", encoding="utf-8") as f:
    f.write(index_html)

with open(os.path.join(base_dir, "styles.css"), "w", encoding="utf-8") as f:
    f.write(styles_css)

with open(os.path.join(base_dir, "script.js"), "w", encoding="utf-8") as f:
    f.write(script_js)

with open(os.path.join(assets_dir, "logo.svg"), "w", encoding="utf-8") as f:
    f.write(logo_svg)

# -------------------------
# README with Nominalia instructions
# -------------------------
readme_md = dedent("""
# Mecánica Real — Web estática lista para subir

**Colores:** naranja (#ff5a1f), negro (#0f1115), blanco (#ffffff), acento rojo (#e11d48)  
**Teléfono:** 747 404 236

## Estructura
- `index.html`
- `styles.css`
- `script.js`
- `assets/` (imágenes, logo, favicon)

## Formulario (Formspree)
1. Crea una cuenta gratuita en Formspree.
2. Crea un formulario y copia el ID del endpoint (formato `https://formspree.io/f/xxxxxxx`).
3. Abre `index.html` y reemplaza en el `<form>` el atributo `action="https://formspree.io/f/XXXXXXXX"` por tu URL real.
4. Opcional: en Formspree activa reCAPTCHA/anti-spam.

## Subir a Nominalia (FTP o Gestor de Archivos)
### Opción A — Gestor de Archivos (rápido)
1. Entra en tu panel de **Nominalia** > tu **hosting**.
2. Abre **Gestor de Archivos**.
3. En el directorio `public_html` (o `httpdocs`), pulsa **Subir** y selecciona el archivo `mecanica-real-web.zip`.
4. Una vez subido, selecciónalo y pulsa **Extraer**. Asegúrate de que `index.html` queda directamente dentro de `public_html`.
5. Visita tu dominio para comprobar.

### Opción B — FTP (FileZilla)
1. En Nominalia, busca los datos FTP: **servidor**, **usuario**, **contraseña**.
2. Abre **FileZilla** y conecta (Puerto: 21 o 22 según configuración).
3. En el panel derecho entra a `public_html`.
4. Arrastra todo el contenido de la carpeta (no la carpeta en sí) al panel derecho.
5. Cuando termine, abre tu dominio en el navegador.

## Personalización rápida
- Cambia `https://tudominio.com` y `info@tudominio.com` por tus datos.
- Cambia imágenes en `assets/` por fotos reales del taller.
- Edita textos en `index.html` (servicios, opiniones, horario).
- Si tienes dirección exacta, añádela en el JSON-LD (schema.org).

¡Listo!
""")

with open(os.path.join(base_dir, "README.txt"), "w", encoding="utf-8") as f:
    f.write(readme_md)

# -------------------------
# Create ZIP
# -------------------------
zip_path = "/mnt/data/mecanica-real-web.zip"
with zipfile.ZipFile(zip_path, 'w', zipfile.ZIP_DEFLATED) as z:
    for root, _, files in os.walk(base_dir):
        for file in files:
            full_path = os.path.join(root, file)
            arcname = os.path.relpath(full_path, base_dir)
            z.write(full_path, arcname)

zip_path
