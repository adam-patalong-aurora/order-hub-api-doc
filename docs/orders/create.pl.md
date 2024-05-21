# Nowe zamówienie

??? "Przykład ciała kompletnego zamówienia zawierającego jedną konfigurację oraz dodatkowe odbitki"
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
Następnie dodaj do zamówienia konfiguracje lub odbitki.

??? "Przykład jak powinno wyglądać zamówienie"
    === "JSON"
        ```json linenums="1" hl_lines="2-44"
        --8<-- "docs/orders/code/body_create.json"
        ```

### Konfiguracje

Na podstawie konfiguratora stwórz konfiguracje zamówienia. Zamówienie może zawierać kilka konfiguracji. Prawidłowo stworzona konfiguracja składa się z ciała konfiguracji, w którym zawarte są opcje, i na podstawie których zostanie obliczona wartość zamówienia. 

Jeżeli nie chcesz dodawać konfiguracji nie dodawaj atrybutu `configurations` do ciała zamówienia.

??? "Przykład ciała konfiguracji"
    === "JSON"
        ```json linenums="1"
        --8<-- "docs/orders/code/configuration.json"
        ```

??? info "Informacja"
    Całość zamówienia może mieć obszerny rozmiar. Zależny jest on od ilości konfiguracji jakie posiada zamówienie oraz opcji w nich zawartych.

### Odbitki

Na podstawie Twojego konfiguratora utwórz dane do dodatkowych wydruków zamówienia. Dodatkowe wydruki są identyfikowane poprzez atrybut `externalPhotoPrintId`. W atrybucie `formats` należy podać wszystkie odbitki dla tego `externalPhotoPrintId`.

Jeżeli nie chcesz dodawać odbitek nie dodawaj atrybutu `photoPrints` do ciała zamówienia.

??? "Przykład ciała odbitek"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/photo_prints.json"
        ```

### Wysyłanie zamówienia

???+ warning "Informacja"
    Zamówienie musi posiadać co najmniej jedną z opcji: konfigurację lub odbitki.

Przygotowane według powyższych wytycznych zamówienie wyślij jako ciało zapytania metodą `POST` pod API `{{ domain.base_url }}/sales-channel-api/v1/orders`. W nagłówku zapytania umieść [dane autoryzacyjne](../../authorization).
