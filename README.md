[README.md](https://github.com/user-attachments/files/30663151/README.md)
# Top Gear P2P — Enhanced Version

Racing / Demolition Derby **multiplayer serverless** che gira interamente nel browser.

Progetto fork-canale da un tutorial su YouTube e migliorato qui:
**https://github.com/abatukam88/Top-Gear-P2P---Enhanced-Version**

Nessun server dedicato: ogni browser è sia client che host, ed i giocatori si trovano in
rete tramite **Trystero** (WebRTC) attraverso torrent straddle (stile WebTorrent). Basta aprire
lo stesso file — in hosting statico gratis (Netlify, GitHub Pages, ecc.) o anche come file
locale — e mettere lo **stesso nome di stanza** per trovarsi.

---

## Cosa c'è nella cartella

| File / cartella        | Cosa è |
|------------------------|--------|
| `index.html`           | **Versione migliorata** (questa): racing F1 + modalità Destruction Derby |
| `top-gear-p2p.html`    | Progetto **originale** (dallo youtuber), solo racing F1 |
| `auto/`                | Sprite delle 10 auto normali (F1) |
| `auto derby/`          | Sprite delle 10 auto "demo" usate nel Derby |
| `README.md`            | Questo file |

---

## Come si gioca

1. Metti il file su un hosting statico qualsiasi (o apri `index.html` da locale).
2. Digita un nome, scegli la macchina e lo **schema di guida** (tastiera / tastiera+mouse / touch).
3. Metti un **codice stanza** (es. `FESTA`). Amici: stesso codice.
4. Spunta **"Modalità Destruction Derby"** per cambiare modalità (arena smash-up) —
   il primo che entra è l'**host** e decide quando partire col pulsante **🏁 VIA**.
5. **SCENDI IN PISTA**.

> Chi arriva a gara già iniziata diventa **osservatore** di quella gara e viene pilota
> dal round successivo (pulsante RIGIOCA).

---

## Differenze rispetto all'originale (`top-gear-p2p.html`)

| Funzionalità | Originale (YouTube) | Enhanced (`index.html`) |
|--------------|:-------------------:|:-----------------------:|
| Gara F1 multiplayer P2P, campionato a stagione, griglia, osservatori | ✅ | ✅ |
| Danni gomme/frenata/batteria/box + riparazioni, DRS, Boost | ✅ | ✅ |
| Chattata testuale e vocale P2P | ✅ | ✅ |
| Semaforo di partenza con luci | ✅ | ✅ (riusato anche nel derby) |
| **Modalità "Destruction Derby"** | ❌ | ✅ |
| **4 arene derby** tematiche (Landa di Ferro, Deserto di Sassi, Officina Junk, Esagono di Ghiaia) con decori ispirati ad arene vere | ❌ | ✅ |
| **10 auto demo** per il derby (auto derby/*) | ❌ | ✅ |
| **Lobby di attesa + pulsante "VIA" dell'host** (niente start automatico) | ❌ | ✅ |
| **IA bots** che convergono sul gruppo e vanno a sbattere di proposito, con personalità diverse | ❌ | ✅ |
| **Meteo completo** (sole / pioggia leggera/forte con gocce + schizzi / notte con fari e stelle / nebbia volumetrica) | ❌ | ✅ |
| **Audio specifici**: motore, schianti, esplo, colpi al muro, beep semaforo | parziale | ✅ |
| **Effetti terreno**: fango/ghiaia che sporca le auto con il tempo e zolle che schizzano | ❌ | ✅ |
| Barriera pneumatici, pozzanghere, torri faro, "X" centrale alle arene | ❌ | ✅ |
| Fine gara: **ultima macchina in piedi vince** + classifica + **RIGIOCA immediato** | ❌ | ✅ |
| Robustezza: protezioni anti-NaN e render loop infallibile (niente freeze dopo la vittoria) | ❌ | ✅ |

---

## Regole del Derby (gioco)

- Partono **10 macchine** sul perimetro, puntate verso il centro.
- Danno: urti muro + scontri tra auto (dosato in modo che le gare durino).
- **L'ultima auto ancora in piedi vince.** A tempo scaduto si valuta per punteggio.
- Sui tuoi terreni spostarsi sporca le carrozzerie e fa volare zolle di terra.
- Avvio a semaforo (5 luci rosse → tutte spente = VIA).

---

## Comandi (tasti e azioni)

> Gli **schemi di guida** si scelgono al momento della creazione del pilota:
> **tastiera**, **tastiera+mouse** (guida con il mouse come un volante) oppure **touch** (stick virtuale).

| Input | Cosa fa |
|-------|---------|
| `W` / `↑` | Accelera |
| `S` / `↓` | Freno / retromarcia |
| `A` / `←` | Sterza a sinistra |
| `D` / `→` | Sterza a destra |
| `Shift` | Apri **DRS** (ala mobile: più velocità in rettilineo, solo nelle zone DRS) |
| `Spazio` | **Boost** (slancio temporaneo, riempie una barra) |
| `Invio` | Apri la chat testuale (riscrivi per inviare) |
| Mouse | In modalità "tastiera+mouse" muove l'auto come un volante |
| Touch | Joystick virtuale a sinistra (accel/freno/boost/DRS) nei controlli touch |
| Ruota del mouse sul campo | Zoom avanti/indietro della vista |
| Pulsante `🌦️` in gara | Cambia **meteo** istantaneo (Sole → Pioggia leggera → Forte → Notte → Nebbia) |
| Pulsante `🏆` | Mostra/nascondi la classifica live |

### Nel Derby

| Input | Cosa fa |
|---|---|
| `W`/`S`/`A`/`D` (o frecce) | Muove la macchina da demo (accelera, sterza, retromarcia) |
| `Spazio` | Boost per schiantarti più forte |
| `Shift` | Semi-DRS / aumento velocità |
| Pulsante **🏁 VIA** | Solo l'**host**: fa partire la gara dal semaforo |
| Pulsante **RIGIOCA** | Riparte un nuovo derby subito, senza ricaricare la pagina |
| Pulsante **TORNA AL MENU** | Ricarica la pagina e torna al menu |

> I tasti valgono sia in F1 che nel Derby; nella modalità **Derby** i tasti del semaforo
> e la partenza sincrona valgono per tutti i piloti.

---

## Animazioni ed effetti visivi

Ogni condizione meteo/avvenimento ha il suo pacchetto di animazioni. Ecco cosa mostra (le voci in **grassetto** sono le più appariscenti):

### ☀️ Sole
| Effetto | Descrizione |
|---|---|
| **Disco solare luminoso** | Palla di luce in alto a destra con alone radiale, senza raggi volumetrici fastidiosi |
| **Caldo ambientale** | Tonalità dorata che avvolge tutta la scena + bagliore basso sul suolo |
| **Nuvole volumetriche** | Nuvole soffici illuminate dal sole che si muovono lentamente con ombra interna |
| **Crowd** | Il pubblico agita le braccia e ondeggia (di pari passo col tempo dell'animazione) |

### 🌦️ Pioggia leggera
| Effetto | Descrizione |
|---|---|
| **Cielo plumbeo** | Gradiente grigio-scuro su tutto lo schermo |
| **Gocce a 3 strati** | Pioggia con strati lontano/medio/vicino per profondità (puntini corti → strisce lunghe) |
| **Increspature** | Cerchi in espansione sulle pozzanghere con macchia interna luminosa |
| **Pozzanghere** | Macchie d'acqua statiche con riflesso del cielo sul tracciato |
| **Asfalto bagnato** | Banda riflessa nella parte bassa + fari accesi delle auto |
| **Aderenza ridotta** | L'aderenza delle gomme cala (effetto di gioco non solo visivo) |

### ⛈️ Pioggia forte (tempesta)
| Effetto | Descrizione |
|---|---|
| **Pioggia intensa** | Tutto come la pioggia leggera ma più denso (380 gocce, più lunghe e luminose) |
| **Fulmini** | Bagliori a tutto schermo, ramificazioni luminose con alone e riverbero (casuali) |
| **Schizzi e vento** | Spruzzi d'acqua e folate che piegano la pioggia |
| **Splash alle ruote** | In curva ad alta velocità l'auto solleva scie di pioggia |

### 🌙 Notte
| Effetto | Descrizione |
|---|---|
| **Cielo stellato** | Cielo scuro con stelle e luna luminosa (disco chiaro in alto) |
| **Fari delle auto** | Fasci di luce, pool di luce stradale e luci posteriori rosse accese |
| **Torri faro** | Torri di illuminazione con fascio di luce sul tracciato/arena |
| **Lampioni e semaforo** | Lampioni luminosi lungo la pista + semaforo acceso |

### 🌫️ Nebbia
| Effetto | Descrizione |
|---|---|
| **Light shafts** | Colonne di luce che filtrano attraverso la coltre |
| **5 banchi di nebbia** | Strati di nebbia in parallasse a velocità diverse per profondità |
| **Nebiolina rasente** | Strato basso e veloce vicino al suolo |
| **Vignettatura bianca** | Bordi lattiginosi che sfumano verso il centro |

### 🏆 Cartellone Derby (jumbotron)
| Effetto | Descrizione |
|---|---|
| **Trofeo disegnato a mano** | Trofeo in oro con gradiente (niente emoji) e raggi che pulsano |
| **Fondo scuro con doppio bordo oro** | Angoli arrotondati + ombra esterna per staccarsi dal campo |
| **Scritta "DERBY"** | Lettera per lettera con spaziatura animata, gradiente oro e glow |
| **Sottotitolo** | "DISTRUGGI I TUOI AVVERSARI" (o "GARA FINITA") con effetto neon cyan |
| **Animazione d'entrata** | Bounce (scale 0.8→1 + fade-in) + scintillio diagonale |

### 💥 Effetti nello schianto / gara
| Effetto | Descrizione |
|---|---|
| **Semaforo di partenza** | In F1 e nel Derby: 5 luci e beep |
| **Toast di gara** | Nel derby: "FUORI:", "COLPO:" in tempo reale |
| **Auto distrutta** | Lo sprite si scurisce e basta + fumo nero che sale dal cofano + brace leggera (niente cerchi/quadrati) |
| **Tracce di gomma** | Frenate e curve in velocità lasciano segni scuri sull'asfalto |
| **Fango/ghiaia** | L'auto si sporca con chiazze di terra e zolle che volano se esci di pista |
| **Boost** | Scia luminosa + scintille dietro l'auto |
| **Danno** | Fumo dal cofano oltre il 60% di danno |
| **Camera shake** | Lo schermo trema sugli impatti forti |
| **Pioggia dinamica** | Schizzi e riflessi che reagiscono alla velocità dell'auto |

> Il **meteo** è selezionabile sia al momento della creazione sia in gara con il pulsante `🌦️`:
> la pioggia riduce l'aderenza (approssimazione fisica), tutto il resto è pura animazione.

---

## Nota tecnica

- Networking: `https://esm.sh/trystero@0.21.1/torrent` — stanza creata con
  `joinRoom({appId}, roomCode)`; **stesso `appId`** in modalità F1 e Derby, stessa stanza.
- Niente database: la classifica del campionato è tenuta viva finché almeno un
  browser rimane collegato alla stanza.
- Per il testing headless del progetto sono disponibili diversi script Node
  (smoke + verifica errori) — riprodurli se necessario.

---

## License / credits
Modifiche e migliorie fotografiche a parte: ispirazione dal canale che ha creato il
gioco originale (progetto `top-gear-p2p.html`). Maggiori info nel repo:
**https://github.com/abatukam88/Top-Gear-P2P---Enhanced-Version**
