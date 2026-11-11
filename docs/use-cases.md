# Use Cases

## 1. Creare Quiz Automat din Materiale de Curs

**Descriere scurtă:** Un profesor încarcă materiale de curs în sistem și primește automat un set de întrebări generate pe baza lor. Profesorul poate edita întrebările generate sau poate adăuga manual altele noi.

### Pre-condiții
- Actorul este un Profesor autentificat în sistem.
- Profesorul dispune de cel puțin un material de curs într-un format acceptat de sistem.

### Flux principal
1. Profesorul selectează opțiunea de „Creare Quiz Automat".
2. Profesorul încarcă unul sau mai multe materiale de curs.
3. Sistemul analizează materialele și generează un set de întrebări.
4. Profesorul vizualizează setul de întrebări generat.
5. Profesorul editează, șterge sau adaugă manual întrebări, după necesitate.
6. Profesorul salvează quiz-ul.

### Flux alternativ
- **2a.** Formatul materialului încărcat nu este acceptat: sistemul afișează un mesaj de eroare, iar profesorul încarcă un alt fișier (revenire la pasul 2).
- **3a.** Sistemul nu poate genera întrebări din materialele furnizate (conținut insuficient): sistemul informează profesorul, iar acesta poate încărca alte materiale sau poate adăuga întrebările manual (continuare de la pasul 5).
- **6a.** Profesorul părăsește pagina fără a salva: sistemul solicită confirmarea; dacă profesorul confirmă, modificările sunt pierdute și quiz-ul nu este salvat.

### Post-condiții
- Quiz-ul este salvat în sistem și este disponibil pentru a fi atribuit studenților.

---

## 2. Gestionare Conturi Utilizatori și Asignare la Cursuri

**Descriere scurtă:** Un administrator adaugă sau elimină conturile profesorilor și ale studenților și îi asignează la cursuri. Doar utilizatorii înregistrați de administrator se pot autentifica în sistem, iar un utilizator are acces doar la cursurile la care a fost asignat.

### Pre-condiții
- Actorul este un Administrator autentificat în sistem.
- Pentru asignare, există cel puțin un curs creat în sistem.

### Flux principal
1. Administratorul selectează opțiunea de „Gestionare Conturi".
2. Administratorul alege acțiunea dorită: adăugare cont, eliminare cont sau asignare la cursuri.
3. Pentru **adăugare**, administratorul introduce datele utilizatorului (nume, e-mail, rol: profesor sau student) și confirmă.
4. Pentru **eliminare**, administratorul selectează un cont existent și confirmă ștergerea.
5. Pentru **asignare**, administratorul selectează un cont existent, alege unul sau mai multe cursuri din lista disponibilă și confirmă asignarea.
6. Sistemul actualizează lista conturilor și asignările la cursuri.

### Flux alternativ
- **3a.** Există deja un cont asociat adresei de e-mail introduse: sistemul afișează un mesaj de eroare, iar administratorul introduce alte date sau anulează operația.
- **3b.** Datele introduse sunt incomplete sau invalide: sistemul indică câmpurile de corectat, iar administratorul le completează (revenire la pasul 3).
- **3c.** După crearea contului, administratorul poate trece direct la asignarea la cursuri (continuare de la pasul 5).
- **4a.** Administratorul anulează confirmarea ștergerii: contul rămâne neschimbat.
- **4b.** Administratorul încearcă să elimine propriul cont de administrator: sistemul refuză operația și afișează un mesaj explicativ.
- **4c.** Contul eliminat este asignat la cursuri: sistemul elimină automat și asignările asociate, fără a afecta quiz-urile sau rezultatele istorice ale cursurilor.
- **5a.** Nu există niciun curs disponibil: sistemul afișează un mesaj corespunzător, iar administratorul poate încheia operația sau poate reveni la alte acțiuni.
- **5b.** Utilizatorul este deja asignat la cursul selectat: sistemul ignoră duplicatul și informează administratorul.
- **5c.** Administratorul retrage o asignare existentă: utilizatorul pierde accesul la cursul respectiv, iar rezultatele deja obținute rămân salvate.

### Post-condiții
- Contul este adăugat sau eliminat din sistem, iar utilizatorul în cauză se poate autentifica, respectiv nu se mai poate autentifica.
- Utilizatorul are acces doar la cursurile la care a fost asignat.

---

## 3. Parcurgere Quiz și Vizualizare Rezultate

**Descriere scurtă:** Un student parcurge un quiz atribuit de profesor și poate consulta ulterior rezultatele obținute.

### Pre-condiții
- Actorul este un Student autentificat în sistem.
- Există cel puțin un quiz disponibil pentru studentul respectiv.

### Flux principal
1. Studentul alege un quiz disponibil și îl începe.
2. Studentul răspunde la întrebările quiz-ului.
3. Studentul trimite quiz-ul spre evaluare.
4. Sistemul calculează scorul și afișează rezultatul.
5. Studentul poate consulta oricând rezultatele obținute, inclusiv răspunsurile corecte.

### Flux alternativ
- **1a.** Nu există niciun quiz disponibil: sistemul afișează un mesaj corespunzător, iar cazul de utilizare se încheie.
- **4a.** Studentul trimite quiz-ul cu întrebări fără răspuns: sistemul avertizează studentul, iar acesta poate reveni la întrebări sau poate trimite quiz-ul oricum.
- **4b.** Timpul alocat quiz-ului expiră (dacă există o limită de timp): sistemul trimite automat răspunsurile completate până în acel moment.
- **4c.** Conexiunea cu sistemul se pierde în timpul parcurgerii: răspunsurile deja date sunt păstrate, iar studentul poate relua quiz-ul după reconectare.

### Post-condiții
- Răspunsurile și rezultatul studentului sunt salvate în sistem.