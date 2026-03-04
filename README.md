# Déterminants de l'IDH en Afrique subsaharienne
![R](https://img.shields.io/badge/R-276DC3?logo=r&logoColor=white)
![Data Science](https://img.shields.io/badge/Data%20Science-Social%20Sciences-green)

### Analyse économétrique par régression linéaire multiple 



> **Réalisé dans le cadre personnel**  
> **Auteur :** [Ibrahima Bah](https://github.com/bahEzope224)

---

## Problématique

> *Dans quelle mesure le taux d'alphabétisation, l'accès à l'électricité, les dépenses publiques de santé, la mortalité infantile et le PIB par habitant expliquent-ils le niveau de développement humain (IDH) des pays d'Afrique subsaharienne ?*

---

## Données

| Variable | Source | Code WDI |
|---|---|---|
| IDH | PNUD — HDR 2022 | — |
| Taux d'alphabétisation (%) | Banque mondiale | SE.ADT.LITR.ZS |
| Dépenses de santé (% PIB) | Banque mondiale | SH.XPD.CHEX.GD.ZS |
| Accès à l'électricité (%) | Banque mondiale | EG.ELC.ACCS.ZS |
| Mortalité infantile (‰) | Banque mondiale | SP.DYN.IMRT.IN |
| PIB/habitant, PPA (USD) | Banque mondiale | NY.GDP.PCAP.PP.KD |

**Échantillon :** 47 pays d'Afrique subsaharienne — année de référence 2022

---

## Méthodologie

```
Collecte (PNUD + World Bank WDI)
    ↓
Nettoyage et fusion (R / tidyverse)
    ↓
Statistiques descriptives + matrice de corrélation
    ↓
Régression linéaire simple (modèle baseline)
    ↓
Régression linéaire multiple (modèles 2 et 3)
    ↓
Diagnostic : test de Breusch-Pagan, VIF, résidus
    ↓
Interprétation économique et limites
```

---

## Principaux résultats

Le modèle complet (Modèle 3) explique environ **87%** de la variance de l'IDH dans l'échantillon.

- **Alphabétisation** : déterminant le plus significatif — confirme le rôle central du capital humain dans le développement
- **Mortalité infantile** : relation négative forte — les défaillances de santé publique freinent directement le développement humain
- **PIB/habitant (log)** : significatif mais insuffisant seul — la richesse doit s'accompagner d'investissements sociaux
- **Dépenses de santé** : effet non significatif — cohérent avec la littérature sur l'efficacité conditionnelle des dépenses publiques

**Conclusion :** L'éducation et la santé publique apparaissent comme les deux leviers prioritaires pour améliorer l'IDH en Afrique subsaharienne, indépendamment du niveau de richesse des pays.

---

## Structure du repo

```
├── data_afrique_subsaharienne.csv   # Dataset (47 pays, 6 variables)
├── analyse_IDH.R                    # Script R complet (EDA + régressions + diagnostic)
├── rapport_IDH_Afrique.Rmd          # Rapport RMarkdown (compile en HTML ou PDF)
└── output/                          # Graphiques générés (auto-créé à l'exécution)
```

---

## Lancer l'analyse

```r
# Packages requis
install.packages(c("tidyverse", "corrplot", "car", "lmtest", "ggrepel", "knitr", "kableExtra"))

# Exécuter le script
source("analyse_IDH.R")

# Ou compiler le rapport complet (HTML navigable)
rmarkdown::render("rapport_IDH_Afrique.Rmd")
```

---


*Sources : PNUD (2022), Banque mondiale — World Development Indicators (2022)*  
