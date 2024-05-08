# Nowe zamówienie

??? "Przykład ciała kompletnego zamówienia zawierającego jedną konfigurację"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/body_create.json"
        ```

??? "Przykład odpowiedzi"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/response.json"
        ```
## Krok po kroku

### Tworzenie zamówienia
Stwórz ciało zamówienia w formacie JSON stosując właściwe dla twojego sklepu atrybuty i wartości.

??? "Przykład jak powinno wyglądać zamówienie"
    === "JSON"
        ```json linenums="1" hl_lines="2-45 132-137"
        --8<-- "docs/orders/code/body_create.json"
        ```

### Tworzenie konfiguracji

Na podstawie konfiguratora stwórz konfigurację zamówienia. Zamówienie może zawierać kilka konfiguracji.Prawidłowo stworzona konfiguracja składa się z ciała konfiguracji, w którym zawarte są opcje, i na podstawie których zostanie obliczona wartość zamówienia.

??? "Przykład ciała konfiguracji"
    === "JSON"
        ```json linenums="1" hl_lines="46-130"
        --8<-- "docs/orders/code/body_create.json"
        ```

??? info "Informacja"
    Całość zamówienia może mieć obszerny romiar. Zależny jest on od ilości konfiguracji jakie posiada zamówienie oraz opcji w nich zawartych.

### Wysyłanie zamówienia

Przygotowane według powyższych wytycznych zamówienie wyślij jako ciało zapytania metodą `POST` pod API `/sales-channel-api/v1/orders`. W nagłówku zapytania umieść [dane autoryzacyjne](../../authorization).
