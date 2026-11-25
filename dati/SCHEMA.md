# Scheda dati — Festival Segnale

## Entità: Evento

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `titolo` | stringa | `"Lettere in movimento"` |
| `data` | data in formato `AAAA-MM-GG` | `"2026-06-12"` |
| `orario` | ora in formato `HH:MM` | `"10:00"` |
| `categoria` | stringa | `"Incontro"` |
| `descrizione` | stringa | `"Un incontro su tipografia, ritmo e comunicazione visiva."` |
| `immagine` | stringa, percorso del file | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | stringa | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | numero intero | `1` |

**Chiave primaria:** `id`, numerico, univoco nell’entità Evento e stabile.

## Entità: Sede

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `nome` | stringa | `"Officina Nord — Sede centrale"` |
| `indirizzo` | stringa | `"Corso Duca degli Abruzzi 24, Torino"` |

**Chiave primaria:** `id`, numerico, univoco nell’entità Sede e stabile.

## Relazione

Una sede può ospitare più eventi; ogni evento si svolge in una sola sede. Il campo `Evento.sede_id` fa riferimento a `Sede.id`.

**Quantità nei dati:** sei eventi e tre sedi.

## Aggiornamento e pubblicazione

Chi gestisce il sito aggiorna i dati modificando `dati/eventi.json` e `dati/sedi.json` nella repository. Dopo aver verificato che i file JSON siano validi e che ogni `sede_id` corrisponda a un `id` presente in `sedi.json`, pubblica le modifiche secondo la procedura prevista per il progetto.

## Cosa mostra la pagina

La pagina Programma mostra le schede dei sei eventi, con titolo, immagine, data, orario, categoria e descrizione. La sede di ciascun evento è collegata tramite `sede_id` ai dati di `sedi.json`. La pagina Info e luoghi presenta le tre sedi e i relativi indirizzi.

## Schema Evento–Sede

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
