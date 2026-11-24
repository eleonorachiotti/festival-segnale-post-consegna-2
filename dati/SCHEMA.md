# Schema dei dati — Segnale

## Entità

### Evento

| Campo | Tipo | Definizione |
|---|---|---|
| `id` | Numero intero | Identificativo univoco dell’evento; chiave primaria. |
| `titolo` | Testo | Titolo dell’evento. |
| `data` | Data (`AAAA-MM-GG`) | Data in cui si svolge l’evento. |
| `orario` | Testo (`HH:MM`) | Orario di inizio dell’evento. |
| `categoria` | Testo | Tipologia dell’evento, per esempio “Incontro”, “Laboratorio” o “Mostra”. |
| `descrizione` | Testo | Descrizione dell’evento. |
| `immagine` | Testo | Percorso del file immagine. |
| `immagine_alt` | Testo | Testo alternativo dell’immagine. |
| `sede_id` | Numero intero | Identificativo della sede in cui si svolge l’evento; chiave esterna verso `Sede.id`. |

### Sede

| Campo | Tipo | Definizione |
|---|---|---|
| `id` | Numero intero | Identificativo univoco della sede; chiave primaria. |
| `nome` | Testo | Nome della sede. |
| `indirizzo` | Testo | Indirizzo della sede. |

## Chiavi e relazione

`Evento.id` e `Sede.id` sono le chiavi primarie delle rispettive entità. Ogni evento fa riferimento a una sede tramite `Evento.sede_id`, che corrisponde a `Sede.id`. Una sede può ospitare zero o più eventi; ogni evento è associato a una sede.

## Quantità

Il dataset contiene sei eventi e tre sedi.

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


