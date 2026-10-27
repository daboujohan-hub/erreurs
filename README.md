# Base d'erreurs

Une base d'erreurs pour téléphones et applications, expliquées simplement en français.

Chaque fiche explique :

- ce que la personne voit à l'écran ;
- quand l'erreur apparaît (téléphone, tablette, appareil Android de voiture) ;
- pourquoi elle apparaît ;
- comment la corriger, pas à pas ;
- un conseil de sécurité ;
- une illustration (ou une vraie capture d'écran).

Une barre de recherche permet de retrouver une erreur en tapant quelques mots (« batterie », « écran noir », « ne répond plus »). Elle accepte les petites fautes de frappe et surligne les mots trouvés.

Les erreurs sont classées en 8 catégories (boutons en haut de la page) : applications, installation, stockage, batterie, réseau, écran et son, sécurité, autres appareils.

**Site en ligne :** https://daboujohan-hub.github.io/erreurs/

**Développeur :** https://daboujohan-hub.github.io

## Contenu

52 erreurs documentées, par exemple :

- l'application s'arrête systématiquement, ne répond plus, se ferme sans message ;
- stockage plein, batterie, chauffe, lenteur ;
- APK : « Application non installée », « Analyse du package impossible » ;
- Wi-Fi, réseau, SMS, Bluetooth, Play Store, compte Google ;
- arnaques par SMS et faux agents Mobile Money ;
- télévision et décodeur (Incompatibilité HDMI) ;
- comprendre les autorisations des applications (caméra, micro, contacts, position) ;
- erreurs fréquentes dans Termux.

## Organisation des fichiers

```
erreurs/
├── index.html              le site (ne change plus)
├── confidentialite.html    la politique de confidentialité
├── fiches/
│   ├── liste.json          la liste des fiches
│   ├── 1.json
│   ├── 2.json
│   └── ...
└── images/
    ├── erreur-1.png
    ├── erreur-2.png
    └── ...
```

Chaque erreur est un fichier dans `fiches/` (une fiche = un fichier `.json`). La page lit ces fichiers et les affiche. Pour ajouter une erreur, il n'y a pas besoin de modifier `index.html`.

## Ajouter une nouvelle erreur

1. Crée le fichier `fiches/53.json` (le numéro suivant) avec ce modèle :

```json
{
  "numero": 53,
  "titre": "Titre court de l'erreur",
  "categorie": "Applications et performance",
  "message": "Le message affiché à l'écran",
  "image": "images/erreur-53.png",
  "video": "",
  "motsCles": "mots que les gens peuvent taper pour la chercher",
  "quand": ["Quand elle apparaît."],
  "explication": "Ce qui se passe, en termes simples.",
  "causes": ["Première cause.", "Deuxième cause."],
  "solutions": ["Première étape.", "Deuxième étape."],
  "securite": "Conseil de sécurité."
}
```

Le champ `categorie` range la fiche dans un des boutons du haut de la page : réutilise le nom exact d'une catégorie existante (ou crée-en une nouvelle). Champs facultatifs : `video`, `commande` et `commandeNote` (une commande à tester, avec son explication).

2. Ajoute l'image dans `images/` sous le nom `erreur-53.png`. Sans image, la fiche s'affiche quand même.
3. Ajoute `"53.json"` à la fin de `fiches/liste.json`. **Cette étape est obligatoire sur le site en ligne.**
4. Envoie les changements :

```
git add .
git commit -m "Ajout de l'erreur 53"
git push
```

## Utiliser le site sur son téléphone avec Termux

```
pkg install python git -y
cd ~/erreurs
python -m http.server 8080
```

Puis ouvre `localhost:8080` dans Chrome. Garde Termux ouvert pendant que tu utilises le site. Ne double-clique pas sur `index.html` : la page doit être ouverte par le serveur.

## Confidentialité

Le site ne collecte aucune donnée personnelle, n'utilise ni cookies, ni statistiques, ni publicité. Voir `confidentialite.html`.

## Remarques sur les images

Les images des erreurs 1, 2, 32, 45, 46, 47, 48, 49 et 50 sont de vraies captures ou photos d'écran. Les autres sont des **illustrations explicatives**. Pour remplacer une illustration par une vraie capture, enregistre la capture sous le même nom (par exemple `images/erreur-5.png`).

## Avertissement

Ces fiches sont données à titre d'information. Avant une action importante (réinitialisation, désinstallation, réparation), sauvegarde tes données. N'installe des applications que depuis des sources de confiance.
