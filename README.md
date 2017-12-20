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
 default = {
	title : "Information",	// Titre de la modal
	content : "",		// Contenu HTML ou DOM de la modal	
	btn : [{			// Array contenant les bouton d'actions
		id : "lis-close-modal",	// ID du bouton
		content : "Fermer",	// Texte du bouton
		class : "danger",	// class du bouton (info|warning|danger|success|default)
		ico : "times",	// Icone du bouton (FontAwesome)
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
