Un simple module jQuery pour ajouter facilement des modals dans son code JS

# Installation

```html
<!-- Incure jQuery -->
<script src="/js/jquery.min.js"></script>

<!-- jQuery Modal -->
<script type="text/javascript" src="js/lis.modal.js"></script>
<link rel="stylesheet" href="css/lis.modal.css" />
```

# Utilisation

Les modals s'utilisent uniquement dans le code JS, elles ont pour utilité de remplacer les fonctions `alert()` et `confirm()`.
Toutes mes fonctions JS sont incluses dans l'objet `lis` afin de créer une bibliothèque de fonctions.
```js
lis.modal("info","Ceci est une information");
// lis.modal(type,options);
type (string) : identifiant de la modal
options (string | objet) : paramètres de la modal;
```

# Options
 ```js
 default = {
			title : "Information",
			content : "",
			btn : [{
				id : "lis-close-modal",
				content : "Fermer",
				class : "danger",
				ico : "fa-times",
				close : true,
				onClick : ""
			}],
			id : "lis-modal",
			type : "info",
			icon : "info-circle",
			onClose : function(){},
			onLoad : function(){},
			close : true,
			size : "md",
			animateIn : "fadeInDown",
			animateOut : "fadeOutUp",
			keyboard : true,
};
```
