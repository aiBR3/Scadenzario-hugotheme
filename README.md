# Scadenzario-hugotheme

Ho creato questo tema perché avevo bisogno di visualizzare i dati delle fatture di vendita in una tabella HTML. È *quasi* uguale a quello vuoto che si crea con il comando `hugo new theme ilmiotema` ([documentazione](https://gohugo.io/commands/hugo_new_theme/)).

Ho aggiunto:

- */data/[demo.toml](data/demo.toml)*
- */layouts/_shortcodes/[scadenzario.html](layouts/_shortcodes/scadenzario.html)*

E riempito */assets/css/[main.css](assets/css/main.css)*.

## Istruzioni

1. Creare un nuovo sito con `hugo new site ilmiosito`
2. Aggiungere questo tema nella cartella */themes/*
	- scaricandolo a mano
	- con `git init` e poi `git submodule add https://github.com/aiBR3/Scadenzario-hugotheme.git themes/scadenzario` ([documentazione](https://gohugo.io/getting-started/quick-start/))
3. Configurare il sito per usare il tema, scrivendo in *hugo.toml*:
	```
	theme = 'scadenzario'
	```
5. Aggiungere una pagina, per esempio */content/_index.md*:
	```
	+++
	draft = false
	+++
	
	Lorem ipsum dolor sit amet, consectetur adipiscing elit.
 	
	```
6. Invocare lo shortcode con `{{< scadenzario db="demo" debug=false debugInlinea=false esempio=false >}}` per vedere le fatture in *demo.toml*
	```
	+++
	draft = false
	+++
	
	Lorem ipsum dolor sit amet, consectetur adipiscing elit.
	
	{{< scadenzario db="demo" debug=false debugInlinea=false esempio=false >}}
 	
	```

È possibile impostare *debug*, *debugInlinea* e *esempio* su `true` in caso di bisogno.

## Schema di funzionameno dello shortcode *scadenzario.html*

- legge i 4 parametri impostati dall'utente (*db*, *debug*, *debugInlinea*, *esempio*)
	- risponde con vari messaggi di errore in caso di problemi
- legge i dati dal file TOML indicato dall'utente con `db=""`
- ordina i dati per cliente (alfabetico) > data di decorrenza del contratto (dalla più vecchia) > giorno di inizio della fattura (dalla più recente)
	- ad ogni fattura aggiunge il campo *fattLunghezza* e calcola quanti mesi/celle occupa ogni fattura
- elenca tutti gli anni occupati dai contratti e dalle fatture
	- rimuove i duplicati
	- calcola quante colonne serviranno per disegnare la tabella
- scrive la tabella HTML, una riga alla volta partendo dall'alto, una colonna alla volta partendo da sinistra
	- le righe di intestazione con tutti gli anni e i mesi occupati dalle fatture
	- una riga per ogni cliente
		- una riga per ogni contratto dello stesso cliente
			- una riga per ogni sito appartenente allo stesso contratto
				- una cella vuota per ogni mese non occupato da fatture
				- una cella per ogni fattura, può essere lunga 1 mese o più
	- la riga finale del piè di pagina
- se il debug è attivo, mostra alcune variabili e il loro tipo
- se l'esempio è attivo, mostra la stessa tabella HTML della demo scritta manualmente, utile per confrontare l'HTML pulito con quello generato dallo shortcode.
