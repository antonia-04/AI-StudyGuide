### Eroarea totală a unui model ML

În învățarea automată, scopul este să obținem modele care **generalizează bine** – adică au performanțe bune nu doar pe datele de antrenament, ci și pe date noi, nevăzute.

Eroarea totală poate fi împărțită în trei componente:

$Eroare_{totală} = Bias^2 + Variance + Eroare_{ireductibilă}$

- **Bias** – eroare sistematică: cât de departe este predicția medie față de valoarea reală.
- **Variance** – sensibilitatea modelului la fluctuațiile datelor de antrenament.
- **Eroarea ireductibilă** – zgomotul din date care nu poate fi eliminat (ex: măsurători greșite).
![[Pasted image 20250610172607.png]]

![[Pasted image 20250610172623.png]]

#### Bias

Un model cu **bias mare**:

- presupune o relație prea simplă între date
- nu învață suficient din datele de antrenament
- conduce la **underfitting** (subînvațare)

Exemplu: folosirea unei funcții liniare pentru date care au o relație evident nelineară.

#### Variance

Un model cu **variance mare**:

- învață prea mult din detaliile datelor de antrenament
- este foarte sensibil la zgomot și schimbări minore
- conduce la **overfitting** (supraînvățare)

Exemplu: o funcție polinomială de ordin foarte mare care se potrivește exact pe fiecare punct de antrenament.

#### Seturi de antrenament și testare

- **Training set** – folosit pentru a învăța parametrii modelului.
- **Testing set** – folosit pentru a evalua cât de bine generalizează modelul.

Un model care merge foarte bine pe setul de antrenament, dar prost pe cel de test, suferă de **overfitting**.

#### Underfitting și Overfitting

|Situație|Bias|Variance|Performanță|
|---|---|---|---|
|Underfitting|mare|mică|slabă|
|Overfitting|mic|mare|slabă|
|Generalizare bună|mică|mică|bună|

#### Bias mare vs Variance mare

- Bias mare: model prea rigid, nu învață corect
- Variance mare: model prea flexibil, învață inclusiv zgomotul

Scopul este un **compromis între bias și variance** – numit _bias-variance trade-off_.

#### Regularizare

Regularizarea este o tehnică folosită pentru a **reducerea overfitting-ului**, penalizând modelele prea complexe.

#### Tipuri de regularizare:

- **L1 (Lasso)** – promovează modele sparse (unele coeficiente devin exact 0)
- **L2 (Ridge)** – penalizează coeficienții mari, dar nu-i elimină complet

Funcția de cost devine:

$J(\mathbf{w}) = MSE + \lambda \cdot R(\mathbf{w})$

unde $R(\mathbf{w})$ este termenul de regularizare, iar $\lambda$ controlează influența sa.

#### Bagging (Bootstrap Aggregating)

Tehnică pentru reducerea **variance-ului**:

- Antrenăm mai multe modele pe subseturi diferite ale datelor (obținute prin bootstrap)
- La final, agregăm rezultatele (medie sau vot majoritar)

Exemplu: **Random Forest** (bagging de arbori de decizie).

#### Boosting

Tehnică pentru reducerea **bias-ului**:

- Construiește modele secvențial, fiecare model nou corectând erorile celor anterioare
- Exemple greu de clasificat sunt accentuate

Exemple: **AdaBoost**, **Gradient Boosting**, **XGBoost**


#### Concluzie

Un model bun de Machine Learning:

- are **bias mic** și **variance mică**
- **generalizează bine** pe date noi
- folosește tehnici ca regularizarea, bagging sau boosting pentru echilibru

Alegerea corectă a complexității modelului și a metodelor de antrenare este esențială pentru performanță ridicată.