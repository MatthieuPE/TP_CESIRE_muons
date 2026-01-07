#Phd #teaching #python #programmation #TPinfo 

<u>Contacts</u> : 
- Johan Collot, collot@lpsc.in2p3.fr
<u>Nombre heures</u> : 16h (TP)
<u>Liens utiles</u> : [page presentation](https://chamilo.univ-grenoble-alpes.fr/courses/UGA2630/document/Descriptifs-des-experiences/Fiche-Cesire-Muon.pdf?cidReq=UGA2630&id_session=0&gidReq=0&gradebook=0&origin=)

# Séance 1 : prise de données

- voir s'ils ont déjà fait relat, déjà venu dans un labo
- Présenter déroulé global tp : acquisition, puis traitement donnée
- Présenter muons
- Présenter principe global expérience
- Détecter premier muons (oscillo + scintillateur)
- Passer avec des créneaux
- Expliquer principe coincidence
- Expliquer utilité de deux mesures
- Obtenir delta t entre start and stop
- Lancer acquisition
## Explications à donner

### Du rayonnement cosmique aux muons
- Source **RC**
- **Gerbe** et reaction jusqu'a muons ($\pi_0 \rightarrow \pi_\pm \rightarrow \mu_\pm$ where the first decay happens on few meters)
- Calcul relativiste (Contraction longueur $L_\mu=L_t/\gamma$ ou dilation temporelle $T_t = \gamma T_\mu$)
- Pourquoi **essentiellement muons** et non électrons etc : Masse muon 200 fois plus élevée que électron, bcp plus pénétrant dans la matière. L'électron peut faire du Bremstralung (diffusion de l'électron sur une charge, où l'électron rayonne donc, et diffuse de l'énergie). Ceci est différent de la diffusion, qui ne crée aucune nouvelle particule.
Par example, pour une electron et un muon d'une meme énergie de 100GeV traversant du plombs, l'électron parcourt 7cm, contre 59m pour le muons 
- Mais **bcp de muons** ($1/cm^2/min$ ou $1/s$ dans une humain) => problème pour expérience bas bruit car on peut pas se blinder contre
### Fonctionnement experience
#### Scintillateur
Muons traversent scintillateur plastiques, va y perdre de l'énergie par diffusion, et donc exciter les atomes constituant le matériau. Ces derniers vont se desexciter en émettant de la lumière.
#### Photomultiplicateur
Couplé aux scintillateur. Recueille les électrons émis par fluorescence dans le scintillateur, par une **photocathode**. Sur cette dernière les photon vont intéragir par effet **photoélectrique**, en arrachant donc une électron = **photoélectron**. Suit plusieurs **dynodes**, qui sont portées à une tension élevée, de telle sorte que les photoelectrons arrachent d'autre électrons (augmentation courant) => puis **anode** qui recueillent ces électrons pour créer un courant proportionnel. 
Ainsi le courant recueilli est prop au nombre de photoélectrons, qui est prop au nombre de photons, qui est prop à l'énergie déposée.

## Oscillo
- si pic trop larges, possible à cause abscence résistance : prendre T mettre cable (avec adaptateur) et autre cote resistance. Possible brancher direct vers oscillo depuis PM sans passer par tableau vert

## Coincidence
- Pourquoi pas direct différence entre 1 et 1&2&3 (donc start = 1, et stop=1&2&3 au lieu de start=1&2&3 et stop = 1 shifted) ?
Car notre électronique pourrait ne pas bien fonctionner pour des temps trop courts, donc on utilise ce temps shift, donc plus grand, puis on recorrigera ce shift plus tard.

- Pourquoi décale-t-on le signal 3 ?
Car on veut garder l'ordre 1 puis 2 puis 3, de sorte à ce que le delta T mesuré corresponde toujours à la différence entre 1 et 3 (donc que start et stop soient bien obtenus à partir de 1 et 3, avec une simple corrélation avec 2)

## Position haute vs basse
- Pourquoi faire une mesures avec deux positions au lieu de une :

=> Car le delta t mesuré par une unique position garde des dépendances fortes des détecteurs, leur réponse, la taille des cables, qui peut par example introduire des décalages du signal 1 par rapport au 3 par example.
Ainsi, en utilisant deux disposition différentes, on a accès au deltaT corrigé de ces dépendances du matériel utilisé.


- Pourquoi delta t2 > delta t1 (slide 14)

=> C'est juste qu'il ne faut pas confondre le delta1 delta2 du schéma des scintillateurs, de celui du schéma des coincidences. En effet, le décalage qu'on peut mesurer est x ou y. Seuls, ils ne correspondent pas directement au temps physique de parcours du muons, du genre $x=t_\mu +(t_{cable3}-t_{cable1})$, ce qui est donc corrigé en faisant le différence. Et pour comprendre pourquoi delta2>delta1, il faut juste se dire que dans le cas haut / bas les signaux 2 et 3 ne bougent pas, seule le 1 arrive plus tot dans le cas haut que le bas, et donc cela shift le signal stop également, et pas le start, changeant donc la durée du deltat.


Mathématiquement:
On est intéressé par l'écart entre le signal 1 et 3 $X_i$, qu'on obtient à partir d'une différence entre Start and stop $\Delta t_i$ :
$$X_i = f(\Delta t_i,shifts)$$
Or puisque $X_i$ est obtenu à partir du décalage entre deux signaux, il dépend aussi du temps de répondre des deux détecteurs:
$$X_i = t_i + (t_{detec}^3-t_{detec}^1)$$
Ainsi le temps réel parcouru par la particule $t_i$ est pollué par le temps de réponse des détecteurs, qu'on ne connait pas directement, mais qui est indépendant de la disposition du détecteur.
C'est pourquoi on fait une seconde mesure
$$X_j = t_j +(t_{detec}^3-t_{detec}^1)$$
On peut donc obtenir
$$\tau = X_i-X_j=t_i - t_i$$
corrigeant ainsi les différence entre deux détecteur. On place aussi les scintillateurs à des distances différences, de sorte à ce qu'on ne mesure pas les même temps $t_i$ et $t_j$.

## Acquisition

brancher start and stop,
recup output qui va vers boitier blanc, et depuis bloitier plan brancher cable vers ordi. Sur ordi lancer spectroTP (pour position haute)
```ad-warning
- Penser à lancer le fichier de configuration depuis SpectroTP. Cela peut expliquer le problème lorsqu'on n'obtient aucun signal.
- penser aussi à utiliser l'entrée PKD du module Multi-Channel Analyzer
```

## Calibration
Prendre un signal 1 créneau d'un pm, shift de qlq ns, ca donne un pic, donc correspondance pic<=> temps. Et faire la meme pr un second temps. Et la donc réponse linaire donc obtient callibration.

```ad-warning
En plus du delay ajouté au signal, il faut aussi prendre en compte la différence de temps introduit par les cables.
```

## Questions

<u>Sur des étapes du tp</u>

- Pourquoi on doit utiliser un TAC (slide 15) pour avoir le delta T en passant par une conversion à des amplitudes, et non pas directement calculer le delta t ? Car faut convertir signal electronique à signal analytique / canaux
- position haute 1sem car angle solide plus petit donc besoin plus temps pour meme nb data. Et pos basse soit début séance analyse, soit moi meme.

<u>Generales sur déroulé</u> :
- Est ce qu'il montre toutes les slides, ou bien juste celles sur l'intro ? intro, et après fait avec les élèves
- Est ce qu'il a une idée de combien de temps passer sur chaque étapes en gros ? prennent 4h, meme plus court
- Est ce qu'il leur fait visiter des trucs, ou montre des trucs ? pas trop
- Est ce qu'il a le set de données d'autres années ? Oui et il me les a passé
- Est ce qu'ils ont un support autre pour le TP ? non juste slides
- est ce qu'il a du faire des accès pour les étudiants ? Oui


## Informations à donner / regarder en amont
- revoir cours relativité et expérience qui a découvert les muons
- comment fonctionne scintillateur (cf cours detecteur)
- comment fonction PMT (cf cours detecteur)
- pourquoi muons perdent moins d'énergie que les autres particules (cf cours irm)
## Notes sur data
- position basse: localisation du scintillateur du haut = 55cm sur échelle
- problème troncqué : surement threshold

# Séance 2 : estimer numériquement la distance parcourue
delta H haute = 72cm


position basse : y0 = 32.5,
**Objectif**: estimer la distance parcourue par les muons en position basse / haute.

## Etapes
**Explications à donner**:

- Donner objectif séance
- montrer schéma avec formule trigo qui donne la dépendance en fonction des angle pour $d_\mu$.
- Expliquer biais détecteur: certains angle d'incidence capturé par le détecteur sont plus probable que d'autre. Tenir compte en estimant $x_1$ $x_2$ également.
- Poser la questions : on est intéressé par obtenir la distribution de la distance parcourue par les muons. De quels variables / nombres est ce que cela dépend ? (rep : x1,y1 (puis cut avec x2,y2), theta, phi) Quelles distributions ces variables suivent-elles ? (rep : uniform entre 0 et xmax,ymax, et 0, 2pi, puis en cos carré avec theta entre 0 et 2pi)
**Les lancer sur**:
- générer des nombres aléatoires qui suivent une distribution uniforme pour x1, y1, phi.
- plot des histogrammes des distributions générées
- générer des nombres aléatoires qui suivent une densité de probabilité en cos^2. 
	- Expliquer méthode réjection
	- déterminer la constante de normalisation pour avoir la pdf
	- tirer nombre aléatoire dans pdf
	- plot la distribution des valeurs, et la comparer à la pdf théorique
- A partir des nombres aléatoire générés, estimer la distribution des distance (attention)

Si jamais j'ai du temps je peux leur présenter [[Inverse transform - transformée inverse]].
Aussi demander leur valeur pour la calibration, pour que je vérifie en amont ce que ça donne avec leur données.

# Séance 3 : estimer la vitesse du muon
Objectif séance : obtenir la valeur de la vitesse des muons

## Etapes
1. Ouvrir les data et les afficher
2. Obtenir la fonction de calibration canal-temps
	- Définir le modèle de la calibration (ici linéaire)
	- Ecrire la fonction du modèle avec les paramètre de ce dernier
	- Faire une fonction pour fit le modèle sur les données
	- Afficher le fit
3. Obtenir les paramètres décrivant la distribution
	- Définir le modèle (gaussienne avec amplitude, sigma, et moyenne), et ses bornes
	- Faire le fit et obtenir erreur
	- Comparer le fit aux données
4. Recup code pour distance moyenne pour un ymax xmax et d donné
5. Estimer la vitesse

# Séance 4 : estimer les erreurs sur cette vitesse
```ad-warning
Début séance à 9h car ça sera plus court
```

Nos mesures de T contiennent du spreading du aux mesures experimentales (nb d'events, electrononique ...), et dûe aux trajectoires des muons (angle theta, et mesure avec les plaques). Pour ne pas compter deux fois chaque effets, ce qu'on peut faire est:
- Estimer la distance moyenne parcourue par les muons avec simu. Par contre incertitudes taille detecteurs implique qu'on est pas sur de cette valeur moyenne. Donc on peut avoir le spreading sur cette valeur moyenne en generant plusieurs real de la moyenne pour différents valeurs de la taille du detecteur.
- Estimer le temps moyen via le fit. Incertitude donnée par incertitude sur la moyenne ($\Delta \mu = \sigma / \sqrt{N}$), ou directement donnée par l'incertitude sur le fit en donnant les erreurs. Cette mesure prendra donc en compte le  fait que les muons peuvent arriver de tous les côté, et le nombre limité d'évènements mesurés.

On note ainsi que le spreading créant un range de distances pour les muons est pris en compte au niveau du delta T, alors que l'incertitude de la distance est simplement une conséquence de l'incertitude expérimentale sur les longueurs qu'on mesure mal.
	$$V = \frac{d_1-d_2}{t_1-t_2}= \frac{D}{T}$$
	$$\Delta V = V\sqrt{(\frac{\Delta D}{D})^2+(\frac{\Delta T}{T}^2)}$$
	where 
	$$A = A_{low}-A_{up}\text{  and  }\Delta A = \sqrt{\Delta A_{low}^2+\Delta A_{up}^2}$$
	
## Etapes
1. Obtenir formule incertitude vitesse
2. Reflechir source inceritude sur chaque terme
3. Obtenir incertitude sur le fit de la gaussienne
4. Obtenir incertitude sur les distances moyennes en generant plein de fois pour différentes valeurs de xmax, ymax, d.
5. Combiner incertitudes
6. Refaire le point sur le fit : ajouter de prendre en compte les erreurs, en expliquant ce qui est minimisé (un chi2, et expliquer ce que c'est), 
7. Faire minimisation chi2 au lieu de scipy curve
8. Refaire pour les mesures de cette année, en ajoutant la coupure à bas X
9. Donner quelques points qu'on aurait pu faire différemment genre les likelihood

