# Nether senza Fast Travel

Datapack per **Minecraft Java Edition 26.2** che disattiva il fast travel del Nether.

Nel gioco normale 1 blocco nel Nether vale 8 blocchi nell'Overworld, quindi i portali permettono di attraversare grandi distanze camminando poco. Questo datapack porta la scala a **1:1**: le coordinate del Nether sono uguali a quelle dell'Overworld e i portali non fanno più risparmiare strada.

## Compatibilità

| Minecraft Java | Formato datapack |
|----------------|------------------|
| 26.2           | 107.1            |

Per altre versioni bisogna adattare il file `pack.mcmeta` e controllare che `the_nether.json` abbia lo stesso formato di quello del gioco.

## Come funziona

Il datapack sostituisce il tipo di dimensione `minecraft:the_nether` con una copia identica a quella vanilla, tranne un valore:

```json
"coordinate_scale": 1.0
```

In vanilla il valore è `8.0`. Tutto il resto (altezza, luce, regole dei letti, lava, ecc.) resta uguale.

## Installazione

1. Scarica lo zip dalla pagina delle [Release](../../releases) oppure scarica il repository come ZIP.
2. Metti lo zip nella cartella `datapacks` del mondo, senza decomprimerlo:
   ```
   <mondo>/datapacks/nether_no_fast_travel.zip
   ```
3. **Riavvia il mondo o il server.** `/reload` non basta, perché i tipi di dimensione si caricano solo all'avvio.
4. Controlla che sia attivo con `/datapack list`.

Funziona meglio se lo installi **quando crei il mondo**.

## Come verificare che funzioni

1. Costruisci un portale nell'Overworld, per esempio a `X=500 Z=500`, lontano da altri portali.
2. Entra nel portale.
3. Nel Nether premi `F3`: devi essere vicino a `X=500 Z=500`. Con la scala vanilla saresti vicino a `X=62 Z=62`.

## Note e limiti

- **Le coordinate non sono mai identiche al blocco.** Il gioco cerca il posto libero più vicino per il portale di arrivo, quindi X e Z possono cambiare di qualche blocco. La Y dipende dal terreno del Nether.
- **Portali vicini si collegano tra loro.** Il gioco usa un portale già esistente se ne trova uno nel raggio di ricerca (circa 16 blocchi verso il Nether e 128 verso l'Overworld). Costruisci i portali lontani l'uno dall'altro.
- **Mondi già esistenti.** I portali costruiti prima di installare il datapack possono portare in posti diversi. Conviene distruggerli e rifarli.
- **Altri datapack.** Se un altro datapack modifica `data/minecraft/dimension_type/the_nether.json`, vince quello caricato per ultimo.

## Struttura

```
nether_no_fast_travel/
├── pack.mcmeta
└── data/
    └── minecraft/
        └── dimension_type/
            └── the_nether.json
```

## Licenza

Progetto distribuito con licenza [MIT](LICENSE).