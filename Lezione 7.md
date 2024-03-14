# Programmazione nello Shell
Ha un proprio linguaggio che può essere interpretato 
- Shell corrisponde a /bin/sh
- utilizzato come prototipo
I loro file terminano sempre con `nomefile.sh`
cose da fare 
- assegnare i diritti di esecuzione
	- `chmod +x F.sh`
	- controllare le lettere dei diritti, ad esempio user, group, owner. all
	- se non si ha directory corrente nel path, utilizzare 
		- `F.sh`
- osservazione 
	- shabang
		- la prima linea di un file comandi deve specificare la shell che deve essere utilizzata per l'interpretazione 
	- invocare direttamente uno shell che lo esegua 
		- `sh F.sh`
- comando 
	- `sh -x` xtrace
		- stampa i comandi e gli argomenti
		- utile per il debug 
# Variabili Shell
In una shell possiamo utilizzare le variabili, che sono rappresentati da una **coppia nome valore** . Non esiste una fase di dichiarazione della variabile 
- Una variabile esiste se c'è l'**espressione di assegnamento** tramite il metacarattere **=**
	- Inoltre non vi deve nessun spazio prima o dopo del simbolo di assegnamento 
- esempi
	- `a=`
		- viene assegnata una variabile ma priva di valore 
	- `a=10`
		- viene assegnata una variabile a che vale 10
Per i commenti utilizzare `#` che continua fino alla fine della linea o riga.
La variabile a dell'esempio ha come valore la stringa costituita da `1` e `0` e non ha valore 10.
- Il valore di una  variabile viene indicato dal nome della variabile preceduto dal **metacarattere** `$` che prende il contenuto all'interno della parola dopo il $
	- `echo home`
		- da in output home
	- `echo $home`
		- da in output quello che è contenuto in home 
# Ambiente in Shell
Sono un sottoinsieme delle **Variabili di Shell**.
Ogni processo shell ha un ambiente di esecuzione che è costituito da un insieme di variabili.
- `env`
	- mostra l'ambiente corrente di ogni processo shell
Quando viene creato un nuovo processo in cui si ha un padre e un figlio, il successore riceve una copia del processo d'ambiente del padre.
- In un processo shell esistono 
	- variabili di ambiente che **possono** essere ereditate
	- variabili di shell che **non** possono essere ereditate 
- `export nome-var` Export:
	- converte una variabile di ambiente in una variabili shell 
	- dopo aver utilizzato questo comando, una variabile di shell diventa una variabile ambiente, che a quel punto farà parte dell'ambiente 
- **Nota bene**
	- **nella Bourne shell**, qualunque modifica ad una variabile ambiente per aver effetto sull'ambiente doveva essere seguita dal comando export per la variabile modificata
# Da controllare es
`cd file-comandi`
`cat prova.sh` --> mostra il contenuto dei file 
`ls -l prova.sh`
`prova.sh`--> mostra il contenuto dei file ma con i metacaratteri funzionanti, ma le variabili di shell non vengono mostrate, quindi basta fare un export per voler vedere il valore di a 

`prova.sh`
`ls -l prova.sh`
`./prova.sh`--> questi 3 comandi vengono inseriti perchè se non è possbile vedere il contenuto del file, dicenfo che il comando non è stato trovato anche se nonostante si trovi nella directory. A quel punto inserire l'ultimo comando per vedere l'output desiderato

`sh -x prova.sh`--> mette in output il contenuto dei file ma inizia con + o - per mostrare il grado di accesso
# Sostituzione / Espansione
- Le sostituzioni:
	- variabili / parametri
		- `x=12`
		- `echo $x`
	- dei comandi
		- i comandi indicati tra ALT+96 (letteralmente :/)sono eseguiti e ne viene espanso il risultato 
	- dei nomi di file 
		- Le wildcard *, **?**, [] sono espanse ai nomi di file nel file system secondo un algoritmo di pattern matching
	`ls -l 'pwd'/$a`
	Le parentesi quadre fa match con qualunque carattere, in nome di file, compreso tra quelli nell'insieme 
	- echo `[azl]*` restituisce file contenente i caratteri
	- `echo [q-s]*` restituisce i file partendo da f a s
	- `echo *[!0-9]` nega il pattern e restituisce gli altri file
	- `echo [a-p, 1-7]*[0,a]`
	- `echo[a-p]*[0,a, 1-7]`
	- `echo [a-z]*`
	- `echo [!a-z]`--> restituisce i numeri  e i file con iniziali maiuscole 
	- `echo [0-9]
	- `echo \*` --> scrive *
	- `echo \*\*\*`-->scrive ***
	- `echo *\**`-->individua il * nel nome di un file *
	- `*[\*\?]*`
	
		- 


