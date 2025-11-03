# Scadenzario-hugotheme

Ho creato questo tema perché avevo bisogno di visualizzare i dati delle fatture di vendita in una tabella HTML. È *quasi* uguale a quello vuoto che si crea con il comando `hugo new theme ilmiotema` ([documentazione](https://gohugo.io/commands/hugo_new_theme/)).

Ho solo aggiunto:

- */data/[demo.toml](data/demo.toml)*
- */layouts/_shortcodes/[scadenzario.html](layouts/_shortcodes/scadenzario.html)*

Riempito */assets/css/[main.css](assets/css/main.css)* e modificato *file?* per ottenere una pagina bianca di partenza.

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

È possibile impostare *debug*, *debugInlinea* e *esempio* su `true` inn caso di bisogno.
