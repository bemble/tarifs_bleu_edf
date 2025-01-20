# tarifs_electricite

> Tarifs de l'électricité au format JSON.

Selon les abonnements choisis, le tarif de l'énergie n'évolue que rarement, il est donc plus simple d'avoir ces données en "dure" au format JSON que d'aller parser les données fournie par data.gouv.fr, au format CSV, chaque jour.

Format:
```json
{
    "nom_option": {
        "<puissance>": {"subscription": <prix_abonnement>, "prix_kwh<[plus de details]": <prix du kwh pour cette option, cette puissance>}
        ...
    }
}
```

## edf_bleu.json

Tarif Bleu EDF pour les particuliers, [grille tarifaire](https://particulier.edf.fr/content/dam/2-Actifs/Documents/Offres/Grille_prix_Tarif_Bleu.pdf).

Dernière mise à jour: 20 janvier 2025

## edf_zen_fixe.json

Tarif Zen Fixe EDF pour les particuliers, [grille tarifaire](https://particulier.edf.fr/content/dam/2-Actifs/Documents/Offres/Grille-prix-zen-fixe.pdf).

Dernière mise à jour: 20 janvier 2025 
