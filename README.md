# Git-tutorial
The git tutorial presented by @frafra at the Firefox OS Afternoon, you can find the original at the etherpad: https://etherpad.mozilla.org/git-fxmilano

Homepage di GIT: https://git-scm.com/  
##Requisiti:
  - git
  - meld (consigliato) o il vostro difftool preferito

Prima configurazione: impostare username ed email  
```
$ git config --global user.name "Francesco Frassinelli" # Oppure il vostro nickname
$ git config --global user.email "fraph24@gmail.com"
```

Configurare meld (o il vostro difftool preferito):
```
$ git config --global diff.tool meld
$ git config --global merge.tool meld
```

Inizializzare il repository:
```
$ cd cartella-col-vostro-progetto-fighissimo/
$ git init .
```

A questo punto, bisogna aggiungere i nuovi file:
```
$ git add . # Il punto aggiunge tutti i file nella vostra cartella in maniera ricorsiva
```

Ora, si può verificare quali file sono stati aggiunti:
```
$ git status
```

git status vi suggerisce anche i comandi per rimuovere un file dal repo e altre cosettine carine ;)  
Potete ignorare permanentemente dei file tramite regex (espressioni regolari), creando un file .gitignore nella vostra cartella/repository. Ad esempio:
```
$ echo '*~' > .gitignore
$ echo '*.bak' >> .gitignore
```

(ricordatevi di aggiungete .gitignore)  
Quando eseguirete nuovamente ```git add .```, verranno aggiunti tutti i file ad esclusione di quelli che corrispondono alle espressioni che avete finito.

Per creare un nuovo commit, utilizzare:
```
$ git commit -m "Initial import"
```

Questo comando mostra la diff tra i file presenti e quelli aggiunti (ovvero nella cosidetta area di staging)
```
$ git difftool
```

Questo comando mostra la diff tra i file presenti e quelli dell'ultimo commit (se esiste)
```
$ git difftool HEAD
```

Ora provate a fare una modifica, e ad eseguire git difftool (senza aggiungere i file) ;-)  
Una volta fatte le modifiche, aggiungete i file con il classico git add . e create un nuovo commit. Ok? ;)  
Ora vediamo le modifiche tra l'ultimo commit ed il penultimo commit...
```
$ git difftool HEAD HEAD~1
```

La cronologia si vede con:
```
$ git log
```

Cavolo, abbiamo committato un codice bruttisimo! Correggiamolo (se non l'abbiamo già inviato a mezzo mondo s'intende):  
Facciamo le nostre correzioni, e poi:
```
$ git add .
$ git commit --amend --no-edit
```

Se volessimo cambiare, oltre ai file, anche il nome del commit...
```
$ git commit --amend -m "Fix the world"
```

Vi consiglio di iscrivervi a github, creare un repo, e seguire le istruzioni per poter fare il push del vostro codice ;)  
Ora passiamo a fare un nuovo branch, perché vogliamo sviluppare una nuova feature... 
```$ git branch feature-fighissima```

...e ci spostiamo sulla nuova branch...
```
$ git checkout feature-fighissima
```

Vediamo il risultato con:
```
$ git branch
```

Ora vedremo due branch: il master (il branch principale) e quello appena creato. L'asterisco ci indica su che branch stiamo creando.
Dovremmo avere appena creato un branch parallelo, una diramazione del master. Qui possiamo fare tutte le modifiche che vogliamo e tornare su master quando necessario (sempre però dopo aver creato un commit) per fare un nuovo branch, modifiche o un merge.

Il merge serve a importare le modifiche di un branch in un altro (ma il branch importato continua ad esistere a meno che non venga cancellato con ```git branch -D feature-fighissima```).

Se non volete perdere le modifiche che avete fatto potete usare:
```
$ git stash save
```

Non è un commit, non è una branch, è un "limbo" dove potete tenere delle diff temporanee.

```
$ git stash apply
```
...vi applica la modifica che avevate salvato in precedenza.

In caso di grossi casini, potete tornare allo stato dell'ultimo commit con:
```
$ git reset HEAD --hard
```
