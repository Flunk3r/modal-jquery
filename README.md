Un simple module jQuery pour ajouter facilement des modals dans son code JS

# Installation

```html
<!-- Incure jQuery -->
<script src="/js/jquery.min.js"></script>

<!-- jQuery Modal -->
<script type="text/javascript" src="js/lis.modal.js"></script>
<link rel="stylesheet" href="css/lis.modal.css" />
```
Les icones par défauts sont gérer par FontAwesome

# Utilisation

Les modals s'utilisent uniquement dans le code JS, elles ont pour utilité de remplacer les fonctions `alert()` et `confirm()`.
Toutes mes fonctions JS sont incluses dans l'objet `lis` afin de créer une bibliothèque de fonctions.

Attention, contrairement aux fonction `alert()` et `confirm()`, le code qui suit l'initialisation de la modal est executé !

```js
// modal d'information simple (alert())
lis.modal("info","Ceci est une information"); 

// modal d'erreur avec fonction callback à la fermeture
lis.modal("erreur","Une erreur est survenu",function(){	
// onClose
});

// modal de confirmation (confirm()) avec fonction callback onSuccess et onCancel
lis.modal("confirm","Voulez-vous continuer ?",function(){
// onSuccess
},function(){
// onCancel
})
```

# Options

 ```js
lis.modal(type,options,onSuccess,onCancel); 
// type (string) : Type de modal (info|warning|danger|success|default) OU identifiant de la modal
// options (string | object) facultatif : Contenu de la modal OU paramètres d'options
// onSuccess (function) facultatif : Fonction callback executé soit à la fermeture de la modal, soit onSuccess pour le type 'confirm' 
// onCancel (function) facultatif : Fonction callback executé uniquement lors de l'anulation pour le type 'confirm'

default = {
	title : "Information",	// Titre de la modal
	content : "",		// Contenu HTML ou DOM de la modal	
	btn : [{			// Array contenant les bouton d'actions
		id : "lis-close-modal",	// ID du bouton
		content : "Fermer",	// Texte du bouton
		class : "danger",	// class du bouton (info|warning|danger|success|default)
		ico : "times",		// Icone du bouton (FontAwesome)
		close : true,		// Permet de fermer automatiquement la modal lors du clique sur le bouton
		onClick : function(){}	// Fonction à exectuer au clique sur le bouton (avant animation de fermeture)
	}],
	id : "lis-modal",		// ID de la modal
	type : "info",		// Type de la modal (info|warning|danger|success|default)
	icon : "info-circle",	// Icone de la modal (FontAwesome)
	onClose : function(){},	// Fonction à exectuer lors de la fermeture de la modal (après animation)
	onLoad : function(){},	// Fonction à executer lors de l'ouverture de la modal (après animation)
	close : true,		// Permet de fermer automatiquement la modal lors du clique sur le fond
	size : "md",			// Taille de la modal (xs : 300px | md : 500px | lg : 800px)
	animateIn : "fadeInDown",	// Animation d'apparition de la modal (animate.css)
	animateOut : "fadeOutUp",	// Animation de fermeture de la modal (animate.css)
	keyboard : true,		// Activation de la fermeture par le clavier ESC ou ENTER uniquement s'il n'y a qu'un bouton
};
```

# Exemples


```js
// lors d'une requête ajax
$.post("/save.php",{id:1},function(json){

	if(json.hasError)
		return lis.modal("error","Erreur lors de l'enregistrement : "+json.error);
	
	lis.modal("success","Enregirstrement effectué avec succès");
})

// pour confirmer une suppression
$("#del").on("click",function(){

	lis.modal("confirm","Voulez-vous vraiment supprimer cet élément ?",function(){
		$.post("/del.php",{id:1},function(json){
			if(json.hasError)
				return lis.modal("error","Erreur lors de la suppression : "+json.error);

			lis.modal("success","Elément supprimé avec succès");
		})
	})

})
```
