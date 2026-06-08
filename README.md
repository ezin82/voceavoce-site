# Sito "Voce a Voce" (landing statica)

Landing page statica multilingua (IT/EN/ES) per il canale di studio corale. Nessun build: solo HTML/CSS/JS.
Gli asset di brand (`assets/avatar.png`, `banner.png`, `watermark.png`) sono generati con
`python -m scripts.cli.job_brand_assets` (rigenerali e ricopiali qui se cambi logo/colori).

## Anteprima locale
Apri `index.html` nel browser, oppure:
```
python -m http.server 8000   # dentro la cartella site/  →  http://localhost:8000
```

## Deploy gratis su GitHub Pages
1. Crea un repo **pubblico** (es. `voceavoce-site`) e mettici il contenuto di questa cartella `site/`
   (oppure pubblica da questo repo: Settings → Pages → Source = branch + cartella `/site`).
2. Repo → **Settings → Pages** → Source = branch `main` (cartella root del repo del sito, o `/site`).
   Pages pubblica su `https://<utente>.github.io/<repo>/` con HTTPS gratis.
3. `.nojekyll` è già incluso (evita l'elaborazione Jekyll).

## Dominio personalizzato (es. voceavoce.com)
Compra **solo il dominio** (Aruba "solo registrazione", o Cloudflare Registrar). Poi:
1. Crea il file **`CNAME`** in questa cartella con una riga: `voceavoce.com`.
2. Nel **DNS del registrar** (pannello Aruba):
   - record **A** per `voceavoce.com` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - record **CNAME** per `www` → `<utente>.github.io`
3. Repo → Settings → Pages → **Custom domain** = `voceavoce.com` → spunta **Enforce HTTPS**.
NB: lo **spazio web di Aruba NON serve** (il sito sta su Pages).

## Email info@voceavoce.com (separata dal sito; convive coi record sopra)
La registrazione dominio NON include la casella. Aggiungi un servizio email (record **MX**):
- **Cloudflare Email Routing** (gratis): inoltra `info@voceavoce.com` → la tua Gmail.
- **Zoho Mail** (piano gratuito): casella vera sul dominio.
- **Aruba** (a pagamento): casella inclusa nel piano mail/hosting.
I record MX (email) e A/CNAME (sito Pages) **coesistono** senza conflitti.

## Da personalizzare prima del lancio
- Link **Podcast** (`data-link="podcast"`) e gli handle social reali in `index.html`.
- Verifica handle `@voceavoce` su YouTube/social e il dominio prima di fissarli.
