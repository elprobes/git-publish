
# git-publish

`git-publish` è un semplice script Bash pensato per facilitare il salvataggio e la pubblicazione di modifiche effettuate direttamente su un server all'interno di una repository Git.

Nasce per ambienti in cui il codice viene normalmente aggiornato tramite `git pull`, ma dove occasionalmente collaboratori o tecnici possono avere la necessità di modificare alcuni file direttamente sul server.

Lo scopo dello script è evitare che tali modifiche vengano dimenticate o sovrascritte in seguito, automatizzando le operazioni Git più comuni.

---

## Funzionalità

* Verifica di trovarsi all'interno di una repository Git.
* Visualizzazione delle informazioni principali della repository.
* Elenco dei remote configurati.
* Rilevamento automatico delle modifiche locali.
* Richiesta opzionale di una descrizione dell'intervento effettuato.
* Conferma prima della pubblicazione.
* Commit automatico con informazioni su utente, host e timestamp.
* Push verso tutti i remote configurati.
* Logging persistente delle operazioni.
* Output colorato con supporto a Nerd Fonts.

---

## Workflow

Quando viene eseguito, lo script:

1. Verifica che la directory corrente sia una repository Git.
2. Mostra repository, branch, utente e host.
3. Elenca i remote configurati.
4. Esegue `git add -A`.
5. Verifica la presenza di modifiche da committare.
6. Richiede una descrizione opzionale dell'intervento.
7. Chiede conferma all'utente.
8. Crea un commit automatico.
9. Esegue il push verso tutti i remote.
10. Registra il risultato nel file di log.

---

## Esempio di utilizzo

Entrare nella directory della repository:

```bash
cd /var/www/my-project
```

Eseguire:

```bash
git-publish
```

Lo script mostrerà un riepilogo delle informazioni rilevate e guiderà l'utente durante la pubblicazione.

---

## Formato dei commit

I commit vengono creati automaticamente con un messaggio simile al seguente:

```text
[SERVER] Edit by mario on server-prod - 2026-06-12 23:37:10
```

Se viene fornita una descrizione, questa verrà aggiunta come corpo del commit.

Esempio:

```text
[SERVER] Edit by mario on server-prod - 2026-06-12 23:37:10

Corretto il calcolo dell'IVA sulle fatture estere.
```

---

## Log

Tutte le operazioni vengono registrate nel file:

```text
~/.server-save.log
```

Esempio:

```text
[2026-06-12 23:37:10] [INFO] Repository: proxima
[2026-06-12 23:37:10] [INFO] Utente: mario
[2026-06-12 23:37:11] [OK] Commit creato: 2a69b96
[2026-06-12 23:37:12] [OK] Push completato su origin
```

---

## Caso d'uso tipico

Un collaboratore modifica alcuni file direttamente sul server.

Una volta terminato il lavoro, è sufficiente eseguire:

```bash
git-publish
```

Lo script provvederà a:

* salvare le modifiche nella repository Git;
* creare un commit tracciabile;
* pubblicare le modifiche sui remote configurati;
* registrare l'operazione nel log.

In questo modo le modifiche non rischiano di essere dimenticate o sovrascritte durante successivi aggiornamenti del repository.

---

## Requisiti

* Bash
* Git
* Accesso in scrittura ai remote Git configurati
* Terminale compatibile ANSI (consigliato)
* Nerd Fonts (opzionale, per la visualizzazione delle icone)

---

## Licenza

Utilizzo libero.
