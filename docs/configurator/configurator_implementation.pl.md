# Implementacja konfiguratora

Tutaj znajdziesz informacje jak w prawidłowy sposób wdrożyć u siebie konfigurator.

## Krok 1 - Wybór konfiguratora

Sprawdź dostępne konfiguratory. Ich listę otrzymasz wysyłając zapytanie `GET` pod API `{{ configurator_source_path }}/ids`

??? "Przykład odpowiedzi"
    === "JSON"
        ```json linenums="1"
        --8<-- "docs/configurator/code/configurator_ids.json"
        ```

Następnie wybierz konfigurator, który chcesz zaimplementować i wykorzystaj jego numer id w dalszych krokach.

## Krok 2 - Pobranie ciała konfiguratora

Pobierz ciało wybranego konfiguratora wysyłając zapytanie `GET` pod API `{{ configurator_source_path }}/{configuratorId}`, gdzie {configuratorId} to id konfiguratora, którego dane chcesz pobrać.

??? "Przykład odpowiedzi - część ciała konfiguratora"
    === "JSON"
        ```json
        --8<-- "docs/configurator/code/configurator_body.json"
        ```
### Ciało konfiguratora

Jak widzisz ciało konfiguratora zawiera informacje o jego krokach `steps`, elementach `elements` oraz komponentach `components`.

### Komponenty

Komponenty posiadają warunki `conditions`, które określają, kiedy dany komponent może zostać użyty w konfiguracji. To właśnie komponenty należy wykorzystać do stworzenia konfiguracji jako jej opcje.

Komponenty zaliczają sie do typów:
- `button`
- `numeric`
- `product`
- `upload`
- `warning`
- `font`
- `fontPreview`

To od typu komponentu zależy jakie dane musisz przesłać w celu zapisania konfiguracji.

## Krok 3 - Wdrożenie konfiguratora

Wdrożenie konfiguratora polega na stworzeniu formularza, który pozwoli użytkownikowi na wybranie opcji (komponentów) konfiguratora. W celu stworzenia formularza należy wykorzystać dane konfiguratora, które otrzymałeś w poprzednim kroku.

Przygotuj formularz w którym przejdziesz przez wszystkie kroki `steps` oraz elementy `elements` konfiguratora.

### Step 1 / Element 1

Wyświetl wszystkie komponenty pierwszego kroku konfiguratora i pierwszego elementu.

??? example "Step 1 / Element 1"
    === "JSON"
        ```json hl_lines="15-24"
        --8<-- "docs/configurator/code/configurator_body.json"
        ```
