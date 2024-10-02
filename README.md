# Intelligenza_Artificiale
Corso universitario 

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

![FIG.2: 156.jpg](link-a-immagine)

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

![FIG.2: 156.jpg](link-a-immagine)

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

