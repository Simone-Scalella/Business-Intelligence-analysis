# Analisi di un dataset contenente informazioni riguardanti azioni violente commesse dalle forze dell'ordine sul suolo americano.
### Introduzione
Con la seguente relazione si intende illustrare l’analisi descrittiva e predittiva svolta su un dataset relativo alle violenze commesse dalla polizia nel territorio americano.

### Dataset
Il dataset che sarà analizzato più avanti nella trattazione è come detto in precedenza un dataset relativo alle violenze commesse dalla polizia nei confronti dei cittadini americani:[link](https://www.kaggle.com/datasets/jpmiller/police-violence-in-the-us).

Questo dataset è una raccolta di dati provenienti da diverse fonti riguardanti le violenze commesse dalla polizia negli Stati Uniti, tra il 2013 e il 2019. Si andranno ad analizzare vari aspetti, tra cui il più importante l’equità razziale, tema molto sensibile negli Stati Uniti. Nel complesso, in sette anni la polizia americana ha ucciso oltre 7.500 persone, ovvero in media 1.100 all’anno e circa 34 ogni 10 milioni di abitanti. Si tratta soltanto di una parte dei 15 mila e più omicidi commessi ogni anno negli Stati Uniti, ma comunque significativa, considerando che i poliziotti rappresentano una fetta molto piccola della popolazione.


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
Ulteriori dettagli relativi alle analisi effettuate sono riportati nella seguente [relazione]()
