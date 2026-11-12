# Arhitectura sistemului

Pentru arhitectura sistemului am ales să mergem la nivel macro cu un model client-server: aplicația web de pe calculatorul utilizatorului trimite cereri către serverul din spate care efectuează toate operațiile necesare.
La finalizarea operației, programul server va trimite un răspuns corespunzător în format JSON aplicației client.

Din punct de vedere micro al backend-ului vom folosi o arhitectură de tip monolit stratificat. Acest lucru ne reduce volumul de muncă necesar pentru a avea o aplicație funcțională, deoarece nu trebuie să implementăm mecanisme de întrerupere de circuit (circuit breakers) și sisteme
de configurare a microserviciilor. Cu toate acestea, am îmnprumutat o idee de bază de la modelul bazat pe microservicii în proiectarea stratului de servicii. Se poate observa în diagrama de mai jos existența unei structuri de tip REST Gateway -> servicii backend. Această alegere a fost intenționată
pentru a ne putea permite conversia pe o abordare bazată pe microservicii în cazul în care aceasta se dovedește a fi fiabilă pentru volumul de date și utilizatori pe care îl avem în gestiune

Pentru persistența datelor ne vom folosi de o bază de date de tip PostgreSQL datorită structurii relaționare ce facilitează implementarea interacțiunile dintre entitățile folosite pe întreg acest proiect.

Din punct de vedere al securității am ales o procedură de tip autentificare bazată pe token de acces (definit prin OAuth2). Acest model este implementat la scară largă de industrie și ne permite flexibilitatea de a introduce autentificarea bazată pe alte servicii compatibile OAuth2, precum Google, Microsoft, Apple etc. În primă fază vom implementa procesul de autentificare în cadrul aceluiași 
sistem monolit, însă rămânem desciși la ideea de a separa autentificarea într-o entitate arhitecturală distinctă dacă această nevoie apare.


![Diagramă sistem](diagrams/Diagramă%20Sistem.png)


### Descrierea serviciilor

Aici se regăsește un tabel explicativ pentru fiecare serviciu din modulul de servicii


| Serviciu                         | Rol                                                                                                |
|----------------------------------|----------------------------------------------------------------------------------------------------|
| `Accounts service`               | Se ocupă cu extragerea datelor despre utilizatori spre a fi folosite de serviciul de autentificare |
| `Quiz service`                   | Gestionează quiz-urile stocate, analizează răspunsurile studenților și acordă note.                |
| `LLM service`                    | Stabilește conexiunea cu un model de inteligență artificială generativă pentru feedback automat    |
| `Performance management service` | Gestionează datele despre performanța studenților                                                  |
