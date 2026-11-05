# Guida rapida – come aggiornare il sito

Sito online: https://samuelebordini.github.io/BordiniSamuele-academic-cv/

## Come funziona

Il sito è fatto con Hugo (tema HugoBlox Academic CV). Tutti i contenuti sono file di testo (Markdown/YAML).
Quando fai **push sul branch `main`** su GitHub, una GitHub Action ricostruisce e pubblica il sito da sola in 1–3 minuti.
Lo stato della build lo vedi su: https://github.com/SamueleBordini/BordiniSamuele-academic-cv/actions
(icona verde = pubblicato, rossa = errore; clicca per vedere il motivo).

Per vedere le modifiche in anteprima sul tuo PC prima del push: `hugo server` nella cartella del progetto,
poi apri http://localhost:1313 (si aggiorna a ogni salvataggio).

## Dove si trova cosa

| Cosa voglio cambiare | File / cartella |
|---|---|
| CV in PDF (pulsante "Download CV") | `static/uploads/cv.pdf` – sostituisci il file, **il nome deve restare `cv.pdf`** |
| Foto profilo | `assets/media/authors/me.png` |
| Bio, ruolo, link social, interessi, istruzione, esperienze, skills, premi, lingue | `data/authors/me.yaml` |
| Sezioni della home | `content/_index.md` |
| Pagina Experience | `content/experience.md` (i dati vengono da `me.yaml`) |
| Conferenze / talk / eventi | `content/events/<nome-evento>/` |
| Pubblicazioni | `content/publications/<nome-paper>/` |
| Progetti | `content/projects/<nome-progetto>/` |
| Impostazioni generali (titolo, URL) | `config/_default/` |

## Aggiungere una conferenza / evento

1. Copia una cartella esistente in `content/events/` (es. `icra-2026`) e rinominala, es. `nome-evento-2027`.
2. Modifica `index.md` dentro la nuova cartella: `title`, `event_name`, `location`, `address`,
   `date`, `event_start`, `event_end`, `summary`, `abstract`, `tags`, `event_url`.
3. Logo/immagine: mettilo nella stessa cartella chiamandolo `featured.png` (o `featured.jpg`) – viene usato in automatico.
4. `featured: true` per metterlo in evidenza, `false` altrimenti.

## Aggiungere una pubblicazione

1. Copia una cartella in `content/publications/` (es. `alter-art`) e rinominala.
2. In `index.md` modifica `title`, `authors` (tu sei `me`), `date`, `publication`, `publication_types`
   (`article`, `paper-conference`, `preprint`…), `abstract`, `summary`, `tags`, `links` (pdf, preprint, doi…).
3. Immagine di copertina: `featured.png` / `featured.jpg` nella stessa cartella.

## Aggiungere un'esperienza, un titolo di studio o un premio

Apri `data/authors/me.yaml` e aggiungi una voce nella lista giusta (`experience`, `education`, `awards`…),
copiando una voce esistente e rispettando l'indentazione (spazi, non tab). Senza `end:` = "Present".

## Pubblicare le modifiche

Con GitHub Desktop: scrivi un messaggio → **Commit to main** → **Push origin**.
Da terminale:
```
git add .
git commit -m "Descrizione della modifica"
git push
```

## Attenzioni

- I file `.md` e `.yaml` sono sensibili all'indentazione e alle virgolette: se la build diventa rossa, di solito è lì.
- Le date vanno nel formato `'2026-10-01T00:00:00Z'` (eventi/pubblicazioni) o `2026-10-01` (in `me.yaml`).
- Nomi di cartelle senza spazi né maiuscole (es. `irim-3d-2026`).
