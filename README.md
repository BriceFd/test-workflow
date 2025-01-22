# Workshop Node CI
- On créer un répertoire sur Github, pensez à mettre le gitignore pour Node et ajouter le Readme.md
- Clonez le repo en local
- Faite la commande npm init
- Ajoutez un fichier index.js (même vide)
- Ensuite, installez jest avec la commande npm i jest
- Ajoutez un dossier __tests__
- Puis un fichier index.spec.js dans ce dossier avec le contenu 
```
test("hello_world", () => {
    expect(true).toBe(false)
})
```
- Vérifiez que tout fonctionne bien avec la commande npx jest
- Ensuite installez eslint avec npm i eslint
- Initialiser eslint avec npx eslint --init (Choisir syntax, commonjs, none, no, Node, Yes, npm)
- On modifie le contenu du fichier eslint.config.mjs avec
```
import globals from "globals";

export default [
    {
        languageOptions: {
            ecmaVersion: 2022,
            sourceType: "module",
            globals: {
                ...globals.browser,
                ...globals.node,
                myCustomGlobal: "readonly"
            }
        }
        // ...other config
    }
];
```
- On ajoute une entrée "type": "module" dans le package.json
- On fait un petit npm ci
- On fait npx eslint . --debug
- Remplacer dans le package.json dans la clé script par : 
```
    "test": "jest",
    "build": "node index.js",
    "lint": "eslint ."
```
- Faites un add + Commit + push
- Ensuite à vous d'aller dans github actions pour créer un workflow Node (simple) et y intégrer l'analyse eslint.
- A vous de chercher comment créer le fichier pour gérer votre workflow (dans .github/workflows)
- Pensez à mettre un true.toBe(true) dans votre test pour que la CI passe
- Et c'est fini