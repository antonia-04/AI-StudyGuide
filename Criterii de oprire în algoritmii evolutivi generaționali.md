
Într-un algoritm evolutiv, procesul evolutiv rulează pe parcursul mai multor **generații**. Pentru a preveni rularea infinită sau ineficientă, trebuie definit un **criteriu de oprire**.


### Criterii uzuale de oprire:

1. **Identificarea unei soluții optime sau satisfăcătoare**
    - Dacă o soluție atinge o valoare de fitness dorită (considerată optimă sau suficient de bună), algoritmul se oprește.
    - Este un **criteriu valid și des folosit**.
2. **Atingerea unui număr maxim de generații**
    - Se stabilește un prag (ex: 1000 de generații).
    - Este cel mai des utilizat în practică, indiferent de calitatea soluțiilor.
3. **Lipsa de îmbunătățire a fitness-ului pe un anumit număr de generații**
    - Dacă soluțiile nu se îmbunătățesc un număr de generații la rând, algoritmul se poate opri.
4. **Atingerea unui timp limită de execuție**
    - Algoritmul se oprește după un timp maxim alocat.
    

### Criterii **incorecte sau nefolosite**:

- **Atingerea unui număr maxim de indivizi în populație**  
    → Fals: dimensiunea populației este stabilită **dinainte** și **nu crește** în timpul rulării.
    
- **Explorarea completă a spațiului de căutare**  
    → Fals: algoritmii evolutivi sunt **euristici**, deci nu explorează toate combinațiile posibile (ca în căutarea exhaustivă).
    

### Concluzie:

> **Un criteriu valid de oprire într-un algoritm evolutiv generațional este identificarea soluției optime.**  
> Alte criterii valabile includ atingerea unui număr maxim de generații sau stagnarea fitness-ului.
