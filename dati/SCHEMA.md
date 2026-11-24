# Schema dei dati — Segnale

## Entità

### Evento

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `titolo` | testo | `"Lettere in movimento"` |
| `data` | data in formato `AAAA-MM-GG` | `"2026-06-12"` |
| `orario` | testo, formato `HH:MM` | `"10:00"` |
| `categoria` | testo | `"Incontro"` |
| `descrizione` | testo | `"Un incontro su tipografia, ritmo e comunicazione visiva."` |
| `immagine` | percorso testuale | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | testo | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | numero intero | `1` |

### Sede

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `nome` | testo | `"Officina Nord — Sede centrale"` |
| `indirizzo` | testo | `"Corso Duca degli Abruzzi 24, Torino"` |

## Chiavi e relazione

`id` è la chiave primaria numerica di ciascuna entità. È univoca all’interno dell’entità e stabile.

Una sede può ospitare più eventi e ogni evento fa riferimento a una sede. `Evento.sede_id` rimanda a `Sede.id`.

## Quantità

Il dataset contiene sei eventi e tre sedi.

## Aggiornamento

I dati vengono aggiornati modificando i file JSON nella repository e pubblicando le modifiche.

## Visualizzazione

La pagina Programma genera una scheda per ogni evento e mostra data, orario, categoria, titolo, descrizione, immagine e nome della sede. Se il riferimento alla sede non è valido, la scheda mostra “Sede da definire”.

La pagina Info e luoghi presenta le sedi, la galleria fotografica, la mappa e i dati meteo attuali di Torino.

## Schema entità-relazione

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : ospita
    SEDE {
        int id PK
        string nome
        string indirizzo
    }
    EVENTO {
        int id PK
        string titolo
        date data
        string orario
        string categoria
        string descrizione
        string immagine
        string immagine\_alt
        int sede\_id FK
    }