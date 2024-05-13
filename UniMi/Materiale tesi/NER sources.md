- Contesto "geolocalization" e  "identification"

Per questi due contesti l'obiettivo del modello è di individuare rispettivamente entità geopolitiche e persone.
Per far ciò ho utilizzato un modello fornito da spaCy (https://spacy.io/models/en) considerando solo le entità con labels "PERSON" e "GPE". Il modello è stato addestrato con 
- OntoNotes5 (https://catalog.ldc.upenn.edu/LDC2013T19) un progetto di tre università statunitensi che ha l'obiettivo di annotare diversi testi (2.9m words) da fonti diverse (es News, Web, Television...) 
- Wordnet (https://wordnet.princeton.edu/) un database lessicale della lingua inglese fornito dalla Princeton University
- ClearNLP (https://github.com/clir/clearnlp-guidelines/blob/master/md/components/dependency_conversion.md)

F-Score dichiarato: 0.85

- Contesto "health"

Per il contesto sanitario invece l'obiettivo è di individuare malattie e medicine/chemicals.
Per far ciò ho utilizzato un modello presente nel progetto open-source scispacy (https://github.com/allenai/scispacy) dell'organizzazione no profit Allen Institute for Artificial Intelligence (https://allenai.org/).
Tra i vari modelli disponibili ho scelto "en_ner_bc5cdr_md" in quanto riconosceva le entità di mio interesse. Il modello è stato allenato utilizzando BC5CDR (BioCreative V CDR corpus: https://paperswithcode.com/dataset/bc5cdr) che consiste in 1500 articoli medici in cui sono state etichettate 4409 chemicals e 5818 malattie

F1-Score dichiarato: 84.28