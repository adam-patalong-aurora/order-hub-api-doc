# Edycja zamówienia

Edycja zamówienia polega na zmianie wartości atrybutów zamówienia lub konfiguracji. W celu edycji zamówienia należy wysłać zapytanie metodą `PATCH` pod API `{{ domain.base_url }}/sales-channel-api/v1/orders/{id}`, gdzie `{id}` to id zamówienia, które chcesz edytować.

???+ warning "Uwaga"
    Jeżeli zmiana dotyczy opcji, to należy podać wszystkie opcje tej konfiguracji.

??? "Przykład kompletnego ciała edycji zamówienia zawierającego jedną konfigurację"
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

??? "Przykład ciała konfiguracji"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/configuration.json"
        ```

### Wysyłanie aktualizacji zamówienia

Przygotowane według powyższych wytycznych zamówienie wyślij jako ciało zapytania metodą `PATCH` pod API `{{ domain.base_url }}/sales-channel-api/v1/orders/{id}`, gdzie `{id}` to id Twojego zamówienia, które chcesz aktualizować. W nagłówku zapytania umieść swoje [dane autoryzacyjne](../../authorization).
