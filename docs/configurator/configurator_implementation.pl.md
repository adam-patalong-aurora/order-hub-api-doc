# Implementacja konfiguratora

W tej sekcji znajdziesz informacje jak w prawidłowy sposób wdrożyć u siebie konfigurator. Przejdź przez poniższą instrukcję, a stworzenie prawidłowej konfiguracji nie będzie stanowiło dla Ciebie problemu.

***

## Krok 1 - Wybór konfiguratora

Sprawdź dostępne konfiguratory. Ich listę otrzymasz wysyłając zapytanie `GET` pod API `{{ configurator_source_path }}/ids`

??? "Przykład odpowiedzi"
    === "JSON"
        ```json linenums="1"
        --8<-- "docs/configurator/code/configurator_ids.json"
        ```

Następnie wybierz konfigurator, który chcesz zaimplementować i wykorzystaj jego numer id w dalszych krokach.

***

## Krok 2 - Pobranie ciała konfiguratora

Pobierz ciało wybranego konfiguratora wysyłając zapytanie `GET` pod API `{{ configurator_source_path }}/{configuratorId}`, gdzie {configuratorId} to id konfiguratora, którego dane chcesz pobrać.

??? "Przykład odpowiedzi - część ciała konfiguratora"
    === "JSON"
        ```json
        --8<-- "docs/configurator/code/configurator_body.json"
        ```

Jak widzisz ciało konfiguratora zawiera wiele informacji o jego krokach `steps`, elementach `elements` oraz komponentach `components`.

### Kroki

Podczas budowania konfiguracji należy przejść przez wszystkie kroki konfiguratora.

### Elementy

Podczas budowania konfiguracji należy przejść przez wszystkie elementy konfiguratora. Zwróć uwagę na atrybut `required`. Jeśli jego wartość jest `true`, to użytkownik musi wybrać jedną z jego opcji (chyba, że żadna z opcji - czyli żaden komponent nie spełnia warunków do jego wyłączenia do konfiguracji).

### Komponenty

Komponenty posiadają warunki `conditions`, które określają, kiedy dany komponent może zostać użyty w konfiguracji. To właśnie komponenty należy wykorzystać do stworzenia konfiguracji jako jej opcje.

#### Typy komponentów

Komponenty zaliczają sie do typów:

- `button`
- `numeric`
- `product`
- `upload`
- `warning`
- `font`
- `fontPreview`

To od typu komponentu zależy jakie dane musisz przesłać w celu zapisania konfiguracji.

Komponenty typu `numeric` posiadają atrybut `valueRange`, który określa zakres wartości jakie może przyjąć komponent. 

Komponent typu `upload` przyjmie wartość `string` jako adres do pliku. 

Komponent typu `product` przyjmie wartość `int`. Komponenty tego typu najczęściej występują jako dodatkowe albumy, które można dodać do zamówienia. Wartość wskazuje na ilość dodatkowych albumów jakie użytkownik chce zamówić.
W przypadku pozostałych komponentów wartość ta wynosi zawsze `1`.

#### Warunki komponentu

Warunki `conditions` to tablica warunków, które muszą zostać spełnione, aby komponent mógł zostać użyty w konfiguracji. Każdy warunek to obiekt, który należy interpretować wnastępujący sposób:

??? example "`type` - typ warunku mówi o tym czy wszystkie warunki w tablicy muszą zostać spełnione `all` czy wystarczy, że jeden z nich zostanie spełniony `any`."
    ```json hl_lines="4 12 20"
        --8<-- "docs/configurator/code/component_conditions.json"
    ```

??? example "`componentId` - id komponentu, który musi zostać spełniony. `stepId` oraz `elementId` pomagają w lokalizacji tego komponentu"
    ```json hl_lines="5-7 13-15 21-23"
        --8<-- "docs/configurator/code/component_conditions.json"
    ```

??? example "`operator` - operator porównania. Przyjmuje wartość: `eq` - równy"
    ```json hl_lines="8 16 24"
        --8<-- "docs/configurator/code/component_conditions.json"
    ```

??? example "`value` - wartość jaka jest wymagana do spełnienia warunku"
    ```json hl_lines="9 17 25"
     --8<-- "docs/configurator/code/component_conditions.json"
    ```

??? tip "Jeżeli element jest wymagany lecz żaden komponent nie spełnia warunków to element przestaje być wymagany."

***

## Krok 3 - Wdrożenie konfiguratora

Wdrożenie konfiguratora polega na stworzeniu formularza, który pozwoli użytkownikowi na wybranie opcji (komponentów) konfiguratora. W celu stworzenia formularza należy wykorzystać dane konfiguratora, które otrzymałeś w poprzednim kroku.

Przygotuj formularz w którym przejdziesz przez wszystkie kroki `steps` oraz elementy `elements` konfiguratora zgodnie z powyższymi wytycznymi. 

Na podstawie formularza stwórz konfigurację i dodaj ją do zamówienie. Więcej informacji o tym jakie dane musi zawierać zamówienie i konfiguracja znajdziesz [tutaj](../../orders/create).
