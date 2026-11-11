# Requirements

## Cerințe Funcționale

### 1. Autentificare bazată pe roluri
**Prioritate:** Must have

**Descriere:** Utilizatorii se autentifică cu e-mail și parolă și sunt direcționați către interfața specifică rolului lor (administrator, profesor sau student). Doar conturile create de administrator se pot autentifica.

**Justificare prioritate:** Este baza segregării platformei pe roluri și a controlului accesului, obiectiv declarat al proiectului.

### 2. Gestionarea băncii de întrebări
**Prioritate:** Must have

**Descriere:** Profesorul adaugă, editează și șterge întrebări, le clasifică pe categorii și niveluri de dificultate și atașează o explicație pentru feedback.

**Justificare prioritate:** Banca de întrebări stă la baza tuturor quiz-urilor și a feedback-ului manual.

### 3. Creare manuală de quiz-uri
**Prioritate:** Must have

**Descriere:** Profesorul compune un quiz selectând întrebări din banca de întrebări și îl face disponibil studenților.

**Justificare prioritate:** Este funcționalitatea centrală a platformei și condiția pentru ca studenții să poată exersa.

### 4. Parcurgerea quiz-urilor de către student
**Prioritate:** Must have

**Descriere:** Studentul alege un quiz disponibil, răspunde la întrebări, îl trimite și primește scorul final.

**Justificare prioritate:** Răspunde direct problemei de la baza proiectului: evaluarea realistă a nivelului de pregătire al studentului.

### 5. Feedback manual la răspunsuri
**Prioritate:** Must have

**Descriere:** Pentru un răspuns incorect sau incomplet, studentul vede explicația atașată de profesor întrebării respective.

**Justificare prioritate:** Este marcat obligatoriu în documentul de proiect și transformă quiz-ul într-un instrument de învățare.

### 6. Generarea automată de quiz-uri cu LLM
**Prioritate:** Should have

**Descriere:** Profesorul încarcă materiale de curs și primește un set de întrebări generat de un LLM, pe care îl poate edita, completa manual sau șterge înainte de salvare.

**Justificare prioritate:** Este un obiectiv declarat al proiectului și aduce un avantaj major în timp economisit, dar platforma funcționează și fără el.

### 7. Analiză SWOT a performanțelor academice
**Prioritate:** Could have

**Descriere:** Pe ecranul principal, studentul vede o sinteză a performanțelor sale împărțită în puncte tari, puncte slabe, oportunități și provocări.

**Justificare prioritate:** Este marcată opțională în document și depinde de existența istoricului de performanțe.

---

## Cerințe Nefuncționale

### 1. Securitate și confidențialitate a datelor
**Prioritate:** Must have

**Descriere:** Platforma gestionează date sensibile (note, rezultate, informații personale), așa că accesul la ele trebuie protejat strict. Un student poate vedea doar propriile rezultate și nu poate modifica note sau scoruri. Un profesor poate accesa doar datele cursurilor proprii. Toate verificările de acces se fac pe server, în funcție de rolul utilizatorului, iar parolele și comunicația sunt protejate (stocare criptată, HTTPS).

**Justificare prioritate:** Rezultatele academice sunt date cu caracter personal, iar divulgarea sau alterarea lor ar afecta direct studenții și credibilitatea platformei. Fără aceste garanții, sistemul nu poate fi folosit într-un context academic real.

### 2. Stabilitate și fiabilitatea înregistrării datelor
**Prioritate:** Must have

**Descriere:** Platforma nu trebuie să sufere crash-uri și nu trebuie să piardă munca studenților. Răspunsurile se salvează în baza de date pe parcursul quiz-ului, iar în caz de eroare sau pierdere a conexiunii studentul poate relua de unde a rămas.

**Justificare prioritate:** Pierderea răspunsurilor sau a rezultatelor afectează direct studenții și anulează scopul platformei.

### 3. Disponibilitate și reziliență la defecțiunile LLM
**Prioritate:** Must have

**Descriere:** Indisponibilitatea serviciului LLM nu trebuie să blocheze platforma. Funcționalitățile de bază (quiz-uri manuale, feedback manual) rămân complet operaționale, iar utilizatorul primește un mesaj clar dacă o funcție AI eșuează.

**Justificare prioritate:** LLM-ul este o dependență externă, iar funcționalitățile obligatorii nu trebuie să depindă de ea.

### 4. Mentenabilitate și extensibilitate
**Prioritate:** Should have

**Descriere:** Codul ar trebui separat pe straturi, iar arhitectura să permită adăugarea ulterioară a altor posibile funcționalități fără refactorizări majore.

**Justificare prioritate:** Este utilă pentru evoluția proiectului, dar nu influențează funcționarea în prima versiune.