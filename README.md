# SimCoder

Blog statico con [Hugo](https://gohugo.io) (versione **extended**, provato con 0.169) e il tema [PaperMod](https://github.com/adityatelange/hugo-PaperMod), personalizzato con Intel One Mono, sfondo chiaro non bianco e blocchi di codice scuri.

## Primo avvio

```bash
git init -b main
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
hugo server -D
```

Poi apri http://localhost:1313. Il tema non è incluso nello zip: lo scarica il comando `git submodule add`.

## Scrivere un articolo

```bash
hugo new content posts/nome-articolo.md
```

Il file nasce con `draft: true` (visibile solo con `hugo server -D`). Quando è pronto, metti `draft: false`.
Il modello (`archetypes/default.md`) ha già lo scheletro: intro, la notizia con il link, "My take", elenco link.

Categorie consigliate: `sim`, `code`, `simcoder` (i due mondi insieme). I tag sono liberi.

## Cosa puoi usare negli articoli

- **Codice**: blocchi con tre apici e il linguaggio (` ```cpp `, ` ```csharp `). Hanno numeri di riga e pulsante "copy", che copia solo il codice.
- **Diagrammi**: blocco ` ```mermaid `. Lo script di Mermaid (da jsDelivr) viene caricato solo nelle pagine che hanno un diagramma.
- **Immagini**: metti il file in `static/images/` e scrivi `![descrizione](/images/nome.png)`.
- **YouTube**: `{{< youtube ID_DEL_VIDEO >}}` (usa youtube-nocookie.com).
- **Condivisione**: in fondo a ogni articolo ci sono X/Twitter, Facebook e "copia link" (copia l'indirizzo completo dell'articolo). Per nasconderli in un articolo, `disableShare: true` nel front matter; per cambiare quali pulsanti mostrare, `ShareButtons` in `hugo.toml`.
- **Copertina e card su X/Facebook**: ogni articolo è una cartella (`hugo new content posts/nome-articolo/index.md`) e la foto si salva lì dentro come `cover.jpg`. Compare in cima all'articolo e diventa l'immagine della card quando condividi il link su X o Facebook. Hugo ne ricava da solo una versione 1200x630 (l'originale non viene mai usata nella card, così non c'è il rischio di superare il limite di peso di X). Se un articolo non ha copertina, la card usa `static/images/social-default.jpg`.
- **Logo**: `static/images/logo.svg`, mostrato accanto al titolo. Per cambiarlo sostituisci il file (o cambia `[params.label]` in `hugo.toml`).
- **Commenti**: per articolo, con `comments: true` (o `false`) nel front matter. Servono i passi qui sotto.

## Scegliere la foto di copertina (Unsplash)

1. Cerca su https://unsplash.com e scarica la foto in una dimensione media (1600-2400 px di larghezza bastano e avanzano; le originali pesano molti MB).
2. Salvala come `cover.jpg` nella cartella dell'articolo, accanto a `index.md`.
3. Nel front matter compila `cover.alt` (descrizione breve) e `cover.caption` con il credito: `Photo by [Nome](https://unsplash.com/@nome) on [Unsplash](https://unsplash.com/photos/ID)`.

La licenza Unsplash permette l'uso gratuito, anche commerciale, senza obbligo di citare l'autore; il credito è comunque gradito. Prima di pubblicare dai un'occhiata ai termini aggiornati su https://unsplash.com/license: non valgono per le foto "Unsplash+", e vanno evitate foto con persone riconoscibili, marchi o opere protette in primo piano.

Se il file non si trova, Hugo lo segnala con un avviso in fase di build e la card ripiega sull'immagine predefinita.

Una cosa da sapere: la card compare solo quando il sito è online (X e Facebook devono poter leggere la pagina), quindi non si vede in `hugo server`. Dopo la pubblicazione, il primo link condiviso può mostrare per un po' l'immagine vecchia perché le piattaforme tengono in cache.

## Attivare i commenti (Giscus)

1. Crea il repository GitHub del blog (pubblico) e attiva *Settings → General → Features → Discussions*.
2. Installa l'app [giscus](https://github.com/apps/giscus) sul repository.
3. Vai su https://giscus.app, inserisci il repository, scegli una categoria Discussions e copia i quattro valori (`repo`, `repoId`, `category`, `categoryId`) in `[params.giscus]` di `hugo.toml`.

Finché i valori sono vuoti, i commenti non compaiono, anche con `comments: true`.

## Pubblicare su GitHub Pages

1. Fai push su GitHub (branch `main`).
2. *Settings → Pages → Source: GitHub Actions*. Il workflow `.github/workflows/hugo.yml` compila e pubblica a ogni push.
3. Per il dominio: in *Settings → Pages → Custom domain* inserisci `simcoder.ghiboz.com` e crea nel DNS un record CNAME `simcoder` che punta a `<tuo-utente>.github.io`.

Le versioni delle action nel workflow (`checkout@v4` ecc.) potrebbero avere nel frattempo una versione più nuova: se GitHub segnala avvisi, aggiornale.

## Dove si cambia l'aspetto

- `assets/css/extended/simcoder.css`: font, colori della pagina (variabili `--theme`, `--entry`, ...), colore dei blocchi di codice (`--code-block-bg`).
- Colori: la barra in alto usa `--header-bg` (`#34679a`) e `--header-fg`; lo sfondo è un azzurro "Daphne Blue" (`--theme` per gli articoli, `--code-bg` per la home, `--entry` per le card). Il colore della barra del browser sul telefono è `theme_color` in `hugo.toml`.
- Sempre in `simcoder.css`, in cima alla sezione layout: `--main-width` (larghezza della colonna, ora 840px), `--cover-ratio` (forma della copertina nell'articolo: `5 / 2` è circa il 60% dell'altezza di una foto `3 / 2`; per una copertina ancora più bassa prova `3 / 1`), `--thumb-width` e `--thumb-ratio` (miniatura nella home, ora 200px e `4 / 3`). Sotto i 600px di larghezza (telefono) la miniatura torna sopra il titolo.
- `hugo.toml`: titolo, menu, icone social, opzioni del tema.
- `static/fonts/`: Intel One Mono (licenza OFL 1.1, vedi `README.txt` nella cartella).

## Cartella di test

`content/posts/hello-simcoder.md` è un articolo di prova con codice C++/C#, diagramma, immagine e video. L'ID del video YouTube è solo un esempio. Cancellalo quando hai scritto il primo articolo vero.
