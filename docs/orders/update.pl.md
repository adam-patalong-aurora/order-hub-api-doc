# Edycja zamówienia

Edycja zamówienia polega na zmianie wartości atrybutów zamówienia lub konfiguracji. W celu edycji zamówienia należy wysłać zapytanie metodą `PATCH` pod API `{{ domain.base_url }}/sales-channel-api/v1/orders/{id}`, gdzie `{id}` to externalId Twojego zamówienia, które chcesz edytować i które podałes w czasie tworzenia zamówienia.

??? "Przykład kompletnego ciała edycji zamówienia zawierającego jedną konfigurację oraz dodatkowe odbitki"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/body_update.json"
        ```

??? "Przykład odpowiedzi"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/response.json"
        ```

## Krok po kroku

### Aktualizacja zamówienia
Stwórz ciało zamówienia w formacie JSON stosując zaktualizowane wartości atrybutów.

???+ info "Informacja"
    Możesz podać tylko te atrybuty, które chcesz zaktualizować.

### Aktualizacja konfiguracji

Na podstawie posiadanego konfiguratora stwórz zaktualizowaną konfigurację zamówienia. Aktualizacja konfiguracji opiera się na jej atrybucie `externalConfigurationId`. Aktualizowana konfiguracja musi być kompletna, czyli musi zawierać wszystkie atrybuty konfiguracji.
 
???+ warning "Uwaga"
    Jeżeli zmiana dotyczy opcji, to należy podać wszystkie opcje tej konfiguracji.

???+ warning "Uwaga"
    Edytując konfigurację możesz całkowicie zmienić jej opcje jednak muszą one opierać się na tym samym konfiguratorze co poprzednio.

???+ warning "Uwaga"
    Nie można usunąć wcześniej stworzonej konfiguracji.

???+ tip "Podpowiedź"
    Edytując konfigurację musisz podać jej `externalConfigurationId`, które jest unikalnym identyfikatorem konfiguracji.
    Podając nowy `externalConfigurationId` możesz stworzyć nową konfigurację do tego samogo zamówienia.

??? "Przykład ciała konfiguracji"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/configuration.json"
        ```

### Aktualizacja odbitek

Na podstawie posiadanego konfiguratora stwórz zaktualizowane dane dodatkowych odbitek zamówienia. Aktualizacja dodatkowych odbitek opiera się na ich atrybucie `externalPhotoPrintId`. W atrybucie `formats` należy podać na nowo wszystkie dane dodatkowych odbitek dla tego `externalPhotoPrintId`. 

??? "Przykład ciała dodatkowych odbitek"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/photo_prints.json"
        ```

### Wysyłanie aktualizacji zamówienia

Przygotowane według powyższych wytycznych zaktualizowane zamówienie wyślij jako ciało zapytania metodą `PATCH` pod API `{{ domain.base_url }}/sales-channel-api/v1/orders/{id}`, gdzie `{id}` to id Twojego zamówienia, które chcesz aktualizować. W nagłówku zapytania umieść swoje [dane autoryzacyjne](../../authorization).
