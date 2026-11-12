# Modelul de date și interacțiuni importante

## Modelul de date
![model de date](diagrams/Diagramă%20Clase.png)

## Interacțiuni importante
Cea mai importantă interacțiune este rezolvarea unui quiz. Pentru acest exemplu vom presupune că în sistem este autentificat un student.
```http request
GET /api/courses
Authorization: Bearer: <token>
```
Se obține astfel cursurile la care studentul este înscris. Vom alege un curs pe nume {idCurs}


```http request
GET /api/courses/{idCurs}/
Authorization: Bearer: <token>
```

Se obțin toate quiz-urile disponibile pentru cursul respectiv. Vom alege să rezolvăm quiz-ul numărul 1.

```http request
GET /api/courses/{idCurs}/quizes/1
Authorization: Bearer: <token>
```

Vom obține informațiile despre curs - câte întrebări are, cât valorează fiecare întrebare.

```http request
GET /api/courses/{idCurs}/quizes/1/questions/{numQuestion}
Authorization: Bearer: <token>
```
Se va primi textul întrebării numQuestion.
```http request
POST /api/courses/{idCurs}/quizes/1/questions/{numQuestion}
Authorization: Bearer: <token>

{
"answer": "xyz"
}
```
Se trimite răspunsul studentului. Sistemul răspune fie cu un răspuns afirmativ, fie răspunde cu textul de feedback.

```http request
POST /api/courses/{idCurs}/quizes/1/finalize
Authorization: Bearer: <token>
```
Se notifică serverul că studentul a terminat quiz-ul, se va genera un scor final și se va transmite clientului.


### Alte interacțuni importante

| Endpoint                   | Rol                                                                                                                                                                                  |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `/api/students`            | Obținerea tuturor studenților. Accesibil doar de către admin și profesor pentru înrolare la curs                                                                                     |
| `/api/admin/users`         | Oferă operații CRUD pentru administrarea utilizatorilor. Poate fi accesat doar de către administrator                                                                                |
| `/api/courses`             | Afișează datele despre cursuri                                                                                                                                                       |
| `/api/courses/{id}/quizes` | Gestionează quizurile. Operația POST este accesibilă pentru acest endpoint doar profesorilor. Studenții pot accesa subendpointurile folosind comanda POST pentru a rezolva quizurile |
| `/me`                      | Afișează informațiile despre utilizatorul actual                                                                                                                                     |
| `/auth`                    | Solicită token de autentificare. Pașii detaliați va depinde de metoda exactă de autentificare.                                                                                       |
| `/deauth`                  | Invalidează tokenul de autentificare                                                                                                                                                 |