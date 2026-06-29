# Portabilité inter-appareils des attaques par canal auxiliaire (DL-SCA)

Étude de la portabilité inter-appareils d'une attaque AES profilée par
apprentissage profond, et évaluation de l'adaptation de domaine adversariale
(DANN) pour la restaurer.


## Résumé

Une attaque profilée récupère la clé AES en quelques centaines de traces sur son
appareil d'origine, mais échoue dès qu'on change d'appareil (problème de
*portabilité*). Ce travail quantifie ce verrou sur la base multi-appareils
AES_PT, puis évalue le DANN comme solution. 


Résultat principal : le DANN aligne
effectivement les représentations entre appareils, mais cet alignement ne se
traduit pas en gain d'attaque fiable — l'avantage est noyé dans la variance et
aucune clé n'est récupérée.

## Données (non incluses dans le dépôt)

- **ASCAD** : https://github.com/ANSSI-FR/ASCAD
- **AES_PT** (« Mind the Portability ») : base multi-appareils, ~14 Go.

Les fichiers de données ne sont pas versionnés. Lancer `AES_PT_light.py` pour
extraire le sous-ensemble non protégé utilisé ici (~2-3 Go).

## Notebooks (ordre d'exécution)

1. `DL_SCA_consolide.ipynb` — validation sur ASCAD + mise en évidence du verrou.
2. `DANN_colab.ipynb` — entraînement du DANN (GPU recommandé).
3. `Recherche_DANN_colab.ipynb` — analyses : distance entre appareils,
   mécanisme d'alignement, robustesse multi-octets.

## Environnement

Voir `requirements.txt`. Les entraînements lourds sont prévus pour Colab (GPU T4).
