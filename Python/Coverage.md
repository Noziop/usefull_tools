# Coverage

## Qu'est-ce que coverage
Aujourd'hui, je voudrais vous parler d'un outil super utile pour améliorer la qualité de notre code : Coverage.

🔍 Qu'est-ce que Coverage ?
Coverage est un outil qui mesure la couverture de code de vos tests. En d'autres termes, il vous montre quelles parties de votre code sont exécutées par vos tests et lesquelles ne le sont pas.

## 💻 Comment l'installer ?
C'est super simple ! Utilisez pip :
```bash
pip install coverage
```

## 🚀 Comment l'utiliser ?
1. Pour exécuter vos tests avec coverage :

   ```bash
   coverage run -m unittest discover
   ```

2. Pour voir un rapport dans le terminal :

   ```bash
   coverage report
   ```

3. Pour générer un rapport HTML plus détaillé :

   ```bash
   coverage html
   ```
   Cela créera un dossier "htmlcov" avec un fichier index.html que vous pouvez ouvrir dans votre navigateur.

## Astuce

💡 Astuce : Vous pouvez ajouter un fichier .coveragerc à la racine de votre projet pour configurer coverage selon vos besoins.

N'hésitez pas si vous avez des questions ! Coverage est un excellent moyen d'améliorer la qualité de nos tests et de notre code. Bonne journée à tous ! 😊

