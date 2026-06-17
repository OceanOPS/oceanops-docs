# Argo Survival rate

## Survival rate 1:
For each age, we calculate the ratio between the number of deaths that occurred before this age and the total sample of individuals. Operational floats that have not yet reached this age are counted in the numerator. The denominator remains constant along the curve.

**In French:** `"Pour chaque âge, on calcule le rapport entre le nombre de décès survenus avant cet âge et l'échantillon total d'individus. Les flotteurs opérationnels n'ayant pas encore atteint cet âge sont comptabilisés au numérateur. Le dénominateur reste constant le long de la courbe.`

_Analyse/utilité:_

## Survival rate 2:
For each age, we calculate the ratio between the number of deaths that occurred before this age and the number of operational floats that have reached or exceeded this age. Floats that are alive but have not yet reached this age are not counted in either the numerator or the denominator.

**In French:** `Pour chaque âge, on calcule le rapport entre le nombre de décès survenus avant cet âge et le nombre de flotteurs opérationnels ayant atteint ou dépassé cet âge. Les flotteurs en vie n'ayant pas encore atteint cet âge ne sont comptabilisés ni au numérateur ni au dénominateur.`

_Analyse/utilité: Ce taux de survie permet de calculer l'espérance de vie lorsque tous les flotteurs sont mort. Toutefois, si des flotteurs sont encore vivants, alors ce taux de survie sous-estimera l'espérance de vie de l'échantillon car les vivants ne seront pas pris en compte dans le calcul_

## Survival rate 3:
We focus only on the sub-sample of individuals who are capable of reaching a given age. Then, we calculate the ratio between the number of deaths and survivors among these individuals at that given age. This ratio gives the proportion of deaths among those capable of reaching this age.

**In French:** `On se concentre uniquement sur le sous-échantillon d'individus susceptibles d'atteindre un âge donné. Ensuite, on calcule le rapport entre le nombre de décès et de survivants parmi ces individus pour cet âge donné. Ce rapport donne la proportion de décès parmi ceux capables d'atteindre cet âge.`

_Analyse/utilité: Ce survival rate permet de donner la probabilité d'atteindre l'age suivant si le flotteur à déjà atteind cet age._