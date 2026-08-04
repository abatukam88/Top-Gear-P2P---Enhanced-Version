# 🏎️ Top Gear P2P — Enhanced Version

Racing / Demolition Derby **multiplayer serverless** che gira interamente nel browser.

Progetto fork-canale da un tutorial YouTube, migliorato in questo repository.

## 🔥 GIOCA ORA: Abisso Enhanced Version
### 👉 https://sanciopanza88.github.io/Abisso-Enhanced-Version/

Gioca anche a Top Gear P2P Enhanced: https://sanciopanza88.github.io/Top-Gear-P2P---Enhanced-Version/

Nessun server dedicato: ogni browser è sia client che host. I giocatori si trovano in
rete tramite **[Trystero](https://github.com/dmotz/trystero)** (WebRTC), usando i tracker
BitTorrent come sistema di signaling (stile WebTorrent) — non c'è alcun trasferimento di
file torrent, solo scambio degli indirizzi per la connessione P2P. Basta aprire lo stesso
gioco — su un hosting statico gratuito (Netlify, GitHub Pages, ecc.) o anche come file
locale — e usare lo **stesso nome di stanza** per trovarsi.

---

## Indice

- [Cosa c'è nella cartella](#cosa-cè-nella-cartella)
- [Come si gioca](#come-si-gioca)
- [Differenze rispetto all'originale](#differenze-rispetto-alloriginale-top-gear-p2phtml)
- [Regole del Derby](#regole-del-derby-gioco)
- [Comandi](#comandi-tasti-e-azioni)
- [Animazioni ed effetti visivi](#animazioni-ed-effetti-visivi)
- [Nota tecnica](#nota-tecnica)
- [License / credits](#license--credits)

---

## Cosa c'è nella cartella

| File / cartella     | Cosa è |
|----------------------|--------|
| `index.html`         | **Versione migliorata** (questa): racing F1 + modalità Destruction Derby |
| `top-gear-p2p.html`  | Progetto **originale** (dallo youtuber), solo racing F1 |
| `auto/`               | Sprite delle 10 auto normali (F1) |
| `auto derby/`        | Sprite delle 10 auto "demo" usate nel Derby |
| `README.md`          | Questo file |

---

## Come si gioca

1. Metti il file su un hosting statico qualsiasi (o apri `index.html` in locale).
2. Digita un nome, scegli l'auto e lo **schema di guida** (tastiera / tastiera+mouse / touch).
3. Inserisci un **codice stanza** (es. `FESTA`) — gli amici devono usare lo stesso codice.
4. Spunta **"Modalità Destruction Derby"** per cambiare modalità (arena smash-up):
   il primo che entra diventa **host** e decide quando partire col pulsante **🏁 VIA**.
5. **Scendi in pista.**

> Chi entra a gara già iniziata diventa **osservatore** di quella gara e torna pilota
> dal round successivo (pulsante **RIGIOCA**).

---

## Differenze rispetto all'originale (`top-gear-p2p.html`)

| Funzionalità | Originale (YouTube) | Enhanced (`index.html`) |
|---|:---:|:---:|
| Gara F1 multiplayer P2P, campionato a stagione, griglia, osservatori | ✅ | ✅ |
| Danni gomme/frenata/batteria/box + riparazioni, DRS, Boost | ✅ | ✅ |
| Chat testuale e vocale P2P | ✅ | ✅ |
| Semaforo di partenza con luci | ✅ | ✅ (riusato anche nel derby) |
| **Modalità "Destruction Derby"** | ❌ | ✅ |
| **4 arene derby** tematiche (Landa di Ferro, Deserto di Sassi, Officina Junk, Esagono di Ghiaia) con decori ispirati ad arene vere | ❌ | ✅ |
| **10 auto demo** per il derby (`auto derby/*`) | ❌ | ✅ |
| **Lobby di attesa + pulsante "VIA" dell'host** (niente start automatico) | ❌ | ✅ |
| **IA bot** che convergono sul gruppo e speronano di proposito, con personalità diverse | ❌ | ✅ |
| **Meteo completo** (sole / pioggia leggera/forte con gocce e schizzi / notte con fari e stelle / nebbia volumetrica) | ❌ | ✅ |
| **Audio dedicati**: motore, schianti, esplosioni, colpi al muro, beep semaforo | Parziale | ✅ |
| **Effetti terreno**: fango/ghiaia che sporca le auto col tempo, zolle che schizzano | ❌ | ✅ |
| Barriera pneumatici, pozzanghere, torri faro, "X" centrale nelle arene | ❌ | ✅ |
| Fine gara: **ultima auto in piedi vince** + classifica + **RIGIOCA immediato** | ❌ | ✅ |
| Robustezza: protezioni anti-NaN e render loop infallibile (niente freeze dopo la vittoria) | ❌ | ✅ |

---

## Regole del Derby (gioco)

- Partono **10 macchine** sul perimetro, puntate verso il centro.
- Danno: urti col muro + scontri tra auto (dosato per far durare le gare).
- **L'ultima auto ancora in piedi vince.** A tempo scaduto si decide per punteggio.
- Muoversi sul terreno sporca le carrozzerie e fa volare zolle di terra.
- Avvio a semaforo (5 luci rosse → tutte spente = via).

---

## Comandi (tasti e azioni)

> Lo **schema di guida** si scelgono al momento della creazione del pilota:
> **tastiera**, **tastiera+mouse** (il mouse funziona come un volante) oppure **touch** (stick virtuale).

| Input | Cosa fa |
|-------|---------|
| `W` / `↑` | Accelera |
| `S` / `↓` | Freno / retromarcia |
| `A` / `←` | Sterza a sinistra |
| `D` / `→` | Sterza a destra |
| `Shift` | Apri **DRS** (ala mobile: più velocità in rettilineo, solo nelle zone DRS) |
| `Spazio` | **Boost** (slancio temporaneo, riempie una barra) |
| `Invio` | Apri la chat testuale (scrivi e invia) |
| Mouse | In modalità "tastiera+mouse" muove l'auto come un volante |
| Touch | Joystick virtuale a sinistra (accelerazione/freno/boost/DRS) |
| Rotellina del mouse sul campo | Zoom avanti/indietro della vista |
| Pulsante `🌦️` in gara | Cambia **meteo** istantaneo (Sole → Pioggia leggera → Forte → Notte → Nebbia) |
| Pulsante `🏆` | Mostra/nasconde la classifica live |

### Nel Derby

| Input | Cosa fa |
|---|---|
| `W`/`S`/`A`/`D` (o frecce) | Muove l'auto demo (accelera, sterza, retromarcia) |
| `Spazio` | Boost per schiantarti più forte |
| `Shift` | Semi-DRS / aumento velocità |
| Pulsante **🏁 VIA** | Solo l'**host**: fa partire la gara dal semaforo |
| Pulsante **RIGIOCA** | Fa partire un nuovo derby subito, senza ricaricare la pagina |
| Pulsante **TORNA AL MENU** | Ricarica la pagina e torna al menu |

> I tasti valgono sia in F1 che nel Derby; nella modalità **Derby**, il semaforo e la
> partenza sincrona valgono per tutti i piloti connessi.

---

## Animazioni ed effetti visivi

Ogni condizione meteo/evento ha il suo pacchetto di animazioni. Le voci in **grassetto**
sono le più appariscenti.

### ☀️ Sole

| Effetto | Descrizione |
|---|---|
| **Disco solare luminoso** | Palla di luce in alto a destra con alone radiale, senza raggi volumetrici fastidiosi |
| **Caldo ambientale** | Tonalità dorata su tutta la scena + bagliore basso sul suolo |
| **Nuvole volumetriche** | Nuvole soffici illuminate dal sole, movimento lento con ombra interna |
| **Crowd** | Il pubblico agita le braccia e ondeggia (sincronizzato col tempo dell'animazione) |

### 🌦️ Pioggia leggera

| Effetto | Descrizione |
|---|---|
| **Cielo plumbeo** | Gradiente grigio-scuro su tutto lo schermo |
| **Gocce a 3 strati** | Pioggia su tre profondità (puntini corti in lontananza → strisce lunghe in primo piano) |
| **Increspature** | Cerchi in espansione sulle pozzanghere con macchia interna luminosa |
| **Pozzanghere** | Macchie d'acqua statiche con riflesso del cielo sul tracciato |
| **Asfalto bagnato** | Banda riflessa nella parte bassa + fari accesi delle auto |
| **Aderenza ridotta** | L'aderenza delle gomme cala (effetto di gioco, non solo visivo) |

### ⛈️ Pioggia forte (tempesta)

| Effetto | Descrizione |
|---|---|
| **Pioggia intensa** | Come la pioggia leggera ma più densa (380 gocce, più lunghe e luminose) |
| **Fulmini** | Bagliori a tutto schermo, ramificazioni luminose con alone e riverbero (casuali) |
| **Schizzi e vento** | Spruzzi d'acqua e folate che piegano la pioggia |
| **Splash alle ruote** | In curva ad alta velocità l'auto solleva scie di pioggia |

### 🌙 Notte

| Effetto | Descrizione |
|---|---|
| **Cielo stellato** | Cielo scuro con stelle e luna luminosa (disco chiaro in alto) |
| **Fari delle auto** | Fasci di luce, pool di luce sul manto stradale, luci posteriori rosse |
| **Torri faro** | Torri di illuminazione con fascio di luce sul tracciato/arena |
| **Lampioni e semaforo** | Lampioni lungo la pista + semaforo acceso |

### 🌫️ Nebbia

| Effetto | Descrizione |
|---|---|
| **Light shafts** | Colonne di luce che filtrano attraverso la coltre di nebbia |
| **5 banchi di nebbia** | Strati in parallasse a velocità diverse per dare profondità |
| **Nebbiolina rasente** | Strato basso e veloce vicino al suolo |
| **Vignettatura bianca** | Bordi lattiginosi che sfumano verso il centro |

### 🏆 Cartellone Derby (jumbotron)

| Effetto | Descrizione |
|---|---|
| **Trofeo disegnato a mano** | Trofeo dorato con gradiente (nessuna emoji) e raggi pulsanti |
| **Fondo scuro con doppio bordo oro** | Angoli arrotondati + ombra esterna per staccarsi dal campo |
| **Scritta "DERBY"** | Lettera per lettera, spaziatura animata, gradiente oro e glow |
| **Sottotitolo** | "DISTRUGGI I TUOI AVVERSARI" (o "GARA FINITA") con effetto neon cyan |
| **Animazione d'entrata** | Bounce (scale 0.8→1 + fade-in) + scintillio diagonale |

### 💥 Effetti di schianto / gara

| Effetto | Descrizione |
|---|---|
| **Semaforo di partenza** | In F1 e nel Derby: 5 luci e beep |
| **Toast di gara** | Nel derby: messaggi "FUORI:", "COLPO:" in tempo reale |
| **Auto distrutta** | Sprite scurito + fumo nero dal cofano + brace leggera (niente cerchi/quadrati generici) |
| **Tracce di gomma** | Frenate e curve ad alta velocità lasciano segni scuri sull'asfalto |
| **Fango/ghiaia** | L'auto si sporca con chiazze di terra; zolle che volano se esci di pista |
| **Boost** | Scia luminosa + scintille dietro l'auto |
| **Danno** | Fumo dal cofano oltre il 60% di danno |
| **Camera shake** | Lo schermo trema sugli impatti forti |
| **Pioggia dinamica** | Schizzi e riflessi che reagiscono alla velocità dell'auto |

> Il **meteo** si può scegliere sia in fase di creazione stanza sia in gara col pulsante
> `🌦️`: la pioggia riduce l'aderenza (approssimazione fisica), il resto è pura animazione.

---

## Nota tecnica

- **Networking:** `https://esm.sh/trystero@0.21.1/torrent` — la stanza viene creata con
  `joinRoom({appId}, roomCode)`; **stesso `appId`** per modalità F1 e Derby, stessa stanza.
- **Nessun database:** la classifica del campionato resta viva finché almeno un browser
  rimane collegato alla stanza.
- **Testing:** per il testing headless del progetto sono disponibili diversi script Node
  (smoke test + verifica errori) — eseguili se necessario prima di una modifica.

---

## License / credits

Modifiche e migliorie a parte, ispirazione dal canale YouTube che ha creato il gioco
originale (`top-gear-p2p.html`). Maggiori info nel repository:
**https://github.com/abatukam88/Top-Gear-P2P---Enhanced-Version**
