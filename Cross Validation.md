
![[Pasted image 20250610173740.png]]

Cross-validation (validare încrucișată) reprezintă o tehnică statistică utilizată pentru evaluarea și compararea modelelor de învățare automată. Obiectivele principale sunt:

1. Estimarea performanței de generalizare a unui model
2. Reducerea riscului de supraadaptare (overfitting)
3. Furnizarea unei evaluări robuste cu utilizare eficientă a datelor
![[Pasted image 20250610174105.png]]
### Fundamente Teoretice

#### Problema Evaluării Naive

Evaluarea performanței pe același set de antrenament conduce la estimări părtinitoare:

$\text{Error}_{\text{train}} = \frac{1}{n}\sum_{i=1}^{n} L(y_i, \hat{f}(x_i))$

unde $L$ este funcția de pierdere, iar $\hat{f}$ este modelul antrenat pe întreg setul.

#### Soluția Cross-Validation

Principiul de bază:

1. Partitionarea datelor în subseturi
2. Antrenarea iterativă pe subseturi complementare
3. Validarea pe subsetul exclus

#### Tipologii de Cross-Validation

##### 1. k-Fold Cross-Validation

Algoritm:
1. Împarte datele în k subseturi disjuncte de dimensiuni egale ($D_1, ..., D_k$)
2. Pentru fiecare $i = 1,...,k$:
   - Antrenează modelul pe $D \setminus D_i$
   - Evaluează pe $D_i$
3. Calculează media performanțelor

Formal:

$\text{CV}_{(k)} = \frac{1}{k} \sum_{i=1}^{k} \text{Error}_i$

unde $\text{Error}_i = \frac{1}{|D_i|} \sum_{(x,y)\in D_i} L(y, \hat{f}^{-i}(x))$

##### 2. Leave-One-Out Cross-Validation (LOOCV)

Caz particular al k-fold CV cu $k = n$:

$\text{LOOCV} = \frac{1}{n} \sum_{i=1}^{n} L(y_i, \hat{f}^{-i}(x_i))$

##### 3. Stratified k-Fold

Menține distribuția claselor în fiecare fold. Important pentru:

- Seturi de date dezechilibrate
- Probleme cu distribuții neuniforme

##### 4. Time Series CV

Variante specializate:
- Rolling window
- Expanding window

#### Proprietăți Statistiche

##### Bias-Varianță Trade-off

- **LOOCV**: Bias mic, varianță mare
- **k-Fold (k=5,10)**: Bias moderat, varianță mică

##### Consistență

Sub anumite condiții de regularitate, estimatorul CV este consistent pentru:

1. Seleția modelului
2. Estimarea erorii de generalizare

#### Aplicații Practice

##### 1. Seleția Modelului

Compararea performanțelor multiple modele:

$\text{Model}_{\text{opt}} = min_{m \in \mathcal{M}} \text{CV}_m$

##### 2. Tuning de Hiperparametri

Optimizarea parametrilor $\lambda$:

$\lambda_{\text{opt}} = min_{\lambda} \text{CV}(\lambda)$

##### 3. Evaluarea Finală

Estimarea erorii de generalizare pentru modelul selectat.

#### Considerații Avansate

##### Variante Hibridizate

1. **Nested Cross-Validation**:
   - CV extern pentru evaluare
   - CV intern pentru selecție model

2. **Repeated k-Fold**:
   - Execută multipli k-Fold cu reshuffling
   - Reduce varianța estimării

##### Limitări și Pitanje

1. Dependența de structura datelor
2. Cost computațional pentru seturi mari
3. Presupunerea de independență a observațiilor

#### Analiza Teoretică

#### Eroarea de Generalizare

Relatia cu CV:

$\mathbb{E}[\text{Error}_{\text{gen}}] \approx \mathbb{E}[\text{CV}] + \frac{\text{Complexitate Model}}{n}$

##### Convergență

Pentru $n \to \infty$ și $k$ fix:

$\text{CV}_{(k)} \to \text{Error}_{\text{gen}}$ aproape sigur

#### Concluzii

Cross-validation reprezintă o unealtă fundamentală cu proprietăți statistice bine caracterizate, oferind:

1. Estimări robuste ale performanței
2. Mecanisme de selecție obiectivă
3. Protecție împotriva supraadaptării

Alegerea schemei de CV trebuie să țină cont de:
- Natura datelor
- Dimensiunea setului
- Complexitatea modelului
