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
	- con `git init` e poi `git submodule add https://github.com/aiBR3/Scadenzario-hugotheme.git themes/scadenzario`
3. Aggiungere una pagina, per esempio */content/_index.md*, e scriverci lo shortcode `scadenzario`:
	```
	+++
	draft = false
	+++
	
	{{< scadenzario "demo" >}}
	```
4. Lo shortcode mostrerà i dati di *demo.toml*.
