# TP CESIRES - Muons Cosmiques

## À propos

Ce dépôt toryconstitue une base pédagogique pour le **TP CESIRES sur la mesure de la vitesse des muons cosmiques**. Il est destiné aux enseignant·e·s et peut être modifié et enrichi au fil des années.

**Durée totale :** 16 heures de TP réparties en 4 séances  
**Responsable :** Johan Collot  
**Lien de présentation :** [Fiche CESIRE](https://chamilo.univ-grenoble-alpes.fr/courses/UGA2630/document/Descriptifs-des-experiences/Fiche-Cesire-Muon.pdf?cidReq=UGA2630&id_session=0&gidReq=0&gradebook=0&origin=)

## Structure du dépôt

- **`notebooks/`** : codes d'analyse de données pour les étudiants
- **`data/`** : jeux de données des années précédentes (utiles en cas de problème lors de l'acquisition)
- **`Ressources/`** : notes et documentation pour faciliter l'organisation des séances par l'enseignant·e

## Pour les futurs enseignant·e·s

Ce dépôt est conçu pour être **modifié et enrichi** au fil des années. N'hésitez pas à :
- Améliorer les notebooks et leur documentation
- Ajouter de nouveaux jeux de données (créer un dossier `data/data_XXXX/`)
- Enrichir le guide enseignant avec vos retours d'expérience
- Proposer de nouvelles analyses ou extensions
- etc...

### Workflow Git recommandé

Pour des modifications importantes, travaillez sur une branche dédiée :

```bash
git checkout -b nouvelle-version-2027
# Développer et tester vos modifications
git add .
git commit -m "Description des modifications"
git push origin nouvelle-version-2027
# Merger dans main quand prêt
```

## Prérequis techniques

**Pour les étudiants :**
- Python 3.8+
- Bibliothèques : `numpy`, `matplotlib`, `scipy`, `pandas`
- Jupyter Notebook ou JupyterLab
