# Google_Looker_Studio_Esame_Finale
File che compongono l'esame finale del modulo Google Looker Studio.

**MIA IDEA PERSONALE**
  Voglio prendere in analisi la correlazione tra
  - genere e classifica
  - minutaggio della canzone e genere
  - minutaggio dela canzone e classifica

**DOMANDE A CUI RISPONDERO'**
  - Gli uomini scrivono canzoni mediamente più corte?
  - Le canzoni corte vincono di più?
  - Chi vince di più? uomo o donna?

**DATI UTILIZZATI**
  In questa cartella puoi trovare i dati utilizzati per effettuare questa analisi:
  
  I dati utilizzati per questa analisi sono relativi alle edizioni di Sanremo dal 1951 al 2023 organizzati in tre tabelle:
  
  **dati_canzoni_spotify_sanremo-1951-2023**
      Dati sulla popolarità del le canzoni italiane sulla piattaforma Spotify
      Attributi: Canzone, Artis5ta, Anno ultimo rilascio, Durata(min), Popolarità, URL immagine album
  
  **dati-classifica-sanremo-1951-2023**
      Dati sulle classifiche di ogni edizione del festival dal '51 al 2023
      Attributi: Posizione, Interprete, Canzone, Anno, Autori
  
  **dati-festival-sanremo-1951-2023**
    	dati su ogni edizione del festival 
    	Attributi: Anno, Periodo, Sede, Presentatore, Partecipanti, Vincitore


**PROCESSO**

  Sono partito da un analisi preliminare dei dati che avevo.
  
  Per rispondere alle domande che mi sono preposto ho fatto un merge tra le seguenti tabelle:
  dati-classifica-sanremo-1951-2023
  dati-canzoni-spotify-sanremo-1951-2023
  utilizzando il nome della canzone come punto di aggancio.
  La tipologia di Join è un left join in quanto voglio esclusivamente le canzoni che hanno partecipato a Sanremo.
  
  Dopo di ché avevo bisogno di conoscere il genere di ogni artista per fare delle considerazione.
  Da qui la prima difficoltà...
  
  La mia idea principale è stata quella di splittare il nome dell'artista dal cognome in due colonne differenti e poi analizzare il nome singolo.
  Ho usato la formula =TEXTSPLIT che mi ha permesso di dividere il testo in più colonne quando trovava uno spazio.
  
  Dopo di ché ho provato con la formula su Excel:
  =IF(OR(RIGHT(NomeCella, 1) = "a"), RIGHT(NomeCella, 3) = "ina"), "Donna", "Altro)
  
  In sostanza vado ad analizzare le ultime lettere del nome dell'artista, se sono uguali ad "a" o "ina" molto probabilmente è donna.
  
  Mi sono reso conto che questo processo ha dei limiti importanti, ad esempio:
  Non riconosce i nomi femminile che possono essere anche maschili come "Andrea"
  Non riconosce i nomi d'arte come "Levante"
  Non riconosce il nome dei gruppi come "Modà"
  
  Cercando online mi sono imbattuto in un Add-in di Excel:
  Gender API che permette di automatizzare il riconoscimento del genere partendo dal suo nome.
  È stata veramente molto utile.
  
  Una volta che ho pulito i dati, fatto il merge e ottenuto il genere dell'artista dal suo nome ho effettuato l'analisi dei dati vera e propria
