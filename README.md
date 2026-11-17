# Dashboard Paid Media · Kaleos

Dashboard de Meta Ads + Google Ads de Kaleos. Se regenera solo cada día antes de las 7:00 (hora de Madrid) con datos desde el 1 de enero hasta ayer y se publica en GitHub Pages en una URL pública (sin contraseña).

## Cómo funciona

1. GitHub Actions lanza `.github/workflows/actualizar-dashboard.yml` cada día a las 5:40 de Madrid.
2. `build.py` descarga los datos de Windsor.ai (cuentas de `config.json`) y rellena `template.html`.
3. Se publica en GitHub Pages. Si algo falla, el dashboard de ayer sigue online y GitHub avisa por email.

## Archivos

| Archivo | Para qué |
|---|---|
| `build.py` | Descarga y procesa los datos |
| `template.html` | Diseño y lógica del dashboard |
| `config.json` | Cuentas, acción de compra de Google, nombres de anuncios de Google |
| `.github/workflows/actualizar-dashboard.yml` | Programación diaria y publicación |

## Secreto necesario (Settings → Secrets and variables → Actions)

| Nombre | Valor |
|---|---|
| `WINDSOR_API_KEY` | API key de la cuenta de Windsor.ai donde están conectadas las cuentas de Kaleos |

## Tareas habituales

- **Actualizar a mano:** pestaña Actions → "Actualizar dashboard Kaleos" → Run workflow.

## Probar en local

```bash
pip install -r requirements.txt
WINDSOR_API_KEY=tu_clave python build.py   # genera dist/index.html
```
