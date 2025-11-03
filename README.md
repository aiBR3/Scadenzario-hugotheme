# Scadenzario-hugotheme

Questo tema per Hugo è *quasi* uguale a quello vuoto che si crea con il comando `hugo new theme ilmiotema` ([documentazione](https://gohugo.io/commands/hugo_new_theme/)).

Ho aggiunto:

- */data/[demo.toml](data/demo.toml)*
- */layouts/_shortcodes/[scadenzario.html](layouts/_shortcodes/scadenzario.html)*

E riempito */assets/css/[main.css](assets/css/main.css)*

Ho creato questo tema perché avevo bisogno di visualizzare i dati delle fatture di vendita in una tabella HTML.

## Istruzioni

1. Creare un nuovo sito con `hugo new site ilmiosito`
2. Aggiungere questo tema nella cartella */themes/*
	- scaricandolo a mano
	- con `git init` e poi `git submodule add https://github.com/aiBR3/Scadenzario-hugotheme.git themes/scadenzario` ([documentazione](https://gohugo.io/getting-started/quick-start/))
3. Aggiungere una pagina, per esempio */content/_index.md*:
	```
	+++
	draft = false
	+++
	
	Lorem ipsum dolor sit amet, consectetur adipiscing elit.
 	
	```
4. Invocare lo shortcode con `{{< scadenzario db="demo" debug=false debugInlinea=false esempio=false >}}` per vedere le fatture in *demo.toml*
	```
	+++
	draft = false
	+++
	
	Lorem ipsum dolor sit amet, consectetur adipiscing elit.
	
	{{< scadenzario db="demo" debug=false debugInlinea=false esempio=false >}}
 	
	```

È possibile impostare *debug*, *debugInlinea* e *esempio* su `true` inn caso di bisogno.
