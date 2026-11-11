# EduQuiz
Această aplicație își dorește să rezolve problema capcanei mentale care apare în rândul studenților ce le dă impresia că ar stăpâni noțiunile predate în mediul academic mai mult decât le stăpânesc în realitate cât și problema lipsei de feedback din partea studenților către profesori în ceea ce privește starea lor adevărată de pregătire. În acest sens, propunem o platformă de testare individuală prin care studentul poate rezolva exerciții propuse de profesor și primi feedback atât manual cât și automat din partea unui agent AI. 

Astfel, putem oferi studentului un context mai clar în ceea ce privește pregătirea sa efectivă, ajutându-l astfel să pună întrebări relevante pentru acesta cât și profesorului o privire de ansamblu mai precisă despre lacunele studenților.

## Obiective
* Crearea unei platforme web segregată în funcție de rolul utilizatorului
* Posibilitatea elevilor de a exersa interactiv și de a-și evalua cunoștințele prin intermediul quizurilor.
* Posibilitatea profesorilor de a genera și/sau evalua automat quiz-uri cu ajutorul unui LLM.

## Utilizatorii Vizati
Studenții și profesorii. Studenți au nevoie de un mediu organizat de învățare, structurat pe obiective cu materiale de antrenament adiționale. De asemenea, aceștia au nevoie de suport personalizat pentru părțile din curriculă care li se par la nivel individual dificile. Profesorii au nevoie de metode rapide și ușoare de a permite studenților să exerseze materia predată cât și acces la statistici agregate pentru a identifica părțile din materia predată care pun în dificultate studenții. De asemenea, este necesar un acces controlat strict de către un administrator pentru a evita ca persoane neautorizate din afara instituției de învățământ să se folosească de platforma acesteia.

## Funcționalitățile propuse 
### 1. Gestionare Utilizatori și Autentificare bazată pe Roluri
* **Utilizator vizat:** `Administrator`
* **Prioritate:** `Obligatoriu`

**Descriere:**
Administratorul adaugă și elimină conturile pentru profesori și studenți. Un utilizator se poate autentifica doar dacă administratorul i-a adăugat în sistem. În cazul în care nu există niciun cont înregistrat, se va efectua o procedură de configurare inițială în care un prim cont de administrator se va crea.

### 2. Analiză SWOT a Performanțelor Academice
* **Utilizator vizat:** `Student`
* **Prioritate:** `Opțional`

**Descriere:**
Studentul poate vedea pe ecranul principal o vedere de ansamblu a performanțelor sale observate din timpul rezolvării quizurilor, împărțite pe patru categorii: puncte tari, puncte slabe, oportunități și provocări.

### 3. Creare, Parcurgere Quiz-uri și Sistem de Feedback
* **Utilizatori vizați:** `Profesor`, `Student`
* **Prioritate:** `Obligatoriu` (pentru feedback manual) | `Opțional` (pentru feedback automat)

**Descriere:**
Profesorul adaugă, editează sau șterge întrebări din banca de exerciții, le clasifică pe categorii/niveluri de dificultate și atașează explicații pentru feedback. Salvările sunt stocate în baza de date și devin disponibile pentru generarea automată sau manuală de noi quiz-uri.
Studentul poate alege să completeze quiz-urile oferite. Pe măsură ce studentul rezolvă întrebările, în cazul în care răspunsul dat la o întrebare nu este corect sau complet, o fereastră de feedback va apărea care să-l ghideze spre rezultatul corect. La final studentul află scorul pe acel quiz. 

# Tehnologii
* Frontend:  Angular
* Backend: Spring Boot
* Database: PostgreSQL

# Membrii Echipei
* Iacobescu Ionuț-Robert - leader, front-end
* Iloc Lucian-Vasile - developer, back-end
* Mitoiu Bogdan-Petru - developer, back-end
