# Comandi 
modificare un file o la data di ultimo accesso ad un file:
- `> t3` 
- `ls -lt`

	- `cat <3`
	- `rm -i t3`
	- `>t3`
	- `ls -lt`
- Lettura di un file 
	- `more prova.c`
Eseguire un programma .c da compiler di gnu per c
- `$ gcc -o prova -wapp prova.c`
Scrivere cose su prova
- `prova`

da controllare 
- `lc_all=c`
- `export lc_all`

- `lc_collate=c`
- `export lc_collate`

`ls -l`
# Filtro 
Un comando filtro è un programma che riceve in ingresso i dati nello standard input e produce risultati nello standard output, dove gli eventuali errori vengono segnalati sullo standard error
### Comandi filtro
Operano sullo standard output considerando a linee
- `cat`
	- versione filtro del comando cat
	- paginazione dell'input
- `more`
	- simile al cat ma con la paginazione in output
- `sort`
	- ordina le linee dello standard input
	- `sort -r`
		- ordinamento inverso 
	- `sort -f`
		- ignora la distinzione tra lettere maiuscole e minuscole (nell'ASCII le lettere maiuscole vengono prima)
	- `sort -c`
		- evidenzia l'esistenza di elementi in disordine  fermandosi sempre sul primo
		- se no si procede con il comando `echo $?`
	- `sort -C`
		- non fa vedere nulla sullo standard erro, ma per il resto sono uguali 
	- `sort c < nomefile 2> /dev/null`
		- restituisce nulla
	- `sort C < nomefile 2> /dev/null`
		- restituisce nulla
	- `echo $?`
		- da in output un valore `!=0` vuol dire che il comando non ha avuto successo
	- `sort -u`
		- restituisce le righe uniche senza le eventuali ripetizioni 
- `grep stringa`
	- general regular expression print
	- cerca la stringa o cerca il file nello standard input
	- `grep parola < nomefile`
		- restituisce le varie occorrenze della linea in cui si hanno la parola cercata
		- restituisce soltanto le lettere in maiuscolo o minuscolo in base alla `parola`, quindi è case sensitive 
	- `grep -n parola < nomefile`
		- restituisce le varie occorrenze della linea in cui si hanno la parola cercata, includendo il numero della riga grazie alla `-n` 
	- `grep -i parola < nomefile`
		- restituisce le varie occorrenze della linea in cui si hanno la parola cercata, ignorando se le lettere sono maiuscole o minuscole 
	- `grep -v parola < nomefile`
		- riporta tutte le righe che **non contengono** la `parola`
	- `grep '^che' < nomefile`
		- riporta le righe dove è presente la parola ricercata 
	- `grep -i 'p' < nomefile`
		- restituisce le varie occorrenze della linea in cui si hanno la parola cercata, ignorando se le lettere sono maiuscole o minuscole 
	- `grep -i 'a$' < nomefile`
		- restituisce la riga che finisce per la a
	- `grep '\.$' < nomefile`
		- restituisce la riga che finisce per il punto 
- `rev`
	- rovescia le linee dello standard input
	- `rev < nomefile`
		- restituisce la linea in ordine inverso 
			- ad esempio se nella linea è presente sono, restituisce onoS
- `wc`
	- conta caratteri, parole e linee dello standard input
	- `wc < nomefile`
		- restituisce il numero delle linee, parole, caratteri
	- `wc -l < nomefile`
		- restituisce il numero delle linee
	- `wc -l p*`
		- restituisce tutti i file che iniziano per p 
	- `wc -w < nomefile`
		- restituisce il numero delle parole
	- `wc -c < nomefile`
		- restituisce il numero dei caratteri
- `head [-numerolinee]`
	- `head < nomefile`
		- riporta se prime linee del file se esistono, di default restituisce 10
	- `head -1 < nomefile`
		- riporta soltanto una linea se esiste, lo abbiamo limitato a 1
		- `head -n 1 < nomefile`
- `tail [-numero linee]`
	- identico alla head, ma con il twist che inizia dall'ultimo 
	-  `tail < nomefile`
		- riporta le ultime linee del file se esistono, di default restituisce 10
	- `tail -1 < nomefile`
		- riporta soltanto una linea dall'ultimo se esiste, lo abbiamo limitato a 1
		- `head -n 1 < nomefile`
# Omogeneità dispositivi e file 
### Ridirezione in entrata standard input
- `comando-filtro < fileinput `
- `prova < t`
	- permette di scrivere appunti o quello che vuoi in input 
### Ridirezione in uscita standard output
- `comando-filtro > fileoutput`
- `comando-filtro >> fileoutput`
- `prova > t`
	- permette di vedere quello che hai scritto in output
### Ridirezione standard error
- `ls -l z* p*> nomefile`
- `ls -l z* p* 2> /dev/null`
- `ls -l z* p* > nomefile 2>&1`
- `las -l z* p* 2>&1> nomefile`
# Piping dei comandi 
Letteralmente è l'utilizzo del metacarattere **|** che collega l'output di un comando con l'input del comando successivo.
- `ls -l | grep '^d'`
		- lista i file presenti nella cartella ma con il vincolo che i file iniziano con la lettera d 
-  `ls -l | grep '^d' | wc-l`
	- ritorna il numero di linee
-  `ls -l | grep '^d' | tee wc -l`
	- ha riportato lo standard output del grep per poi dare il numero delle linee 
- `ps \ wc -l`
	- si devono contare i processi, wc, sh
	-  `ps | tee temp | wc -l`
- cat p*|more
	- meglio non utilizzarlo, la prof la prende sul personale :/
