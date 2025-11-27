# Detecció de Parla Falsa mitjançant Intel·ligència Artificial

Aquest repositori conté el desenvolupament complet d’un sistema capaç de distingir entre àudios reals i sintètics generats per IA. El projecte es basa en un procés rigorós d’aprenentatge automàtic que inclou anàlisi de dades, preprocessament, reducció de dimensionalitat, entrenament de models i selecció de la millor solució predictiva.

---

## Objectiu del projecte

L’objectiu principal és construir un model robust que classifiqui mostres d’àudio com **Real** o **Sintètic**, seguint un procés justificat i metòdic. Per fer-ho, el projecte aborda totes les fases necessàries:

* Anàlisi exploratòria i estadística de variables.
* Gestió de missings, outliers i desbalancejos.
* Normalització i codificació de variables.
* Possible reducció de dimensionalitat amb PCA.
* Entrenament i comparació de diversos models (KNN, Arbre de decisió i SVM).
* Optimització d’hiperparàmetres.
* Avaluació en particions independents i test final.
* Elaboració d’un Model Card per documentar el millor model.

---

## Contingut del repositori

### `deteccio_parla_falsa.ipynb`

Notebook principal amb tot el pipeline:

1. **Anàlisi del dataset**

   * Unificació de variables (per exemple, combinacions de sexe, país i ID) com es mostra a la pàgina 2 de l’informe .
   * Estudi de distribucions, boxplots i balanceig (pàgines 6–8).

2. **Preprocessament**

   * Gestió de missings i outliers amb IQR (pàgines 9–10).
   * Recodificació de variables i normalització diferent per dist. normals i exponencials (pàgines 10–11).
   * Eliminació de variables redundants o sorolloses mitjançant matriu de correlació (pàgines 12–14).
   * Opcional: PCA explicant més del 80% de la variància amb 5 components (pàgina 14).

3. **Modelatge**
   Models implementats i optimitzats:

   * **KNN**
   * **Arbre de decisió**
   * **SVM**
     Cada model inclou selecció d’hiperparàmetres, mètriques i corbes ROC (pàgines 16–26).

4. **Selecció del millor model**
   L’SVM és seleccionat com el millor, amb AUC-ROC de 0.80 en el test final (pàgines 22–27).

5. **Model Card**
   Documentació formal del model final: objectiu, dades, mètriques, biaixos, limitacions i recomanacions (pàgines 27–30).

---

## Models implementats

### KNN

Model basat en la distància entre veïns. Ha obtingut una millora significativa quan es treballa sense PCA (AUC-ROC = 0.87).

### Arbre de decisió

Model interpretable, amb millores també quan s’utilitzen totes les variables originals (AUC-ROC = 0.84).

### SVM

Model guanyador, capaç de capturar fronteres no lineals amb kernel RBF.

* Amb totes les variables: **AUC-ROC = 0.90 (validació)** i **0.80 (test final)**.
* És el model escollit per la solidesa i consistència dels resultats.

---

## Estructura recomanada del repositori

```
/data/                  # Datasets utilitzats (train_csv, test_csv, smile_csv)
/notebooks/             # Notebook principal del projecte
/models/                # Arxius guardats del model (si escau)
/figures/               # Gràfics generats (ROC, confusió, correlacions)
/README.md
```

---

## Requisits

Llibreries principals utilitzades:

```
numpy
pandas
matplotlib
seaborn
scikit-learn
```

Instal·lació (si s’afegeix `requirements.txt`):

```
pip install -r requirements.txt
```

---

## Conclusions del projecte

Segons els resultats reportats a l’informe (pàgines 22–27) :

* Treballar **sense PCA** millora substancialment el rendiment dels models.
* L’SVM és el model amb millor capacitat de separació entre veus reals i sintètiques.
* La pipeline proposada permet una classificació fiable i generalitzable.
* El sistema és aplicable a tasques de verificació i seguretat basades en veu, amb les limitacions descrites.

---

## Autora

**Paula Justo Gili**
Grau en Intel·ligència Artificial – Universitat Politècnica de Catalunya

