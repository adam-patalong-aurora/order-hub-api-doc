# Api
Moduł autoryzacji udostępnia następujące endpointy:

### Tworzenie nowego konta - api/v1/admin [POST]
Aby utworzyć nowe konto należy wykonać zapytanie metodą `POST` na endpoint `api/v1/admin` z danymi nowego użytkownika w ciele zapytania. Dane nowego użytkownika muszą zawierać:

- adres email
- hasło - składające się conajmniej z <b>8 znaków</b> oraz posiadające min <b>1 cyfrę</b>.

Przykład zapytania:
``` json
{
    "email": "new.user@domain.com",
    "password": "Password123"
}
```
Przykład odpowiedzi:
``` json
{
    "message": "The command has been dispatched successfully.",
    "data": [],
    "errors": []
}
```

### Logowanie - api/v1/admin/login [POST]
Aby zalogować się na swoje konto w celu uzyskania tokena autoryzacyjnego należy wykonać zapytanie metodą `POST` na endpoint `api/v1/admin/login` z danymi logowania w ciele zapytania. Dane logowania muszą zawierać:

- adres email
- hasło - składające się conajmniej z <b>8 znaków</b> oraz posiadające min <b>1 cyfrę</b>.

Przykład zapytania:
``` json
{
  "email": "some@valid.email",
  "password": "String123"
}
```
W odpowiedzi otrzymamy token autoryzacyjny, który należy przekazać w nagłówku `Authorization` jako `Bearer Token` w każdym zapytaniu do serwisu.
``` json
{
    "message": "Access granted.",
    "data": {
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhZG1pbklkIjoiMdfs5SDfsdEhqwKfsawKV1QihJYDd36FSHdfsdfg9uLmNvbSJ9.NrQQVdHxziRosfhdZ0Wafdg3HssfhdZ6b_f3hNcU"
    },
    "errors": []
}
```

### Pobranie danych użytkownika - api/v1/admin/{id} [GET]
Aby uzyskać dane użytkownika należy wykonać zapytanie metodą `GET` na endpoint `api/v1/admin/{id}` z nagłówkiem `Authorization` zawierającym token autoryzacyjny. Jako `{id}` należy podać identyfikator użytkownika.

W odpowiedzi otrzymamy dane użytkownika.

Przykład odpowiedzi:
``` json
{
    "message": "Ok",
    "data": {
        "id": "ff131967-d281-4cf1-9b25-547cbacc9515",
        "email": "admindsfffugg@roracreation.com",
        "password": "$2y$13$ZoV4IAMgNPGPsLTgtFRKCOq0T273iuwj9GXdFlE/ogwh4ypOkg6ra"
    },
    "errors": []
}
```

### Lista wszystkich użytkowników - api/v1/admin [GET]
Aby uzyskać listę wszystkich użytkowników należy wykonać zapytanie metodą `GET` na endpoint `api/v1/admin` z nagłówkiem `Authorization` zawierającym token autoryzacyjny.

W odpowiedzi otrzymamy listę wszystkich użytkowników.

Przykład odpowiedzi:
``` json
{
    "message": "Ok",
    "data": [
        {
            "id": "16c9fd65-2530-423d-a1de-594effb2358c",
            "email": "admin@auroracreation.com",
            "password": "$2y$13$cq/s5oKOO22BtimCLPZQBuMZ2dAfOrPJYYUUri62plVYwkHRtaaUS"
        },
        {
            "id": "366fdf1c-c222-4014-8e5c-3b6d2bcc1003",
            "email": "new.user@domain.com",
            "password": "$2y$13$5DsGu0Wvlsft8uNzPk4EQeJCTQJiOGP7WRtVfbwusfwCyTsme7GT."
        }
    ],
    "errors": []
}
```

### Usuwanie użytkownika - api/v1/admin/{id} [DELETE]
Aby usunąć użytkownika należy wykonać zapytanie metodą `DELETE` na endpoint `api/v1/admin/{id}` z
nagłówkiem `Authorization` zawierającym token autoryzacyjny. Jako `{id}` należy podać identyfikator użytkownika którego chcesz usunąć.

Przykład odpowiedzi:
``` json
{
    "message": "The command has been dispatched successfully.",
    "data": [],
    "errors": []
}
```
