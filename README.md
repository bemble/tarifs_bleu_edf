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

## Utilisation

### Home Assistant

Il suffit de configurer l'intégration Restful. Par exemple, pour les tarifs tempo, dans le fichier `configuration.yaml`:

```yaml
rest:
  - resource: https://raw.githubusercontent.com/bemble/tarifs_bleu_edf/main/edf_bleu.json
    method: GET
    scan_interval: 40000
    sensor:
      - unique_id: tarif_kwh_hc_bleu
        name: Tarif Tempo Bleu Heures creuses
        value_template: "{{value_json.tempo['6kva'].prix_kwh_hc_bleu}}"
        unit_of_measurement: EUR/kWh
      - unique_id: tarif_kwh_hp_bleu
        name: Tarif Tempo Bleu Heures pleines
        value_template: "{{value_json.tempo['6kva'].prix_kwh_hp_bleu}}"
        unit_of_measurement: EUR/kWh
      - unique_id: tarif_kwh_hc_blanc
        name: Tarif Tempo Blanc Heures creuses
        value_template: "{{value_json.tempo['6kva'].prix_kwh_hc_blanc}}"
        unit_of_measurement: EUR/kWh
      - unique_id: tarif_kwh_hp_blanc
        name: Tarif Tempo Blanc Heures pleines
        value_template: "{{value_json.tempo['6kva'].prix_kwh_hp_blanc}}"
        unit_of_measurement: EUR/kWh
      - unique_id: tarif_kwh_hc_rouge
        name: Tarif Tempo Rouge Heures creuses
        value_template: "{{value_json.tempo['6kva'].prix_kwh_hc_rouge}}"
        unit_of_measurement: EUR/kWh
      - unique_id: tarif_kwh_hp_rouge
        name: Tarif Tempo Rouge Heures pleines
        value_template: "{{value_json.tempo['6kva'].prix_kwh_hp_rouge}}"
        unit_of_measurement: EUR/kWh
```