# Sito Impronte ODV

Prototipo del sito web per Impronte ODV — Associazione Animalosa.  
Sito statico, gratuito da ospitare, multi-pagina.

---

## 📁 Struttura dei file

```
impronte-site/
├── index.html          → Home / Chi siamo
├── adozioni.html       → Adozioni + vademecum
├── volontari.html      → Volontari + form candidatura
├── donazioni.html      → Teaming, IBAN, 5×1000
├── eventi.html         → Eventi prossimi e passati
├── contatti.html       → Contatti + form
├── styles.css          → Tutti gli stili condivisi
└── assets/
    ├── logo.png        → Logo con sfondo trasparente
    └── favicon.png     → Icona del sito nella tab del browser
```

---

## 🚀 Come mettere online il sito (GRATIS)

### Opzione 1: Netlify (consigliata — la più semplice)

1. Vai su [netlify.com](https://www.netlify.com) e registrati (gratis).
2. Dalla dashboard clicca su **"Add new site" → "Deploy manually"**.
3. **Trascina l'intera cartella `impronte-site/`** nella zona di drag-and-drop.
4. In 30 secondi avrai un URL pubblico (es. `nome-a-caso.netlify.app`).
5. Dalle impostazioni del sito puoi cambiare il dominio in qualcosa tipo `impronte-odv.netlify.app`.

### Opzione 2: GitHub Pages

1. Crea un account su [github.com](https://github.com).
2. Crea un nuovo repository pubblico.
3. Carica tutti i file di questa cartella nel repository.
4. Vai in `Settings → Pages`, imposta la sorgente su `main branch` e `/root`.
5. Dopo qualche minuto il sito sarà online su `username.github.io/nome-repository`.

### Opzione 3: Dominio personalizzato

Sia Netlify che GitHub Pages permettono di collegare un dominio personalizzato (es. `improteodv.it`) gratuitamente. Il dominio va acquistato a parte (~10€/anno da Register.it, Aruba, Namecheap).

---

## ⚙️ Cose da fare prima di andare online

### 1. Collegare i form a un servizio

I form di **volontari.html** e **contatti.html** attualmente hanno come destinazione `https://formspree.io/f/YOUR_FORMSPREE_ID`. Devi:

- **Formspree** (50 invii/mese gratis): registrati su [formspree.io](https://formspree.io), crea un form e sostituisci `YOUR_FORMSPREE_ID` con il tuo ID vero.
- Oppure **Web3Forms** (250 invii/mese gratis): vedi le istruzioni nei commenti HTML dei form.
- Oppure **Netlify Forms** (100 invii/mese gratis, solo se ospiti su Netlify): aggiungi `data-netlify="true"` al tag `<form>`.

### 2. Configurare le piattaforme di adozione

In `adozioni.html` ci sono due card:

- **Petfactor** (adozione fisica): il link è attualmente `href="#"`. Quando avrai creato l'account e caricato gli animali, sostituiscilo con l'URL pubblico della vostra pagina Petfactor.
- **MyAnimal** (adozione a distanza): il link punta già a [my-animal.it](https://www.my-animal.it) ma è generico. Quando avrai la pagina dedicata a Impronte ODV su MyAnimal, sostituisci l'URL con quello specifico.

Cerca `Petfactor` e `MyAnimal` nel file con Trova-Sostituisci per trovare tutti i punti da aggiornare (ci sono anche nella CTA finale).

### 3. Inserire le foto reali

In tutte le pagine ci sono dei box con lo sfondo a righine viola e l'icona 🐾 — sono i **placeholder per le foto**. Ognuno ha un suggerimento sul tipo di foto consigliata.

Per sostituirli:
- Salva la foto nella cartella `assets/` (es. `assets/hero.jpg`).
- Nell'HTML sostituisci il blocco `<div class="photo-placeholder">...</div>` con `<img src="assets/hero.jpg" alt="Descrizione della foto" style="width: 100%; border-radius: 28px; aspect-ratio: 4/5; object-fit: cover;">`.

### 4. Aggiornare eventi e statistiche

- In `index.html` i quattro numeri con il trattino **"—"** sono placeholder: sostituisci con i numeri reali (animali salvati, adozioni, volontari, anni attività).
- In `eventi.html` gli eventi sono di esempio: aggiorna con quelli reali o cancellali se non ne hai di programmati.

### 5. Aggiungere informativa privacy e cookie

Le pagine hanno dei link segnaposto **"Privacy"** e **"Cookie"** nel footer e nei form (`href="#"`). Per essere a norma GDPR conviene:
- Creare una pagina `privacy.html` con l'informativa (si può generare gratis su [iubenda.com](https://iubenda.com) — versione free).
- Aggiungere un banner cookie (se userai Google Analytics o simili). Soluzione gratuita: [cookieconsent](https://www.cookieconsent.com).

### 6. Orari canile

In `contatti.html` c'è il campo **"[Orari di apertura — da inserire]"**. Sostituiscilo con i giorni e gli orari in cui il canile è aperto al pubblico (o l'indicazione "solo su appuntamento").

---

## 🎨 Personalizzazioni rapide

### Cambiare i colori

In `styles.css`, nelle prime righe trovi le variabili:

```css
--purple-dark: #5b5480;
--purple: #756ea9;
--purple-light: #a493bf;
```

Cambia questi valori e si aggiorneranno ovunque nel sito.

### Cambiare i font

Sempre in `styles.css`, all'inizio c'è la riga `@import url('https://fonts.googleapis.com/css2?...')`. Puoi cambiare i font andando su [fonts.google.com](https://fonts.google.com) e sostituendo l'URL e i nomi nelle variabili `--font-display` e `--font-body`.

### Aggiungere pagine

Copia una delle pagine esistenti (es. `contatti.html`), rinominala, modifica i contenuti e aggiungi il link nel menu di tutte le altre pagine.

---

## 💡 Suggerimenti

- **Ottimizza le foto prima di caricarle**: max 1600px di larghezza, formato WebP o JPG, peso <200KB ciascuna. Strumento gratuito: [squoosh.app](https://squoosh.app).
- **SEO**: cambia i tag `<title>` e `<meta description>` in ogni pagina con testi specifici per la vostra zona geografica (es. "Canile Ancona — Impronte ODV").
- **Analytics gratuito**: [plausible.io](https://plausible.io/community-edition) (self-hosted) o Google Analytics (ma richiede banner cookie).
- **Form**: Formspree e Web3Forms hanno piani gratuiti con limiti mensili. Se superate spesso i limiti, valutate il passaggio al piano a pagamento o a Netlify Forms.

---

## 📞 Contatti configurati nel sito

- **Sede**: Via San Giovanni, 60010 Ostra Vetere (AN)
- **WhatsApp**: +39 351 494 6802
- **Email**: impronte.ass@gmail.com
- **Instagram / Facebook / TikTok**: impronte.odv
- **Teaming** (donazioni 1€/mese): https://www.teaming.net/impronteodv
- **Petfactor** (adozioni fisiche): da configurare
- **MyAnimal** (adozioni a distanza): https://www.my-animal.it
- **IBAN**: IT85T0306909606100000407288
- **5×1000 / CF**: 92057820422

Se qualche contatto cambia, cerca il vecchio valore con "Trova" nell'editor di testo e sostituiscilo in tutte le pagine.

---

Buon viaggio a Impronte ODV! 🐾
