# Git Publish

Git Publish è un piccolo strumento Bash pensato per semplificare la pubblicazione di modifiche effettuate direttamente su un server.

L'obiettivo è permettere anche a collaboratori con poca esperienza di Git di salvare e pubblicare correttamente le modifiche apportate al codice, riducendo il rischio di perdere lavoro o sovrascrivere cambiamenti effettuati sul server.

---

## Caratteristiche

* Verifica che la directory corrente sia una repository Git valida
* Verifica la configurazione Git dell'utente (`user.name` e `user.email`)
* Mostra informazioni sulla repository corrente
* Elenca automaticamente i remote configurati
* Aggiunge automaticamente tutte le modifiche (`git add -A`)
* Mostra i file che verranno inclusi nel commit
* Consente di specificare un messaggio di commit personalizzato
* Consente di aggiungere una descrizione opzionale
* Richiede conferma prima di procedere
* Effettua il commit delle modifiche
* Esegue il push verso tutti i remote configurati
* Mantiene un log persistente delle operazioni
* Consultazione avanzata del log tramite `fzf` (se installato)

---

## Installazione

Rendere eseguibile lo script:

```bash
chmod +x git-publish
```

Installarlo in una directory presente nel `PATH`, ad esempio:

```bash
sudo cp git-publish /usr/local/bin/
```

oppure:

```bash
mkdir -p ~/.local/bin
cp git-publish ~/.local/bin/
```

Assicurarsi che `~/.local/bin` sia presente nel proprio `PATH`.

---

## Utilizzo

Posizionarsi all'interno di una repository Git:

```bash
cd /percorso/della/repository
```

Eseguire:

```bash
git-publish
```

---

## Flusso operativo

Git Publish esegue automaticamente i seguenti passaggi:

1. Verifica della repository Git
2. Verifica della configurazione Git dell'utente
3. Analisi delle modifiche presenti
4. Visualizzazione dei file modificati
5. Richiesta del messaggio di commit
6. Richiesta della descrizione opzionale
7. Conferma dell'operazione
8. Creazione del commit
9. Push verso tutti i remote configurati
10. Registrazione dell'intera operazione nel log

---

## Messaggio di commit

Se non viene specificato alcun messaggio, Git Publish genera automaticamente un titolo simile al seguente:

```text
[SERVER] Edit by mario on server-prod - 2026-06-14 09:15:42
```

---

## Log

Tutte le operazioni vengono registrate nel file:

```text
~/.local/state/git-publish.log
```

Ogni esecuzione viene salvata come una sessione separata:

```text
[SESSION] START ------------------------------------
...
[SESSION] END   ------------------------------------
```

Questo rende il log facilmente leggibile sia da strumenti automatici sia da esseri umani.

---

## Consultazione del log

Per visualizzare il log:

```bash
git-publish logs
```

### Priorità dei visualizzatori

Git Publish utilizza automaticamente il miglior visualizzatore disponibile:

1. `fzf`
2. `bat`
3. `less`
4. `cat`

---

## Ricerca nel log con fzf

Se `fzf` è installato:

```bash
git-publish logs
```

aprirà una vista interattiva con:

* Ricerca fuzzy
* Filtri avanzati
* Preview della sessione completa
* Evidenziazione della riga selezionata
* Colorazione dei livelli di log

### Esempi

Mostrare solo errori:

```text
ERROR
```

Escludere le righe informative:

```text
!INFO
```

Cercare operazioni relative a un utente:

```text
brotech
```

Cercare commit o push:

```text
commit | push
```

---

## Livelli di log

| Livello | Significato                        |
| ------- | ---------------------------------- |
| SESSION | Inizio/Fine esecuzione             |
| INFO    | Informazioni generali              |
| OK      | Operazione completata con successo |
| WARN    | Avvisi                             |
| ERROR   | Errori                             |

---

## Requisiti

### Obbligatori

* Bash
* Git

### Opzionali

* fzf
* bat
* less

L'assenza dei componenti opzionali non impedisce il funzionamento dello script.

---

## Filosofia

Git Publish non sostituisce Git.

Git Publish automatizza una serie di operazioni comuni e ripetitive per ridurre gli errori umani durante modifiche effettuate direttamente su un server.

L'obiettivo è rendere semplice e sicuro il salvataggio delle modifiche senza richiedere una conoscenza approfondita di Git da parte degli utenti finali.

---

## Licenza

Utilizzo libero.
