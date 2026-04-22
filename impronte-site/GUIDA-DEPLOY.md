# Guida: mettere il sito online con Netlify + GitHub

Questa guida ti accompagna passo-passo dalla cartella di file sul tuo computer fino al sito pubblicato online, con la possibilità di aggiornarlo nel tempo.

**Tempo stimato totale**: 30-45 minuti la prima volta. Dopo sarà tutto questione di pochi click.

**Costo**: zero. Ora e sempre.

---

## Perché GitHub e non solo Netlify?

- **Solo Netlify (drag & drop)**: veloce, ma ogni modifica significa aprire file HTML a mano e ritrascinare la cartella
- **Netlify + GitHub**: stesso risultato visibile agli utenti, ma gli aggiornamenti diventano più semplici (modifichi un file sul browser di GitHub e il sito si aggiorna da solo) e apre la porta al pannello di modifica Decap CMS che configureremo dopo

In pratica: **con GitHub puoi modificare il sito da qualsiasi computer, senza avere i file in locale**. Per un'associazione con più volontari che potrebbero dare una mano è molto comodo.

---

## PARTE 1 — Crea un account GitHub (5 minuti)

1. Vai su [github.com](https://github.com)
2. Clicca **"Sign up"** in alto a destra
3. Inserisci: email (meglio quella dell'associazione: `impronte.ass@gmail.com`), una password forte, uno username (es. `impronte-odv`)
4. Risolvi il puzzle anti-bot
5. GitHub ti invia un codice via email: inseriscilo
6. Alla domanda "How many team members?" scegli **"Just me"**
7. Alla domanda "What features?" puoi non selezionare nulla
8. Seleziona il piano **Free**
9. Fatto. Sei nella dashboard di GitHub.

---

## PARTE 2 — Crea un repository per il sito (3 minuti)

Un "repository" (o "repo") è una cartella di progetto su GitHub.

1. In alto a destra clicca il **"+"** → **"New repository"**
2. Compila così:
   - **Repository name**: `impronte-sito` (o come preferisci, senza spazi)
   - **Description**: `Sito web di Impronte ODV` (opzionale)
   - **Public** o **Private**: scegli **Public**. Il codice del sito non è segreto e ti serve public per usare Netlify free senza limiti
   - **NON** spuntare "Add a README file" (lo abbiamo già noi)
   - **NON** aggiungere `.gitignore` né license per ora
3. Clicca **"Create repository"**
4. Ti trovi su una pagina con istruzioni tecniche: **ignorale tutte**, useremo un metodo più semplice.

---

## PARTE 3 — Carica i file del sito su GitHub (10 minuti)

Dallo zip che ti ho preparato, **scompatta il contenuto sul tuo computer** ottenendo la cartella `impronte-site` con dentro:
- `index.html`, `adozioni.html`, `volontari.html`, `donazioni.html`, `eventi.html`, `contatti.html`
- `styles.css`
- `README.md`
- la cartella `assets/` (con `logo.png`, `favicon.png` e la sottocartella `photos/`)

**Metodo drag-and-drop su GitHub** (più semplice, niente da installare):

1. Sulla pagina del tuo repository vuoto, sotto "Quick setup" c'è un link **"uploading an existing file"**. Cliccalo.
2. Si apre una pagina con un riquadro "Drag files here". 
3. **Seleziona tutto il contenuto della cartella `impronte-site`** (i file HTML, il CSS, il README e la cartella `assets`) e trascinali nel riquadro.
4. Attendi che GitHub carichi tutto (può servire un minuto per le foto).
5. In fondo alla pagina, nel campo "Commit changes":
   - Titolo: `Primo caricamento del sito`
   - Messaggio: puoi lasciarlo vuoto
6. Lascia selezionata l'opzione **"Commit directly to the main branch"**
7. Clicca **"Commit changes"**.

Dopo qualche secondo vedrai la homepage del repo piena dei file del sito. Perfetto, ci siamo.

> **Nota sulla cartella assets/photos**: se il drag-and-drop non preserva la struttura delle sottocartelle, carica prima i file al primo livello (HTML, CSS, README) e poi per la cartella `assets` segui questa strada alternativa:
> 
> - Dal repo clicca **"Add file" → "Create new file"**
> - Nel nome file scrivi `assets/photos/.gitkeep` (crea la struttura di cartelle)
> - Commit
> - Poi entra in `assets/photos/` cliccandoci sopra e usa "Add file → Upload files" per caricare tutte le foto

---

## PARTE 4 — Crea account Netlify (3 minuti)

1. Vai su [app.netlify.com](https://app.netlify.com)
2. Clicca **"Sign up"**
3. Scegli **"GitHub"** come metodo di registrazione (importante: collega subito GitHub, non usare email)
4. Autorizza Netlify ad accedere al tuo GitHub
5. Segui la procedura guidata iniziale (puoi saltare/ignorare le domande su "team name" mettendo qualcosa tipo "impronte-odv")

---

## PARTE 5 — Collega il repository a Netlify (5 minuti)

1. Nella dashboard Netlify, clicca **"Add new site" → "Import an existing project"**
2. Scegli **"Deploy with GitHub"**
3. Netlify chiede il permesso di leggere i tuoi repo: clicca **"Configure Netlify on GitHub"** → **"Install"** (o "Save" se ti chiede di scegliere quali repo, scegli "Only select repositories" → seleziona solo `impronte-sito`)
4. Torni automaticamente su Netlify. Ora vedi la lista dei tuoi repo GitHub: **clicca `impronte-sito`**
5. Nella pagina "Site settings":
   - **Branch to deploy**: `main` (è già così)
   - **Build command**: **LASCIA VUOTO** (non abbiamo nessun processo di build)
   - **Publish directory**: **LASCIA VUOTO** oppure scrivi `.` (un punto)
6. Clicca **"Deploy site"** (o "Deploy impronte-sito")

Netlify inizia a processare. Dopo 30-60 secondi vedrai **"Published"** con un URL tipo `random-name-abc123.netlify.app`.

Apri l'URL in una nuova scheda: il sito è online! 🎉

---

## PARTE 6 — Personalizza l'URL (2 minuti)

L'URL `random-name-abc123.netlify.app` non è bello. Cambialo:

1. Dal pannello del sito su Netlify, **Site configuration** → **Change site name**
2. Inserisci `impronte-odv` (o `impronteodv` se l'altro fosse già preso)
3. Salva.

Il sito è ora raggiungibile su **`impronte-odv.netlify.app`**.

---

## PARTE 7 — Configura il form dei volontari e dei contatti (10 minuti)

I moduli del sito al momento non funzionano: vanno collegati a un servizio che riceve le email per te. La scelta migliore su Netlify è **Netlify Forms**, 100 invii/mese gratis.

### Attivarlo:

1. Apri il file `volontari.html` direttamente su GitHub (dal tuo repo, clicca il file)
2. Clicca l'icona matita in alto a destra per modificarlo
3. Trova la riga:
   ```html
   <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST" id="volontariForm">
   ```
4. Sostituiscila con:
   ```html
   <form name="volontari" method="POST" data-netlify="true" id="volontariForm">
     <input type="hidden" name="form-name" value="volontari">
   ```
5. Scorri in fondo, nel "Commit changes" scrivi `Attivazione Netlify Forms volontari`
6. Clicca **Commit changes**

Ripeti gli stessi passaggi per `contatti.html`, cambiando "volontari" con "contatti".

In 30 secondi Netlify ridistribuisce il sito e i form funzionano.

### Vedere i messaggi ricevuti:

Dal pannello Netlify del sito → **Forms** → vedrai i submit che arrivano. Puoi anche impostare una notifica email a `impronte.ass@gmail.com`:

1. Forms → **Settings and usage**
2. Scorri a **Form notifications** → **Add notification** → **Email notification**
3. Metti `impronte.ass@gmail.com` come destinazione

Ogni volta che qualcuno compila un form arriverà una mail direttamente alla casella dell'associazione.

---

## PARTE 8 — Come aggiornare il sito nel tempo

### Modifiche semplici (un evento, un numero, una frase)

1. Vai su [github.com](https://github.com), login, apri il repo `impronte-sito`
2. Clicca il file da modificare (es. `eventi.html`)
3. Icona matita → modifica il testo
4. Scorri in fondo → **Commit changes** (dai un titolo tipo "Aggiunto evento XYZ")
5. Entro 1 minuto il sito è aggiornato su `impronte-odv.netlify.app`

### Aggiungere una nuova foto

1. Sul repo, apri la cartella `assets/photos`
2. **Add file → Upload files** → trascina la foto
3. Commit
4. Modifica l'HTML che deve usare quella foto (aggiungendo un tag `<img>`)

### Aggiungere/modificare un evento: tutorial pratico

Apri `eventi.html` e cerca il blocco di un evento esistente, ad esempio:

```html
<div class="event-card">
  <div class="event-date">
    <div class="day">22</div>
    <div class="month">APR</div>
    <div class="year">2026</div>
  </div>
  <div class="event-details">
    <h3>Titolo evento</h3>
    ...
```

Copia tutto il blocco, incollalo sopra o sotto, modifica i dati. Non serve toccare altro.

---

## Problemi comuni e soluzioni

### "Il sito non si vede" dopo il deploy

- Aspetta 1-2 minuti: Netlify a volte ci mette un po'
- Vai nella sezione **Deploys** del pannello Netlify: se vedi il pallino **rosso**, c'è un errore. Clicca il deploy per vedere il log.
- Errore più comune: **Publish directory** sbagliato. Nelle impostazioni del sito (Build & deploy → Build settings), metti `.` (un punto) come Publish directory.

### Le immagini non si vedono sul sito online

- Controlla che nel tuo repo GitHub esista davvero la cartella `assets/photos/` con dentro le foto
- Apri `index.html` sul repo e verifica che i percorsi nelle `<img src="...">` corrispondano ai file che hai caricato (differenza tra `Photo.jpg` e `photo.jpg` conta su Netlify)

### Ho modificato un file ma il sito non cambia

- Il deploy richiede 30-60 secondi: aspetta e ricarica la pagina col CTRL+F5 (svuota la cache del browser)
- Controlla su Netlify → Deploys se c'è un nuovo deploy "Published" dopo la tua modifica
- Se non c'è, vai su **Deploys** → **Trigger deploy** → **Deploy site** per forzare manualmente

### Voglio accettare aiuto da un altro volontario

Su GitHub, dal repo: **Settings** → **Collaborators** → **Add people** → inserisci il loro username GitHub. Potranno modificare i file direttamente.

---

## Recap dei tuoi accessi

Quando finisci, tieni a portata di mano:

- **GitHub**: `github.com/tuousername/impronte-sito` (o il nome che hai scelto)
- **Netlify**: `app.netlify.com` con login via GitHub
- **Sito pubblicato**: `impronte-odv.netlify.app`
- **Form submissions**: `app.netlify.com` → il tuo sito → Forms

---

## Passo successivo (opzionale): Decap CMS

Una volta che sei a tuo agio con questa configurazione, possiamo aggiungere **Decap CMS**: un pannello web per modificare eventi, testi e foto senza toccare l'HTML, raggiungibile da `impronte-odv.netlify.app/admin`.

Quando vuoi attivarlo, scrivimelo e preparo la configurazione su misura.

---

## Hai bloccato in un passaggio?

Fammi sapere in quale e ti guido nello specifico. Tipicamente i punti dove ci si può impantanare sono:
- Il drag-and-drop su GitHub della cartella `assets` (se non preserva la struttura)
- La schermata "Site settings" su Netlify (se lasci qualcosa di sbagliato)
- L'attivazione dei form (se l'HTML non viene modificato correttamente)

Per ognuno di questi, una foto dello schermo è sufficiente a farti risolvere in 2 minuti.

Buon lavoro! 🐾
