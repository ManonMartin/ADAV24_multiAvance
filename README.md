---
title: "ADAV - Multivarié avancé : Démarrage"
subtitle: "Analyse de données multivariées : Méthodes supervisées et traitement de données -omiques"
---

Les quelques étapes suivantes sont à réaliser avant le début du module ADAV - Multivariié avancé, afin de préparer notre répertoire de travail et de démarrer efficacement ce module.


# Installation des packages R

Excécutez toutes les commandes R de cette section pour tester si les packages nécessaires au module ne sont pas encore installés sur votre ordinateur, et les installer le cas échéant.

## packages du CRAN

```r
# packages to install from CRAN
pkgs_cran <- c(
          "knitr",
          "pander",
          "pls",
          "penalized",
          "factoextra",
          "readxl",
          "gplots",
          "RColorBrewer",
          "MASS",
          "chemometrics",
          "e1071",
          "randomForest",
          "class",
          "rpart.plot",
          "rpart",
          "Epi",
          "caret",
          "corrplot",
          "tidyverse",
          "dplyr",
          "missMDA",
          "circlize",
          "plsVarSel",
          "scales")
          


FUN_install_packages <- function(x){
  if (!requireNamespace(x)) install.packages(pkgs=x, dependencies="Depends")
}

invisible(mapply(FUN_install_packages, pkgs_cran))
  
if (!requireNamespace("Vennerable")){
  install.packages("Vennerable", repos="http://R-Forge.R-project.org",
                 dependencies="Depends")
}
```


Si un message apparait pour mettre à jour les dépendances, répondez toujours par l'affirmative.

## packages de Bioconductor

```r
pkgs_bioc <- c("ALL", "ComplexHeatmap",
               "SummarizedExperiment",
               "limma", "pcaMethods",
               "multtest")


if (!requireNamespace("BiocManager"))
  install.packages("BiocManager")

FUN_test_packages <- function(x){
 !requireNamespace(x)
}

bioc_packages <- mapply(FUN_test_packages, pkgs_bioc)

BiocManager::install(pkgs_bioc[bioc_packages])
```

## Charger tous les packages

Testez enfin si tous les packages peuvent être chargés correctement dans votre session R.

```r
lapply(pkgs_cran, require, character.only = TRUE)
lapply(pkgs_bioc, require, character.only = TRUE)
```

# Structure du répertoire de travail

La structure des dossiers peut être téléchargée depuis cette page sur GitHub : en cliquant sur le dossier zippé `ADAV24_multiAvance.zip` et ensuite "Download raw file" en haut à droite (comme illustré dans `Fig1.png`).

Afin de mieux structurer ce module, nous allons travailler sur un ensemble de dossiers organisés de la façon suivante :  

| nom | description |
| ------|:--------:|
| `0-data` | jeux de données utilisés|
| `1-slides` | slides du cours théorique |
| `2-demos_exercices` | Rmd des démos et exercices|


Le dossier `2-demos_exercices` comporte les sous-dossiers suivants: 

- `a-regression`
- `b-classification`
- `c-testsmultiples`
- `d-omics`



# Données à télécharger 

Les dossiers de données suivants sont à télécharger depuis Moodle (Bibliothèque de données) et à placer dans un dossier nommé `0-data` :

- `farines_animales`
- `qPCR`
- `yeast_proteomics`
- `skin_cancer_proteomics`


