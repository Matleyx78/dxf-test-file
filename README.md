# DXF di prova
 
File DXF disegnati da zero e salvati con AutoCAD, da usare come riferimento per i
test di [Tecnigrafo](https://github.com/Matleyx78/tecnigrafo) e di qualunque altro
lettore o scrittore DXF.
 
Pubblicati in **CC0 1.0** (pubblico dominio, vedi [LICENSE](LICENSE)): si possono
copiare, modificare e ridistribuire liberamente, anche senza citare la fonte.
 
## Caratteristiche comuni
 
- Salvati da AutoCAD in DXF ASCII, fine riga CRLF.
- Unità del disegno in millimetri (`$INSUNITS` = 4), tranne `vuoto-pollici.dxf`.
- Code page `ANSI_1252`: fino a R2004 i caratteri non latini sono scritti come
  sequenze `\U+XXXX`, da R2007 il file è in UTF-8.
- Ripuliti dai dati personali: `$LASTSAVEDBY` vuoto, percorso del file ridotto al
  solo nome, GUID sostituiti con valori fittizi.
- Lo stesso disegno salvato in versioni diverse contiene le stesse entità, con le
  stesse coordinate.
| Versione DXF | `$ACADVER` |
|---|---|
| R2000 | AC1015 |
| R2004 | AC1018 |
| R2007 | AC1021 |
| R2010 | AC1024 |
| R2013 | AC1027 |
| R2018 | AC1032 |
 
## File
 
| File | Versioni | Contenuto |
|---|---|---|
| `base-<versione>.dxf` | 2000, 2004, 2007, 2010, 2013, 2018 | Entità base: 2 `LINE`, 2 `CIRCLE`, 2 `ARC`, 3 `LWPOLYLINE` (con archi), 1 `TEXT` |
| `testi-<versione>.dxf` | 2000, 2004, 2007, 2010, 2018 | 23 `TEXT`: tutte le giustificazioni (sinistra, centro, destra, mezzo, adatta, allineato, alto/mezzo/basso × sinistra/centro/destra), rotazione 30°, obliquo 15°, fattore di larghezza 0,8, testo capovolto e all'indietro, lettere accentate con `%%C`, `%%D`, `%%P`, testo in cirillico |
| `Specchiati-<versione>.dxf` | 2000, 2007, 2010, 2013, 2018 | Oggetti specchiati sul piano (testo, arco, cerchio, polilinea con archi) e oggetti con estrusione (0, 0, −1): `CIRCLE`, `ARC` e `TEXT` |
| `polilinee.dxf` | 2018 | 5 `LWPOLYLINE`: larghezza costante, larghezza variabile per vertice, archi (bulge), polilinea chiusa, elevazione negativa |
| `quote-z.dxf` | 2018 | Quote Z e spessori: `LINE` a Z = 10, `CIRCLE` con spessore, `LWPOLYLINE` con elevazione ±25 e spessore, `CIRCLE` su un piano inclinato di 45° |
| `colori-layer-tipilinea.dxf` | 2018 | 12 `LINE` su 4 layer, ognuno con colore e tipo di linea propri: `0` (7, Continuous), `Layer1` (1, `ACAD_ISO02W100`), `Layer2` (3, `ACAD_ISO05W100`), `Layer3` (5, `ACAD_ISO14W100`, spessore 0,30 mm); 6 linee hanno un colore proprio (ACI 1–6) invece di "DaLayer" |
| `non-gestiti.dxf` | 2018 | Oggetti che un lettore semplice potrebbe non gestire: `HATCH` (ANSI31), 5 `DIMENSION` (lineare, allineata, angolare, raggio, diametro), `ARC_DIMENSION`, 3 `INSERT` di 2 blocchi, insieme a `LWPOLYLINE` e `CIRCLE` |
| `vuoto-mm.dxf` | 2018 | Disegno vuoto in millimetri (`$INSUNITS` = 4) |
| `vuoto-pollici.dxf` | 2018 | Disegno vuoto in pollici (`$INSUNITS` = 1) |
 
## Da sapere
 
- `$MEASUREMENT` vale 0 (imperiale) in tutti i file, ereditato dal modello di
  partenza: indica le impostazioni predefinite di tratteggi e tipi di linea, non
  l'unità del disegno.
 
