# Analisi di un dataset contenente informazioni riguardanti azioni violente commesse dalle forze dell'ordine sul suolo americano.
### Introduzione
Con la seguente relazione si intende illustrare l’analisi descrittiva e predittiva svolta su un dataset relativo alle violenze commesse dalla polizia nel territorio americano.

### Dataset
Il dataset che sarà analizzato più avanti nella trattazione è come detto in precedenza un dataset relativo alle violenze commesse dalla polizia nei confronti dei cittadini americani: [link](https://www.kaggle.com/datasets/jpmiller/police-violence-in-the-us).

Questo dataset è una raccolta di dati provenienti da diverse fonti riguardanti le violenze commesse dalla polizia negli Stati Uniti, tra il 2013 e il 2019. Si andranno ad analizzare vari aspetti, tra cui il più importante l’equità razziale, tema molto sensibile negli Stati Uniti. Nel complesso, in sette anni la polizia americana ha ucciso oltre 7.500 persone, ovvero in media 1.100 all’anno e circa 34 ogni 10 milioni di abitanti. Si tratta soltanto di una parte dei 15 mila e più omicidi commessi ogni anno negli Stati Uniti, ma comunque significativa, considerando che i poliziotti rappresentano una fetta molto piccola della popolazione.

In particolare, questo dataset è composto da 5 file in formato .csv, e sono:

1. **deaths_arrests.csv:** questo file contiene informazioni relative all’etnia della popolazione americana, al numero di persone uccise durante un arresto in un determinato arco temporale e varie medie ottenute da questi dati.

2. **fatal_encounters_dot_org.csv:** questo file contiene informazioni relative agli eventi con esito le-tale tra civili e forze dell’ordine, dove i civili hanno perso la vita.

3. **police_deaths_538.csv:** questo file contiene informazioni relative ai decessi degli agenti delle forze dell’ordine durante il servizio.

4. **police_killings_MPV.csv:** questo file contiene informazioni relative alle persone che sono morte durante una colluttazione con le forze dell’ordine. La differenza con il file precedente è che in questo file sono riportati solo gli eventi letali dovuti ad un intervento diretto delle forze dell’ordine, nell’altro file consideriamo anche eventi indiretti, come ad esempio incidenti e suicidi.

5. **shootings_wash_post.csv:** questo file contiene un sottoinsieme delle informazioni presenti nel file police_killings_MPV.csv.

## ETL dei dati:

Al fine di preparare il dataset che sarà poi analizzato con i diversi tool di analisi, è risultato necessario mettere in atto una fase di ETL dei dati, articolata in tre fasi principali:

1. **Extract:** durante la fase di estrazione dei dati, sono stati scartati tutti quei campi non utili ai fini delle analisi. In particolare, si è deciso di tenere in considerazione alcuni campi utili per creare delle gerarchie sulle dimensioni (temporale, spaziale, fascia d’età).

2. **Trasformation:** con questa fase andiamo ad effettuare una sorta di pulizia, una preparazione dei dati per la fase di load, rendendoli più chiari e completi.
   In particolare, si è voluto prestare attenzione a:
   * Rinominare i campi: si è notato che alcuni campi possiedono una terminologia alquanto complessa al fine della nostra analisi; si è quindi deciso di rinominare tali campi utilizzando una nomenclatura più adatta;
   * Impostazione della data nel formato italiano: essendo le date impostate nel formato mm/gg/aaaa, si è deciso di sostituire con il formato gg/mm/aaaa, in quanto più comprensibile; sono stati anche eliminati campi contenenti anche solo l’anno, considerando quindi la data come unico campo temporale;
   * Eliminazione delle virgole per identificare le migliaia: nei campi numerici, le migliaia sono separate mediante una virgola, si è deciso di toglierle per migliorare le analisi in cui questi verranno impiegati;
   * Controllo di campi vuoti e nulli: In presenza di campi vuoti o campi nulli, utili all’analisi è deciso di trattarli in tre tipologie differenti:
     - Eliminare la riga relativa al campo vuoto o nullo;
     - Sostituire tali valori, nel caso di campi numerici, con lo zero;
     - Essendo il dataset composto da un numero notevolmente grande di dati, si è deciso nel caso di campi numerici, se necessario, di inserire il valore medio ottenuto dalla media dei valori di tutti i campi relativi a quell’attributo oppure considerare il valore massimo o minimo che occorre il maggior numero di volte nei campi di quell’attributo.
   * Controllo valori risultato: nel caso di campi contenenti il risultato di determinate funzioni, si è andato a controllare se il risultato ottenuto non ritornasse valori errati o impossibili;
   * Controllo numero popolazione: abbiamo controllato se il numero effettivo delle persone appartenenti ad un Paese effettivamente corrispondessero con il numero reale;
   * Eliminazione dei campi contenenti url: si è deciso di rimuovere tali campi in quanto non utili al fine delle analisi (tali url fanno riferimento ad immagini delle vittime o a documenti/articoli ufficiali relativi all’omicidio);
   * Eliminazione campi contenenti informazioni ridondanti: all’interno della stessa tabella sono stati individuati dei campi contenenti informazioni duplicate, si è quindi deciso di rimuoverli
3. **Load:** In questo modo otteniamo un dataset più pulito e pronto per essere caricato e analizzato tramite i vari tool


## Qlik
Nello specifico andremo ad utilizzare Qlik Sense, un software per la “Self-service Analytics”, il quale permette all’utente finale di realizzare analisi sui dati d’interesse, al fine di creare report personalizzati e dashboard dinamiche.
In primis, all’interno dello spazio di lavoro condiviso, è stata creata un’applicazione in cui è presente una raccolta di elementi riutilizzabili, come dati (articolati in misure, dimensioni e visualizzazioni), fogli e racconti. Una volta caricato il dataset abbiamo deciso di effettuare una serie di analisi esplorative, con lo scopo di estrarre informazioni di interesse. Le analisi che siamo andati a fare, relativamente a ciascun dataset sono le seguenti:
<ol>
  <li><b>deaths_arrests.csv:</b>
    <ul>
      <li>Totale degli arresti avvenuti negli anni, dal 2013 al 2018, in base allo Stato e alla città</li>
      <li>Totale delle persone uccise dalla polizia dal 2013 al 2020</li>
      <li>Totale dei crimini violenti dal 2013 al 2018</li>
    </ul>
  </li>
  <li><b>fatal_encounters_dot_org.csv:</b>
    <ul>
      <li>Distribuzione maggiorenne/minorenne</li>
      <li>Tipologie di armi possedute dalla vittima</li>
      <li>Fascia di età delle vittime</li>
      <li>Andamento annuale incontri letali</li>
      <li>Incontri letali, suddivisi per contea</li>
    </ul>
  </li>
  <li><b>police_deaths_538.csv:</b>
    <ul>
      <li>Rapporto uomo/unità cinofile deceduti</li>
      <li>Analisi degli Stati in base all'etnia delle vittime</li>
      <li>Analisi degli Stati rispetto all'indice di violenza e al numero di vittime per arresti</li>
    </ul>
  </li>
</ol>

## Tableau
Questo software permette di creare e distribuire dashboard interattive e condivisibili, che rappresentano le tendenze e le conoscenze rilevate dai dati. Permette la fusione di dataset etero-genei e la centralizzazione dei dati. Consente inoltre di stabilire delle relazioni tra le tabelle del dataset effet-tivamente collegate, in modo da poter definire analisi più approfondite. Abbiamo un foglio di lavoro per ogni grafico mentre la dashboard può essere costituita dall’unione di più worksheet. Abbiamo deciso di suddividere le dashboard in relazione al tipo di file che stiamo analizzando, suddividendole in quattro tipologie di analisi. Le analisi che siamo andati a fare, relativamente a ciascun dataset sono le seguenti:
<ol>
  <li><b>deaths_arrests.csv:</b>
    <ul>
      <li>Numero di persone uccise ogni 10 mila arresti</li>
      <li>Numero dei crimini violenti per Stato</li>
      <li>Cinque stati con la media annuale più alta degli arresti</li>
      <li>Numero di persone uccise, divise per etnia, tra il 2013 e il 2019</li>
    </ul>
  </li>
  <li><b>fatal_encounters_dot_org.csv:</b>
    <ul>
      <li>Andamento trimestrale 2000-2020 delle persone uccise, con confronto tra andamento della previsione nell'anno 2021-2022 e andamento reale con dati di test raccolti successivamente</li>
      <li>Dipartimenti con più di 150 omicidi</li>
      <li>Omicidi divisi per fascia d'età</li>
      <li>BoxPlot età media delle persone uccise, per Stato</li>
      <li>Numero di persone uccise per fascia d'età, suddivisi per arma utilizzata per l'omicidio</li>
    </ul>
  </li>
  <li><b>police_deaths_538.csv:</b></li>
    <ul>
      <li>Stati con un numero di poliziotti uccisi superiore alla media</li>
      <li>Andamento temporale dei poliziotti deceduti (umani ed unità cinofile mantenute separatamente)</li>
    </ul>
  <li><b>police_killings_MPV.csv:</b>
    <ul>
      <li>Scontri letati per aree geografiche: Rural, Suburban, Urban</li>
      <li>Totale degli omicidi per tipologia di intervento: sparo, teaser, contenimento, spray al peperoncino</li>
    </ul>
  </li>
  <li><b>shootings_wash_post.csv:</b>
    <ul>
      <li>Stati con più di 100 omicidi</li>
      <li>Andamento temporale del numero di persone uccise, divise per sesso</li>
      <li>Percentuali armi possedute dalle vittime al momento dell'omicidio</li>
      <li>Andamento temporale del numero di persone uccise su Stati con più di 200 omicidi</li>
    </ul>
  </li>
</ol>

## PowerBI
Questo software offre una serie di strumenti in grado di rappresentare i dati in maniera grafica ed intuitiva attraverso l’uso dei report, inoltre, mette a disposizione tutta una serie di grafici, utili per svolgere qualsiasi tipo di analisi, e per rappresentare i dati nel modo più corretto.Power BI offre una serie di strumenti aggiuntivi per la manipolazione dei dati attraverso l’editor di Power Query, da una parte, e l’uso di un linguaggio simile a quello utilizzato per Microsoft Excel, dall’altro. Tutte queste funzionalità gli permettono di essere molto utile anche in fase di ETL, inoltre, offre la possibilità di integrare script in R e Python, linguaggi molto utilizzati nell’ambito della data science che permettono di aumentare le funzionalità del software stesso. Le analisi che siamo andati a fare sono le seguenti:
<ul>
    <li>Andamento annuale di persone uccise, divise per sesso</li>
    <li>Fattori di influenza chiave sul sesso della vittima</li>
    <li>Andamento temporale del numero di decessi per etnia con previsione</li>
    <li>Analisi sulle conseguenze per gli agenti</li>
    <li>Analisi temporale sull'andamento dei suicidi</li>
    <li>Analisi sull'uso intenzionale di forza letale</li>
</ul>

## Tecnologie utilizzate
<ul>
  <li>Qlik</li>
  <li>Tableau</li>
  <li>PowerBI</li>
</ul>

Questi software sono strumenti molto efficienti e flessibili, che danno anche la possibilità di scrivere interrogazioni personalizzate. Ad esempio si è implementata soluzione che consiste nel fare un controllo sui valori, nel caso in cui si trova questo valore si va ad inserire uno 0, in tutti gli altri mettiamo la somma del campo d’interesse.
Riportiamo di seguito l'immagine dell'esempio.

![01](https://github.com/Simone-Scalella/Business-Intelligence-analysis/blob/main/image/condizione%20di%20ordinamento.png)


Ulteriori dettagli relativi alle analisi effettuate sono riportati nella seguente [relazione](https://github.com/Simone-Scalella/Business-Intelligence-analysis/blob/main/Relazione_Qlik_Tableau_PowerBI.pdf).

## Esempi di risultati ottenuti

### Dash ottenuta con Qlik:

![Qlik](https://github.com/Simone-Scalella/Business-Intelligence-analysis/blob/main/image/Analisi01qlik.png)

### Analisi con Tableu:

![Tableu](https://github.com/Simone-Scalella/Business-Intelligence-analysis/blob/main/image/Dash03T.png)

### Analisi realizzata utilizzando un oggetto visivo presente nel marketplace commerciale Microsoft AppSource:

![BI](https://github.com/Simone-Scalella/Business-Intelligence-analysis/blob/main/image/BILastImage.png)

## Autori

* **Scalella Simone:** [Github](https://github.com/Simone-Scalella)
* **Zhang Yihang:** [Github](https://github.com/Accout-Personal)
* **Margherita Galeazzi:** [Github](https://github.com/MargheritaGaleazzi)
* **Chiara Amalia Caporusso:** [Github](https://github.com/ChiaraAmalia)
