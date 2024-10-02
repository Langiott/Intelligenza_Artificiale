# Intelligenza_Artificiale
Corso universitario 
![FIG.0: IA.jpg](/IMMAGINI/IA)

## Strumenti Utilizzati e Reti Neurali

In questo progetto è stato utilizzato **Colab**, un framework che consente di eseguire blocchi di codice e commentarli utilizzando le caselle di testo chiamate Markdown. Abbiamo utilizzato il linguaggio **Python** e il **Google Drive** per prelevare le immagini precedentemente salvate in cartelle specifiche.

---

### CARICA_DATASET

Questo script permette di estrapolare le immagini dal Google Drive e di poterle visualizzare.

---

### CAT_&_DOG

Il notebook riguarda la **classificazione di immagini di cani e gatti** utilizzando una **rete neurale convoluzionale (CNN)**. Sono state utilizzate tecniche di **Data Augmentation** per migliorare la capacità del modello di generalizzare. Queste tecniche includono operazioni come:

- Flip delle immagini
- Rotazioni casuali
- Shift spaziali casuali

I metodi di valutazione includono **Accuracy & Precision**, che misurano la percentuale di immagini classificate correttamente, e la **Loss Function**, che monitora l'errore durante l'addestramento. Il risultato ottenuto è il seguente:

![FIG.1: cat.jpg](/Immagini)

---

### OBJ_PEAPLE_CNN

In questo script viene utilizzata una rete **CNN - Convolutional Neural Network** per classificare le immagini del **dataset-civiltà-contadina**, cercando di individuare la classe di appartenenza degli oggetti o delle persone presenti nell'immagine. Ad esempio, classificando un'immagine chiamata `86.jpg`, il risultato potrebbe essere:

- Swing (altalena): 51.25%
- Shovel (vanga): 7.47%
- Hook (amo): 6.06%

La predizione risulta di bassa qualità a causa di alcuni fattori mancanti:

- **Data Augmentation**
- **Pre-addestramento**
- Nessuna ottimizzazione del numero delle epoche
- Nessun **Cross-validation** dei dati di input

Sono state implementate le seguenti funzioni, che verranno utilizzate anche successivamente:

1. **load_images_from_directory()**: Carica le immagini dalla directory specificata, senza preprocessing.
2. **load_and_preprocess_image()**: Carica e trasforma le immagini nel formato richiesto dal modello, includendo ridimensionamento e normalizzazione.
3. **classify_and_move_image()**: Classifica le immagini utilizzando un modello pre-addestrato e le sposta nella cartella appropriata, OGGETTO o PERSONA, in base alla predizione.
4. **display_predictions()**: Visualizza i risultati delle predizioni dopo la classificazione.

---

### OBJ_&_PEAPLE_VGG16

In questo script viene utilizzata la rete **VGG16** per classificare le immagini del dataset-civiltà-contadina. La rete è pre-addestrata sul dataset **Imagenet**.

I risultati non sono soddisfacenti: la rete classifica tutte le immagini come oggetti, anche quando raffigurano persone. Tuttavia, la predizione sugli oggetti risulta più accurata. Ad esempio, l'immagine `197.jpg` viene classificata come:

- Potter's wheel (tornio): 35.11%
- Caldron (calderone): 20.80%
- Bucket (secchio): 9.33%

Anche se l'oggetto non viene riconosciuto correttamente come frantoio, la rete comprende che si tratta di un oggetto rotante. Un altro esempio è l'immagine `156.jpg`, correttamente classificata come hay (fieno).

---

### OBJ_PEAPLE_SEGNET

![FIG.2: 156.jpg](/Immaginj)

- **SegNet**: Modello di rete utilizzato per l'addestramento e la classificazione delle immagini.
- **COCODatasetPearson**: Dataset utilizzato per addestrare il modello SegNet, costituito principalmente da immagini di persone.
- **Test - dataset-civiltà-contadina**: Dataset di test contenente immagini del mondo della civiltà contadina. Viene utilizzato per valutare la capacità di classificazione del modello dopo l'addestramento.

Durante l'esecuzione su Colab, la GPU utilizza rapidamente tutta la RAM disponibile, causando limitazioni dopo pochi minuti di addestramento. Per ottimizzare l'uso delle risorse o accelerare i tempi di calcolo, è possibile modificare le impostazioni hardware selezionando TPU o altre opzioni.

Tuttavia, la GPU offerta su Colab è limitata in termini di potenza e memoria, il che potrebbe richiedere hardware più performante per gestire modelli di grandi dimensioni o dataset complessi. Non è stato possibile visualizzare il risultato finale.

---

### OBJ_PEAPLE_YOLO

In questo script viene utilizzata la rete **YOLO** per classificare le immagini del **dataset-civiltà-contadina**. La rete è pre-addestrata sul dataset **Imagenet**.

La predizione risulta di alta qualità, anche se mancano alcuni accorgimenti:

- **Epoche**: È stato deciso di utilizzare solo 1 epoca per ridurre i tempi di addestramento. L'aumento del numero di epoche migliorerebbe sicuramente i risultati.
- **Data Augmentation**
- **Pre-addestramento**
- Nessuna ottimizzazione del numero di epoche
- Nessun **Cross-validation** dei dati di input

Ad esempio, l'immagine `155.jpg` viene classificata correttamente come **thatch (paglia)** con una percentuale del 97.39%. Non tutte le predizioni sono accurate, ma la rete è comunque in grado di identificare correttamente il tipo di oggetto, come nel caso dell'immagine `194.jpg`, che viene classificata come **drum (bidone)** con una percentuale del 65.42%. La rete offre buone prestazioni.
![FIG.3: 155.jpg](/Immaginj)
![FIG.4: 194.jpg](/Immaginj)

Il codice nel file **OPEAN_AI_DALL_E_3.ipynb** utilizza librerie per interagire con modelli di intelligenza artificiale generativa, in particolare con quelli offerti da **OpenAI**. Questi modelli AI sono noti per essere in grado di generare contenuti, come testo o immagini, a partire da input testuali o visivi.

### Cos'è l'Intelligenza Artificiale Generativa?

L'intelligenza artificiale generativa è una sottocategoria dell'IA che si concentra sulla creazione di nuovi contenuti. Può essere applicata in vari contesti, tra cui:

- **Testo generativo**: Modelli di linguaggio come **GPT-4** generano frasi, documenti o risposte a domande sulla base di input forniti dall'utente.
- **Immagini generative**: Modelli come **DALL-E** creano immagini originali a partire da descrizioni testuali.
- **Musica o suoni generativi**: Esistono modelli capaci di generare tracce audio.
- **Video generativi**: Anche se ancora in evoluzione, ci sono reti neurali che possono generare brevi video.

### Modelli Utilizzati nel Codice

Dal codice presente nel notebook, possiamo ipotizzare l'uso dei seguenti modelli:

1. **DALL-E**: Questo è un modello generativo sviluppato da OpenAI che crea immagini a partire da descrizioni testuali. Probabilmente, lo script nel notebook interagisce con le API di OpenAI per inviare prompt testuali e ricevere immagini generate come output.

2. **GPT**: Anche se il notebook installa la libreria OpenAI, potrebbe essere utilizzato per integrare modelli di linguaggio come GPT (ad esempio, GPT-3 o GPT-4). Questi modelli sono utilizzati per generare testo, rispondere a domande, o supportare processi creativi come la scrittura di articoli o storie.

3. **API di OpenAI**: Il codice utilizza la libreria **OpenAI**, che permette di interfacciarsi facilmente con i vari modelli offerti dall'azienda tramite richieste API. Questo significa che lo script probabilmente include funzioni per inviare prompt a modelli di generazione di immagini o testo e ricevere i risultati.

### Dettagli di Funzionamento del Codice

Lo script si occupa probabilmente di:

- **Installazione delle dipendenze**: Come visto, installa la libreria OpenAI per interagire con i modelli.
- **Integrazione con le API**: Lo script potrebbe contenere funzioni che inviano una descrizione testuale all'API di DALL-E per ottenere immagini generate.
- **Gestione delle risposte**: Dopo l'invio di un prompt, lo script riceve una risposta, che può essere una stringa di testo o un'immagine generata, e la mostra all'utente o la salva in un file.

### Caratteristiche delle IA Generative Utilizzate:

- **DALL-E**: Questo modello utilizza reti neurali convoluzionali per interpretare il linguaggio naturale e trasformarlo in immagini dettagliate. È in grado di comprendere concetti complessi e di combinare elementi diversi in un'unica immagine coerente.
  
- **GPT (Generative Pretrained Transformer)**: Un modello di linguaggio molto potente, basato su un'architettura transformer. Viene utilizzato per generare testo in maniera fluida e contestualizzata, grazie al suo addestramento su una vasta quantità di dati testuali.

In sintesi, il notebook **OPEAN_AI_DALL_E_3.ipynb** sembra sfruttare i potenti strumenti di intelligenza artificiale generativa, come DALL-E, per creare contenuti visivi a partire da input testuali, utilizzando le API di OpenAI. Questo tipo di applicazione è particolarmente utile in campi creativi, artistici o di automazione del design.

