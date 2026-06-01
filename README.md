# 📊 Analisi Finanziaria delle Transazioni - Power BI Dashboard

## 📌 Descrizione del progetto

Questa dashboard è stata realizzata in **Power BI** come progetto di apprendimento per approfondire diverse funzionalità dello strumento, tra cui:

- Data Cleaning con Power Query
- Creazione di misure DAX
- Calcolo delle variazioni **Year over Year (YoY%)**
- Navigazione tramite **Drill-through**
- Filtri interattivi
- Visualizzazioni KPI
- Tabelle e grafici dinamici

L'obiettivo della dashboard è fornire una panoramica delle transazioni finanziarie e consentire un'analisi dettagliata delle operazioni effettuate dai clienti.

---

## 📂 Dataset

Il dataset contiene informazioni relative a transazioni finanziarie effettuate da clienti, tra cui:

- ID transazione
- Data transazione
- Cliente
- Tipologia di transazione
- Stato della transazione
- Importo
- Commissioni
- Tasse
- Stato e città
- Segmento cliente

---

## 🧹 Data Cleaning e Preprocessing

Prima della realizzazione della dashboard sono state effettuate alcune operazioni di pulizia e preparazione dei dati.

### 1. Rimozione dei duplicati

La colonna `transaction_id` rappresenta la chiave primaria del dataset.

Sono stati eliminati eventuali record duplicati per garantire che ogni transazione fosse rappresentata una sola volta.

---

### 2. Gestione degli importi negativi

Nella variabile `amount` erano presenti valori negativi.

Poiché una transazione rappresenta un importo movimentato e non può assumere valore negativo nel contesto dell'analisi, è stato applicato il valore assoluto:

```text
amount = |amount|
```

---

### 3. Gestione dei valori null nelle commissioni

La variabile `fee_amount` presentava alcuni valori mancanti.

È stata effettuata una sostituzione tramite la media della variabile:

```text
NULL → media(fee_amount)
```

Motivazione:

- il valore mancante potrebbe indicare un'informazione non disponibile;
- utilizzare la media consente di non perdere osservazioni.

In alternativa sarebbe stato possibile sostituire i valori mancanti con `0`, poiché nel dataset sono presenti commissioni pari a zero che potrebbero indicare l'assenza di commissioni applicate.

---

### 4. Creazione del nome completo cliente

Nel dataset erano presenti due colonne separate:

- `first_name`
- `last_name`

È stata creata una nuova variabile:

```text
customer_name = first_name + " " + last_name
```

per migliorare la leggibilità delle informazioni nelle visualizzazioni.

---

## 📈 KPI principali

La dashboard mostra i seguenti indicatori:

- Importo totale movimentato
- Numero totale di transazioni
- Valore medio delle transazioni
- Totale commissioni
- Totale imposte

Ogni KPI include la variazione rispetto all'anno precedente (**YoY %**).

---

## 📊 Analisi disponibili

### Andamento mensile

Visualizzazione dell'evoluzione dell'importo totale (o degli altri kpi in base al filtro) nel corso dell'anno.

---

### Stato delle transazioni

Distribuzione delle transazioni tra:

- Success
- Failed
- Pending

---

### Segmentazione clienti

Analisi degli importi per tipologia di cliente:

- Retail
- Premium
- SME
- Corporate
- Wealth

---

### Analisi geografica

Visualizzazione degli importi aggregati per stato.

---

### Analisi per tipologia di transazione

Confronto tra:

- Numero di transazioni
- Importo totale
- Commissioni
- Tasse

per ciascuna categoria di operazione.

---

### Analisi per sesso

Ripartizione degli importi movimentati tra clienti maschi e femmine.

---

## 🔄 Analisi Year over Year (YoY%)

Uno degli aspetti principali sviluppati in questo progetto è stato il calcolo delle variazioni rispetto all'anno precedente.

Per ciascun KPI è stata implementata una misura che confronta il valore corrente con quello dell'anno precedente:

```text
YoY % = (Valore corrente - Valore anno precedente)
        / Valore anno precedente
```

Questo consente di valutare rapidamente la crescita o la diminuzione delle metriche principali.

---

## 🔍 Drill-through

È stata implementata una funzionalità di **Drill-through** che permette di passare da una vista aggregata a una vista dettagliata delle transazioni.

### Esempio

Se l'utente seleziona il mese di **Gennaio** dal grafico dell'andamento mensile:

1. compare l'opzione **Drill-through Transazioni**
2. cliccando sull'opzione si viene reindirizzati alla pagina di dettaglio
3. vengono mostrate esclusivamente le transazioni relative al contesto selezionato

La stessa funzionalità è disponibile anche per altri elementi della dashboard.

---

## 🛠️ Strumenti utilizzati

- Power BI Desktop
- Power Query
- DAX

---

## 🎯 Obiettivi di apprendimento

Questo progetto è stato realizzato principalmente come esercitazione per approfondire:

- Modellazione dati in Power BI
- Data Cleaning con Power Query
- Creazione di KPI
- Misure DAX
- Calcoli YoY%
- Drill-through
- Interattività tra visualizzazioni
- Best practice di progettazione dashboard

---

## 🚀 Possibili sviluppi futuri

- Analisi delle transazioni fallite
- Segmentazione avanzata dei clienti
- Analisi temporali più avanzate (MoM, QoQ, CAGR)
- Geolocalizzazione tramite mappe interattive

---
