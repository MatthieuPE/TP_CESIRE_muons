
# Guide Enseignant - TP CESIRES Muons Cosmiques

## Informations générales

**Contact responsable:** Johan Collot 
**Volume horaire:** 16h de TP  
**Lien de présentation:** [Fiche CESIRE](https://chamilo.univ-grenoble-alpes.fr/courses/UGA2630/document/Descriptifs-des-experiences/Fiche-Cesire-Muon.pdf?cidReq=UGA2630&id_session=0&gidReq=0&gradebook=0&origin=)

---

## Séance 1 : Acquisition des données expérimentales

### Déroulement de la séance

#### 1. Introduction

**Questions d'amorce:**
- Les étudiants ont-ils déjà fait de la relativité restreinte ?
- Ont-ils déjà travaillé dans un laboratoire de physique expérimentale ?

**Présentation du TP:**
- Vue d'ensemble : acquisition puis traitement de données
- Présentation des muons cosmiques
- Principe global de l'expérience

#### 2. Bases théoriques à présenter

##### Rayonnement cosmique et production de muons

**Origine des muons cosmiques:**
- Source : rayonnement cosmique (RC) primaire
- Formation de gerbes atmosphériques
- Chaîne de désintégration : $\pi_0 \rightarrow \pi_\pm \rightarrow \mu_\pm$ (première désintégration sur quelques mètres)
- Effets relativistes : contraction des longueurs $L_\mu = L_t/\gamma$ ou dilatation temporelle $T_t = \gamma T_\mu$

**Pourquoi essentiellement des muons ?**
- Masse du muon : 200 fois supérieure à celle de l'électron
- Pouvoir de pénétration élevé dans la matière
- Comparaison : à 100 GeV dans du plomb, un électron parcourt 7 cm contre 59 m pour un muon
- L'électron perd de l'énergie par Bremsstrahlung (rayonnement de freinage)
- Flux de muons : ~1 muon/cm²/min (soit ~1/s traversant un être humain)
- Conséquence : impossibilité de se blinder contre les muons (problème pour les expériences bas bruit, évoquer laboratoire souterrain de Modane)

##### Principe de détection

**Scintillateur plastique:**
- Le muon traverse le scintillateur et perd de l'énergie par diffusion
- Excitation des atomes du matériau
- Désexcitation avec émission de lumière

**Photomultiplicateur (PMT):**
- **Photocathode:** Les photons de fluorescence arrachent des électrons par effet photoélectrique (→ photoélectrons)
- **Dynodes:** Portées à haute tension, elles multiplient le nombre d'électrons par émission secondaire
- **Anode:** Collecte les électrons pour créer un courant mesurable
- Le courant final est proportionnel au nombre de photoélectrons, donc au nombre de photons, donc à l'énergie déposée
- Montrer les PMs de la vitrine

#### 3. Manipulation expérimentale

##### Détection des premiers muons
- Utilisation de l'oscilloscope couplé aux scintillateurs
- Visualisation des signaux

##### Principe de coïncidence

**Questions fréquentes des étudiants:**

*Q: Pourquoi ne pas mesurer directement la différence entre le signal 1 et le signal (1&2&3) ?*  
**R:** L'électronique ne fonctionne pas correctement pour des temps trop courts. On utilise un décalage temporel (shift) que l'on corrigera par calcul. De plus, utiliser le signal en coïncidence comme start permet de ne mesurer que les muons authentiques (réduction du bruit).

*Q: Pourquoi décale-t-on le signal 3 ?*  
**R:** Pour conserver l'ordre temporel 1 → 2 → 3, garantissant que le Δt mesuré correspond toujours à la différence entre les détecteurs 1 et 3 (avec corrélation avec 2).

##### Mesures en positions haute et basse

**Justification de deux positions:**

Le temps mesuré par une unique position dépend fortement de :
- La réponse des détecteurs
- La longueur des câbles
- Les délais électroniques

En utilisant deux configurations différentes, on peut s'affranchir de ces dépendances systématiques du matériel.

**Analyse mathématique:**

L'écart temporel mesuré $X_i$ entre les signaux 1 et 3 s'exprime :

$$X_i = f(\Delta t_i, \text{shifts})$$

Or, $X_i$ dépend également du temps de réponse des détecteurs :

$$X_i = t_i + (t_{\text{detec}}^3 - t_{\text{detec}}^1)$$

Le temps réel de parcours $t_i$ est donc "pollué" par les temps de réponse des détecteurs, qui sont indépendants de la position des scintillateurs.

En effectuant une seconde mesure :

$$X_j = t_j + (t_{\text{detec}}^3 - t_{\text{detec}}^1)$$

On obtient, par différence :

$$\tau = X_i - X_j = t_i - t_j$$

Cette opération élimine les dépendances systématiques du matériel. Les scintillateurs sont placés à des distances différentes pour que $t_i \neq t_j$.

*Q: Pourquoi Δt₂ > Δt₁ ? (slide 14)*  
**R:** C'est juste qu'il ne faut pas confondre le delta1 delta2 du schéma des scintillateurs, de celui du schéma des coincidences. En effet, le décalage qu'on peut mesurer est x ou y. Seuls, ils ne correspondent pas directement au temps physique de parcours du muons, du genre $x=t_\mu +(t_{cable3}-t_{cable1})$, ce qui est donc corrigé en faisant le différence. Et pour comprendre pourquoi delta2>delta1, il faut juste se dire que dans le cas haut / bas les signaux 2 et 3 ne bougent pas, seule le 1 arrive plus tot dans le cas haut que le bas, et donc cela shift le signal stop également, et pas le start, changeant donc la durée du deltat.

##### Procédure d'acquisition

**Configuration:**
1. Brancher les signaux start et stop
2. Connecter la sortie vers le boîtier blanc
3. Depuis le boîtier, relier le câble vers l'ordinateur
4. Lancer le logiciel SpectroTP

**Troubleshooting:**
- Si aucun signal n'est détecté :
  - Vérifier que le fichier de configuration est bien chargé dans SpectroTP
  - Vérifier l'utilisation de l'entrée PKD du Multi-Channel Analyzer
- Si les pics sont trop larges à l'oscilloscope :
  - Vérifier la présence d'une résistance d'adaptation
  - Possibilité de connecter directement l'oscilloscope au PM sans passer par le tableau vert

##### Calibration

**Principe:**
- Générer un signal créneau depuis un PM
- Appliquer un décalage (delay) de quelques ns
- Observer le pic correspondant → établir la correspondance pic ↔ temps
- Répéter avec un second temps
- La réponse linéaire permet d'obtenir la calibration complète

**Attention:** En plus du delay ajouté au signal, il faut prendre en compte la différence de temps introduite par les longueurs de câbles.

#### 4. Questions fréquentes

**Sur le TAC (Time-to-Amplitude Converter):**  
*Q: Pourquoi utiliser un TAC pour mesurer Δt via une conversion en amplitude plutôt que mesurer directement ?*  
**R:** Il faut convertir le signal électronique analogique en signal numérique (canaux) pour l'analyse informatique.

**Sur la durée d'acquisition:**  
*Q: Pourquoi la position haute nécessite-t-elle plus de temps d'acquisition ?*  
**R:** L'angle solide de détection est plus petit en position haute, donc il faut plus de temps pour collecter le même nombre d'événements. La position basse peut être acquise par l'enseignant avant la deuxième séance.

---

## Séance 2 : Estimation de la distance parcourue par simulation Monte Carlo

### Objectif

Estimer par simulation la distribution des distances parcourues par les muons dans les configurations haute et basse.

### Introduction théorique (20 min)

**Question d'amorce aux étudiants:**  
*"Nous voulons obtenir la distribution de la distance parcourue par les muons. De quelles variables cette distance dépend-elle ?"*

**Réponse attendue:** 
- Positions d'impact : $(x_1, y_1)$ sur le premier détecteur
- Positions d'impact : $(x_2, y_2)$ sur le deuxième détecteur (avec coupure/sélection)
- Angles : $\theta$ (angle zénithal) et $\phi$ (angle azimutal)

**Question de suivi:**  
*"Quelles distributions statistiques ces variables suivent-elles ?"*

**Réponse attendue:**
- $(x_1, y_1)$ : distribution uniforme entre 0 et $x_{\max}$, $y_{\max}$
- $\phi$ : distribution uniforme entre 0 et $2\pi$
- $\theta$ : distribution en $\cos^2\theta$ entre 0 et $\pi/2$

**Points clés à présenter:**
1. Montrer le schéma avec la formule trigonométrique donnant la dépendance de $d_\mu$ en fonction des angles
2. Expliquer le biais de détection : certains angles d'incidence sont plus probables que d'autres (flux cosmique en $\cos^2\theta$)
3. Tenir compte de l'acceptance géométrique en estimant les positions sur les deux scintillateurs

### Déroulement de la séance

#### Étape 1 : Génération de nombres aléatoires uniformes 

**Objectifs:**
- Générer des nombres aléatoires suivant une distribution uniforme pour $x_1$, $y_1$, $\phi$
- Tracer les histogrammes des distributions générées
- Vérifier la qualité de la génération

**Points techniques:**
- Utilisation de `numpy.random.uniform()` ou équivalent
- Choix approprié du nombre d'événements (typiquement $10^5$ à $10^6$)

#### Étape 2 : Génération selon une distribution $\cos^2\theta$

**Objectifs:**
- Comprendre la méthode de rejet (rejection sampling)
- Déterminer la constante de normalisation pour la PDF
- Générer des nombres aléatoires suivant $p(\theta) \propto \cos^2\theta$
- Comparer visuellement la distribution obtenue à la PDF théorique

**Méthode de rejet - Explications à donner:**

1. **Principe général:**
   - On veut échantillonner une distribution $p(x)$ non triviale
   - On utilise une distribution uniforme et un test d'acceptation/rejet
   
2. **Application au cas $\cos^2\theta$:**
   - PDF normalisée : $p(\theta) = \frac{3}{2}\cos^2\theta$ pour $\theta \in [0, \pi/2]$
   - Algorithme :
     1. Tirer $\theta$ uniformément dans $[0, \pi/2]$
     2. Tirer $u$ uniformément dans $[0, 1]$
     3. Accepter $\theta$ si $u < \cos^2\theta$, sinon rejeter et recommencer

3. **Validation:**
   - Tracer l'histogramme normalisé des valeurs acceptées
   - Superposer la courbe théorique $\frac{3}{2}\cos^2\theta$
   - Vérifier l'accord statistique

**Extension possible (si temps disponible):**  
Présenter la méthode de la transformée inverse (inverse transform sampling) comme alternative à la méthode de rejet.

#### Étape 3 : Calcul de la distribution des distances

**Objectifs:**
- Utiliser les variables aléatoires générées pour calculer $d_\mu$ pour chaque événement
- Appliquer les coupures géométriques (le muon doit traverser les deux scintillateurs)
- Obtenir la distribution de $d_\mu$ et sa valeur moyenne $\langle d_\mu \rangle$

**Formule géométrique:**
À partir des positions $(x_1, y_1)$ et $(x_2, y_2)$ et de la distance verticale $\Delta h$ :

$$d_\mu = \frac{\Delta h}{\cos\theta}$$

**Points d'attention:**
- Vérifier la cohérence géométrique (muon passant par les deux détecteurs)
- Estimer séparément pour les positions haute et basse
- Conserver les résultats pour la séance 3

---

## Séance 3 : Estimation de la vitesse des muons 

### Objectif

Déterminer la vitesse des muons cosmiques à partir des données expérimentales et des simulations.

### Déroulement de la séance

#### Étapes
1. Ouvrir les data et les afficher
2. Obtenir la fonction de calibration canal-temps
	- Définir le modèle de la calibration (ici linéaire)
	- Ecrire la fonction du modèle avec les paramètre de ce dernier
	- Faire une fonction pour fit le modèle sur les données (chi2 ou scipy.curve)
	- Afficher le fit
3. Obtenir les paramètres décrivant la distribution
	- Définir le modèle (gaussienne avec amplitude, sigma, et moyenne), et ses bornes
	- Faire le fit et obtenir erreur 
	- Comparer le fit aux données
4. Recup code pour distance moyenne pour un ymax xmax et d donné
5. Estimer la vitesse

**Questions de réflexion pour les étudiants:**
- La valeur obtenue est-elle cohérente avec la physique des muons ?
- Que vaut $\gamma = 1/\sqrt{1-\beta^2}$ pour les muons détectés ?
- Quelle serait la distance parcourue sans effets relativistes ?

---

## Séance 4 : Propagation des incertitudes 

### Objectif

Estimer rigoureusement les incertitudes sur la vitesse mesurée et introduire les concepts avancés d'analyse statistique.

### Fondements théoriques

#### Sources d'incertitudes

Les mesures de distance et de temps comportent deux types d'incertitudes :

1. **Incertitudes statistiques** :
   - Nombre fini d'événements détectés
   - Distribution angulaire des muons
   - Prises en compte par la largeur des distributions

2. **Incertitudes systématiques** :
   - Dimensions des détecteurs
   - Calibration
   - Électronique
   - Prises en compte par propagation des erreurs de mesure

#### Stratégie de séparation des effets

**Pour éviter de compter deux fois les mêmes effets :**

**Distance moyenne :**
- Calculée par simulation Monte Carlo
- L'incertitude provient de l'incertitude sur les dimensions physiques ($x_{\max}$, $y_{\max}$, $\Delta h$)
- Estimation : régénérer la simulation avec différentes valeurs de ces dimensions

**Temps moyen :**
- Extrait par ajustement gaussien
- L'incertitude statistique est donnée par : $\Delta\mu = \sigma/\sqrt{N}$ ou directement par l'ajustement
- Cette mesure inclut déjà la dispersion due aux trajectoires variées des muons

**Conséquence :** La dispersion angulaire créant un "étalement" des distances est déjà prise en compte dans $\Delta t$, tandis que $\Delta d$ représente uniquement l'incertitude expérimentale sur les longueurs.

#### Etapes
1. Obtenir formule incertitude vitesse
2. Reflechir source inceritude sur chaque terme
3. Obtenir incertitude sur le fit de la gaussienne
4. Obtenir incertitude sur les distances moyennes en generant plein de fois pour différentes valeurs de xmax, ymax, d.
5. Combiner incertitudes
6. Refaire le point sur le fit : ajouter de prendre en compte les erreurs, en expliquant ce qui est minimisé (un chi2, et expliquer ce que c'est), 
7. Faire minimisation chi2 au lieu de scipy curve
8. Refaire pour les mesures de cette année, en ajoutant la coupure à bas X
9. Donner quelques points qu'on aurait pu faire différemment, par example fit via un likelihood


---


## Checklist enseignant

**Avant la séance 1 :**
- [ ] Vérifier le fonctionnement de l'ensemble de l'expérience
- [ ] Vérifier l'accès des étudiants au laboratoire
- [ ] Préparer introduction aux muons
- [ ] Réserver plateforme TP pour 1 semaine d'acquisition

**Avant la séance 2 :**
- [ ] Vérifier que les données position haute sont acquises (1 semaine)
- [ ] Optionnel : acquérir les données position basse en amont
- [ ] Vérifier les calibrations des étudiants
- [ ] Réserver salle informatique si les élèves n'ont pas d'ordinateurs perso

**Avant la séance 3 :**
- [ ] S'assurer que tous les étudiants ont leurs codes de simulation
- [ ] Vérifier la disponibilité des données complètes
- [ ] Réserver salle informatique si les élèves n'ont pas d'ordinateurs perso

**Avant la séance 4 :**
- [ ] Préparer les discussions sur le $\chi^2$ et les likelihood
- [ ] Réserver salle informatique si les élèves n'ont pas d'ordinateurs perso

