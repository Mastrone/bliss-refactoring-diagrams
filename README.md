# Architettura e Refactoring del Software BLISS

Questo repository contiene i diagrammi architetturali e di sequenza ad alta risoluzione citati all'interno della tesi: **"[Refactoring del software BLISS per la ricerca di Tecnofirme]"**.

I diagrammi documentano il processo di ingegneria del software e di refactoring applicato alla pipeline **BLISS** (Breakthrough Listen Interesting Signal Search), un software di ricerca SETI ad alte prestazioni accelerato tramite GPU. Tutti i diagrammi presenti sono stati generati utilizzando il tool di analisi statica `clang-uml`.

## Struttura del Repository

Il repository è organizzato in tre categorie principali, strutturate per fornire un confronto oggettivo e diretto tra lo stato del codice pre-refactoring e post-refactoring.

### 1. Diagrammi Architetturali (`/architecture_diagrams`)
Diagrammi dei pacchetti ad alto livello che illustrano la topologia del software. 
* Evidenziano l'eliminazione delle dipendenze cicliche originariamente presenti tra i moduli `core` e `file_types`, dimostrando il raggiungimento di un'architettura unidirezionale.

### 2. Diagrammi delle Classi (`/class_diagrams`)
Diagrammi UML dettagliati focalizzati sui componenti matematici e di dominio centrale.
* Illustrano la risoluzione delle cosiddette "God Classes" e l'abbattimento della complessità dei costruttori tramite l'implementazione del Parameter Object Pattern. 
* Dimostrano il disaccoppiamento del motore logico dalle librerie fisiche di I/O (es. HDF5) attraverso l'introduzione delle interfacce astratte, come `IScanDataSource`.

### 3. Diagrammi di Sequenza (`/sequence_diagrams`)
Mappatura del flusso di esecuzione dinamico relativo al comando principale `bliss_find_hits`.
* La documentazione include il flusso esecutivo completo per entrambe le versioni del software.
* Per garantire una maggiore leggibilità, l'analisi del flusso dinamico è stata frammentata in quattro macro-fasi (Inizializzazione, Configurazione del Device, Calcolo Matematico, Serializzazione dell'Output). Questa suddivisione permette di isolare e analizzare nel dettaglio le ottimizzazioni introdotte a runtime, quali l'adozione della Lazy Evaluation e la drastica riduzione delle chiamate bloccanti ai dischi.

## Riferimenti Esterni

* Repository originale del software BLISS: [n-west/bliss](https://github.com/n-west/bliss)
* Informazioni sul progetto SETI e Breakthrough Listen: [Berkeley SETI Research Center](https://seti.berkeley.edu/)