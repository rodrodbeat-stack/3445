# 888 Digital Factory — Cyber Web

Web estática inspirada en una mezcla de **cyberpunk industrial + interfaz militar futurista + horror biomecánico**, usando la imagen entregada como banner principal.

## Estructura

- `index.html` — página principal
- `style.css` — diseño responsive, efectos CRT, HUD y terminal
- `script.js` — animación de terminal y entrada de tarjetas
- `assets/banner.jpg` — imagen proporcionada

## Ejecutar

### Opción 1 — navegador
Abre `index.html`.

### Opción 2 — servidor local

```bash
python3 -m http.server 8080
```

Luego abre:

`http://localhost:8080`

## Publicar en GitHub Pages

```bash
git init
git add .
git commit -m "feat: 888 digital factory cyber website"
git branch -M main
git remote add origin https://github.com/USUARIO/REPOSITORIO.git
git push -u origin main
```

Después activa GitHub Pages desde Settings → Pages → Deploy from branch → `main`.

## Concepto visual

La interfaz evita copiar elementos concretos de una película o franquicia y utiliza recursos originales de estética cyberpunk: CRT, verde fosforescente, HUD, retículas, terminal, mapa de red y biomecánica industrial.


## CI/CD con GitHub Actions

El proyecto ahora incluye un pipeline:

```text
Developer
   │
   ▼
GitHub
   │
   ├── Pull Request
   │      │
   │      └── CI
   │           ├── Validar archivos
   │           ├── Validar JavaScript
   │           └── Docker Build
   │
   └── merge/push a main
          │
          └── CD
               └── GitHub Pages
```

### Pipeline

Archivo:

```text
.github/workflows/ci-cd.yml
```

Cada cambio en `main` ejecuta:

1. Checkout del código.
2. Validación de la estructura.
3. Validación sintáctica de JavaScript.
4. Build de imagen Docker.
5. Publicación automática en GitHub Pages.

### Docker

Construir:

```bash
docker build -t 888-digital-factory .
```

Ejecutar:

```bash
docker run -d --name 888-factory -p 8080:80 888-digital-factory
```

Abrir:

```text
http://localhost:8080
```

O con Compose:

```bash
docker compose up -d --build
```

### Activar GitHub Pages

En el repositorio:

```text
Settings
  → Pages
  → Source: GitHub Actions
```

Después:

```bash
git add .
git commit -m "feat: add CI/CD pipeline"
git push origin main
```

GitHub Actions hará automáticamente:

```text
git push
   ↓
CI
   ↓
Docker Build
   ↓
CD
   ↓
GitHub Pages
```

### Siguiente nivel AWS

La siguiente evolución puede reemplazar GitHub Pages por:

```text
GitHub
   ↓
GitHub Actions
   ↓
Terraform
   ↓
AWS
   ├── S3
   ├── CloudFront
   └── Route 53
```

Así el laboratorio pasa de una web estática a un escenario real de **GitHub + CI/CD + Terraform + AWS**.
