# Implementation-Plan

## Tehnologii Propuse

### Frontend – Angular

**Utilizare:** Dezvoltarea interfeței web și gestionarea interacțiunii dintre utilizator și aplicație.

**Justificare:**
- Potrivit pentru dezvoltarea aplicațiilor web moderne, oferind un ecosistem integrat de instrumente pentru gestionarea componentelor, rutării, formularelor și comunicării cu API-urile backend.
- Dezvoltatorul responsabil de componenta frontend are experiență anterioară în utilizarea Angular și TypeScript.

### Backend – Java și Spring Boot

**Utilizare:** Implementarea logicii aplicației, expunerea API-urilor REST, gestionarea autentificării și autorizării și integrarea cu serviciile externe.

**Justificare:**
- Java este un limbaj de programare cunoscut de membrii echipei, fiind studiat în cadrul activităților universitare. Astfel, timpul necesar familiarizării cu tehnologia este redus.
- Spring oferă suport pentru dezvoltarea API-urilor REST, accesarea bazelor de date, validarea datelor și implementarea mecanismelor de securitate.

### Persistence – PostgreSQL

**Utilizare:** Persistența datelor aplicației și gestionarea relațiilor dintre entități.

**Justificare:**
- PostgreSQL este un sistem de gestiune a bazelor de date relaționale open-source, fără costuri de licențiere.
- Dispune de o documentație extinsă, numeroase instrumente și librării convenabile.

---

## Strategia de Versionare

Se va utiliza un workflow simplificat, inspirat din GitHub Flow, adaptat dimensiunii echipei.

| Branch | Rol |
|---|---|
| `main` | Conține versiunea stabilă și funcțională a aplicației. |
| `develop` | Integrează funcționalitățile finalizate înainte de promovarea în `main`. |
| `feature/*` | Dezvoltarea unor funcționalități noi. |
| `fix/*` | Remedierea erorilor identificate. |
| `docs/*` | Modificări aduse documentației. |
| `refactor/*` | Îmbunătățirea structurii codului fără modificarea funcționalității. |

### Convenția de commit

Se propune utilizarea convenției **Conventional Commits**, pentru păstrarea unui istoric clar și ușor de urmărit.

| Tip | Utilizare |
|---|---|
| `feat` | Adăugarea unei funcționalități noi. |
| `fix` | Remedierea unei erori. |
| `docs` | Modificări ale documentației. |
| `refactor` | Restructurarea codului. |
| `test` | Adăugarea sau modificarea testelor. |
| `style` | Modificări de formatare, fără schimbarea logicii. |
| `chore` | Configurări, dependențe și alte activități administrative. |

---

## Planul de Implementare și Prioritizarea Activităților

Pentru versiunea beta, Etapa 3, **EduQuiz** își propune:

### Must Have – Funcționalități esențiale

- **Setup-ul mediului de dezvoltare:** Configurarea framework-urilor, Docker, a mediului de lucru și rezolvarea problemelor inițiale de conectivitate.
- **Database-First Development:** Proiectarea și integrarea bazei de date în aplicație, inclusiv maparea entităților și a relațiilor dintre acestea.
- **Arhitectura Client-Server:** Implementarea unui client Angular și a unui server Spring Boot funcționale, cu un flux de comunicare persistent în baza de date.
- **Business Logic – Quizz-uri:** Implementarea operațiilor CRUD pentru crearea și gestionarea quizz-urilor și a seturilor de întrebări, precum și funcționalitatea de parcurgere și rezolvare a acestora.
- **Interfața utilizator:** Implementarea interfețelor principale: Home, Curs și Quizz.

### Should Have – Funcționalități importante

- **Business Logic – Cursuri:** Implementarea operațiilor CRUD pentru crearea și gestionarea cursurilor.
- **Paginare și căutare:** Implementarea funcționalităților de paginare, căutare și statistici.
- **Feedback și explicații:** Afișarea rezultatelor, feedback-ului și explicațiilor după rezolvarea quizz-urilor.

### Could Have – Funcționalități opționale

- **Sistem de roluri:** Introducerea rolurilor de Profesor, Elev și Administrator.
- **Integrare LLM:** Implementarea unei integrări incipiente cu un Large Language Model.
- **Autentificare și autorizare:** Implementarea unui mecanism de autentificare și gestionare a accesului utilizatorilor.

---

### Săptămâna 1 – Setup și infrastructură

- Setup Spring Boot, Angular și Docker
- Configurare bază de date și structura inițială a aplicației
- Proiectarea entităților, a relațiilor și configurarea conexiunii ORM
- Crearea componentelor principale Angular și configurarea comunicării cu backend-ul

### Săptămâna 2 – Core Business Logic

- API-uri, DTO, CRUD pentru Quizz-uri și Întrebări
- UI pentru Home, Curs, Quizz și Întrebări
- Implementarea fluxului de comunicare Server + Client și persistarea informației

### Săptămâna 3 – Integrare și funcționalități suplimentare

- API-uri, DTO, CRUD pentru Cursuri
- Implementare căutare și paginare
- Feedback și explicații pentru rezultate
- Testare, stabilitate și corectarea problemelor

## Repartizarea Responsabilităților

### Iacob – Frontend și interfață grafică

**Rol:** Frontend Developer

Responsabil pentru dezvoltarea interfeței web și pentru experiența de utilizare a aplicației.

**Responsabilități:**
- Dezvoltarea aplicației client utilizând Angular și TypeScript.
- Proiectarea și implementarea interfeței grafice.
- Definirea structurii paginilor, componentelor și layout-urilor.
- Implementarea rutării între paginile aplicației.
- Dezvoltarea componentelor reutilizabile.
- Implementarea formularelor și a mecanismelor de validare la nivelul interfeței.
- Integrarea frontend-ului cu API-urile REST furnizate de backend.
- Gestionarea stărilor interfeței, inclusiv loading, success și error.
- Asigurarea unei experiențe de utilizare coerente și responsive.
- Verificarea compatibilității interfeței cu diferite dimensiuni de ecran.

**Livrabile:**
- Aplicația Angular.
- Componentele grafice reutilizabile.
- Paginile și formularele aplicației.
- Integrarea cu API-urile backend.

---

### Bogdan – API, securitate și testare

**Rol:** Backend Developer

Responsabil pentru implementarea mecanismelor de securitate, expunerea API-urilor și verificarea corectitudinii funcționale a componentelor backend.

**Responsabilități:**
- Implementarea mecanismelor de autentificare și autorizare.
- Configurarea Spring Security și a mecanismului de gestionare a tokenurilor.
- Definirea și implementarea controller-elor REST.
- Definirea DTO-urilor utilizate pentru comunicarea dintre frontend și backend.
- Implementarea mapper-elor pentru conversia dintre entități și DTO-uri.
- Gestionarea validării datelor primite prin API.
- Implementarea mecanismelor de tratare centralizată a excepțiilor.
- Scrierea testelor unitare pentru serviciile și componentele backend.
- Verificarea comportamentului API-urilor în diferite scenarii de utilizare.
- Verificarea accesului la resurse în funcție de rolurile utilizatorilor.

**Livrabile:**
- Mecanismele de autentificare și autorizare.
- Controller-ele REST și contractele de comunicare aferente.
- DTO-urile și mapper-ele.
- Suita de teste unitare pentru componentele backend.
- Mecanismele de validare și tratare a erorilor.

---

### Lucian – Persistență, logică de business și integrare LLM

**Rol:** Backend & Integration Developer

Responsabil pentru gestionarea datelor, implementarea logicii de business și integrarea serviciilor externe.

**Responsabilități:**
- Implementarea entităților și a mapărilor ORM utilizând JPA/Hibernate.
- Configurarea conexiunii dintre Spring Boot și PostgreSQL.
- Implementarea repository-urilor și a operațiilor de acces la date.
- Implementarea serviciilor de business și a operațiilor CRUD.
- Integrarea serviciului extern bazat pe Large Language Model (LLM).
- Implementarea mecanismelor de comunicare cu serviciile externe.
- Gestionarea răspunsurilor, erorilor și eventualelor indisponibilități ale serviciilor externe.
- Configurarea mediului Docker și Docker Compose.
- Gestionarea dependențelor și a configurărilor necesare funcționării aplicației.
- Asigurarea compatibilității dintre componentele dezvoltate de membrii echipei.

**Livrabile:**
- Modelul bazei de date și entitățile JPA.
- Repository-urile și serviciile de business.
- Integrarea serviciului LLM.
- Configurația Docker și Docker Compose.
- Configurațiile de conectare și integrare dintre componente.