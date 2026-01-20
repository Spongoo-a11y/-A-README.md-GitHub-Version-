
# 🟦 **A) README.md (GitHub‑Version)**  
*(Du kannst das exakt so in dein Repository packen.)*

---

# **ΕΥΘΗΝΙΑ (ETHN) – Smart Contract Dokumentation**

## 🔹 Überblick

**ΕΥΘΗΝΙΑ (ETHN)** ist ein deflationärer BEP‑20 Token auf der Binance Smart Chain, entwickelt mit Fokus auf:

- **Sicherheit**  
- **Transparenz**  
- **Fairness**  
- **Anti‑MEV‑Mechanismen**  
- **Zeitlich begrenzte Admin‑Kontrolle**  

Der Contract wurde vollständig audit‑bereinigt und folgt strengen Sicherheits‑ und Tokenomics‑Standards.

---

## 🔹 Contract‑Adresse  
*(Wird nach Deployment ergänzt)*

---

## 🔹 Hauptmerkmale

### ✔️ **Deflationärer Mechanismus**
- 7 % Transaktionssteuer  
- 6 % Marketing  
- 1 % Burn  
- Burn geht direkt an `0x000…dEaD`

### ✔️ **Anti‑MEV Auto‑Swap**
- Swap nur bei **Verkäufen**  
- **Randomisierte Swap‑Schwelle**  
- **Block‑Cooldown** zwischen Swaps  
- Schutz vor Sandwich‑Attacken

### ✔️ **Fair‑Launch‑Sicherheit**
- Trading erst nach `launch()` möglich  
- Owner ist von Fees ausgenommen (für LP‑Aufbau)

### ✔️ **Zeitlich begrenzte Admin‑Kontrolle**
- **Blacklist nur 60 h** nach Launch möglich  
- **Pause nur 7 Tage** nach Launch möglich  
- Danach sind beide Funktionen **permanent deaktiviert**

### ✔️ **Keine Backdoors**
- Kein Mint  
- Kein Owner‑Transfer  
- Kein versteckter Fee‑Bypass  
- Router kann nach Launch **nicht** geändert werden  
- Keine Upgradability (kein Proxy)

### ✔️ **BEP‑20 Standard**
- Vollständig kompatibel mit Wallets, DEXs und Explorern  
- `transferFrom` korrekt implementiert (Allowance‑Bug behoben)

---

## 🔹 Tokenomics

| Kategorie | Wert |
|----------|------|
| Name | ΕΥΘΗΝΙΑ |
| Symbol | ETHN |
| Decimals | 18 |
| Total Supply | 10 000 ETHN |
| Burn bei Deployment | 4 500 ETHN |
| Owner‑Supply | 5 500 ETHN |
| Steuer | 7 % |
| Marketing | 6 % |
| Burn | 1 % |

---

## 🔹 Sicherheit & Audit‑Features

### ✔️ Reentrancy‑Schutz  
`nonReentrant` + interne Swap‑Lock‑Mechanik

### ✔️ Anti‑Bot‑Mechanismen  
- Blacklist nur in den ersten 60 h  
- Max‑Tx & Max‑Wallet Limits  
- Trading erst nach Launch

### ✔️ Anti‑Honeypot  
- Pause nur 7 Tage möglich  
- Danach **permanent deaktiviert**  
- Owner kann Contract nicht einfrieren

### ✔️ Anti‑Rug  
- Kein Mint  
- Kein versteckter Supply‑Zugriff  
- Kein manipuliertes Router‑Update  
- Owner‑Macht klar begrenzt

---

## 🔹 Funktionen (Auszug)

### `launch()`
Aktiviert Trading und setzt Deadlines für Blacklist & Pause.

### `blacklist(address,bool)`
Nur in den ersten 60 h möglich.

### `pause()` / `unpause()`
Nur in den ersten 7 Tagen möglich.

### `manualSwap()`
Owner kann Marketing‑Tokens manuell in BNB tauschen.

### `_maybeSwap()`
Automatischer Swap bei Verkäufen mit Randomisierung.

---

## 🔹 Lizenz  
MIT License

---

# 🟩 **B) Website‑Text (Landing Page)**  
*(Kurz, klar, vertrauensbildend)*

---

# **ΕΥΘΗΝΙΑ (ETHN)**  
### Ein sicherer, transparenter und fairer Token auf der Binance Smart Chain

ΕΥΘΗΝΙΑ wurde entwickelt, um das zu bieten, was viele Projekte versprechen, aber kaum eines hält:  
**echte Sicherheit, klare Regeln und vollständige Transparenz.**

Unser Smart Contract wurde audit‑bereinigt und enthält:

- **Anti‑MEV‑Mechanismen** gegen Sandwich‑Bots  
- **Zeitlich begrenzte Admin‑Kontrolle** (Blacklist 60 h, Pause 7 Tage)  
- **Keine Backdoors, kein Mint, kein manipuliertes Routing**  
- **Deflationäre Tokenomics** mit realem Burn  
- **Fair‑Launch‑Mechanik** ohne versteckte Vorteile  

ΕΥΘΗΝΙΑ ist ein Token, der Vertrauen verdient — durch Code, nicht durch Worte.

---

# 🟧 **C) Whitepaper‑Kapitel: Smart‑Contract‑Architektur**

---

# **4. Smart‑Contract‑Architektur**

Der Smart Contract von ΕΥΘΗΝΙΑ wurde mit besonderem Fokus auf Sicherheit, Transparenz und langfristige Stabilität entwickelt.  
Er basiert auf dem BEP‑20‑Standard und nutzt geprüfte OpenZeppelin‑Bibliotheken.

---

## **4.1 Sicherheitsprinzipien**

### **Reentrancy‑Schutz**
Alle Swap‑Operationen sind durch `nonReentrant` und interne Swap‑Locks geschützt.

### **Zeitlich begrenzte Admin‑Kontrolle**
Um Missbrauch zu verhindern, sind kritische Funktionen nur in der frühen Phase verfügbar:

- Blacklist: **60 Stunden** nach Launch  
- Pause: **7 Tage** nach Launch  

Danach sind beide Funktionen **permanent deaktiviert**.

### **Keine Backdoors**
Der Contract enthält **keine** Funktionen zum:

- Minten neuer Tokens  
- Manipulieren von Balances  
- Ändern des Routers nach Launch  
- Umgehen der Gebührenmechanik  

---

## **4.2 Tokenomics‑Mechanik**

### **Transaktionssteuer**
Jede Transaktion unterliegt einer 7 % Steuer:

- **6 % Marketing**  
- **1 % Burn**  

Der Burn erfolgt direkt an die `0x000…dEaD` Adresse und reduziert das zirkulierende Angebot dauerhaft.

---

## **4.3 Anti‑MEV‑Mechanismen**

Um Sandwich‑Attacken zu erschweren, nutzt ΕΥΘΗΝΙΑ:

- Swap nur bei **Verkäufen**  
- **Randomisierte Swap‑Schwelle**  
- **Block‑Cooldown** zwischen Swaps  

Diese Mechanik macht Auto‑Swaps schwer vorhersehbar und reduziert MEV‑Risiken erheblich.

---

## **4.4 Fair‑Launch‑Mechanik**

Trading ist erst nach dem Aufruf von `launch()` möglich.  
Vor Launch sind:

- Transfers nur für Owner möglich  
- Blacklist & Pause noch nicht aktiv  
- Keine versteckten Vorteile für Bots oder Insider

---

## **4.5 BEP‑20‑Konformität**

Der Contract implementiert den vollständigen BEP‑20‑Standard:

- `transfer`  
- `transferFrom`  
- `approve`  
- `allowance`  
- `balanceOf`  
- `totalSupply`  

Alle Wallets, DEXs und Explorer erkennen den Token korrekt.
