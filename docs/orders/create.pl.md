# Nowe zamówienie
## Tworzenie zamówienia
Stwórz ciało zamówienia w formacie JSON stosując właściwe dla twojego sklepu atrybuty i wartości.

??? "Przykład jak powinno wyglądać zamówienie"
    === "JSON"
    ```json
    {
      "externalOrderId": "1-01/2020",
      "salesChannelId": "{your-sales-channel-id}",
      "configurations": 
          [
              { konfiguracja 1 },
              { konfiguracja 2 }
          ],
      "price": 544.45,
      "address": {
        "street": "Testowa 1",
        "city": "Warszawa",
        "zipCode": "00-001",
        "country": "PL"
      },
      "deliveryDate": "2020-12-24"       
    }
    ```

## Tworzenie konfiguracji

Na podstawie konfiguratora stwórz konfigurację zamówienia. Zamówienie może zawierać kilka konfiguracji.Prawidłowo stworzona konfiguracja składa się z ciała konfiguracji, w którym zawarte są opcje, i na podstawie których zostanie obliczona wartość zamówienia.

??? "Przykład ciała konfiguracji"
    === "JSON"
    ```json
        {
          "externalConfigurationId": "{yourUniqueConfigurationId}",
          "configuratorId": "{configuratorId}",
          "configurationName": "Konfiguracja 1",
          "options":
          [
            {
              "name": "{optionName}",
              "stepId": "Step1",
              "elementId": "{uniqueElementId}",
              "componentId": "{uniqueComponentId}",
              "value": "1"
            }
          ],
          "price": 123.45
        }
    ```
??? info "Informacja"
    Całość zamówienia może mieć obszerny romiar. Zależny jest on od ilości konfiguracji jakie posiada zamówienie oraz opcji w nich zawartych.

## Wysyłanie zamówienia

Przygotowane według powyższych wytycznych zamówienie wyślij jako ciało zapytania metodą `POST` pod API `/sales-channel-api/v1/orders`. W nagłówku zapytania umieść [dane autoryzacyjne](../../authorization).

??? "Przykład ciała kompletnego zamówienia zawierającego jedną konfigurację"
    === "JSON"
    ```json
    {
      "externalOrderId": "1-01/2020",
      "salesChannelId": "{your-sales-channel-id}",
      "configurations": 
          [
            {
              "configuratorId": "{configuratorId}",
              "configurationName": "Konfiguracja 1",
              "options":
              [
                {
                  "name": "{optionName}",
                  "stepId": "Step1",
                  "elementId": "{uniqueElementId}",
                  "componentId": "{uniqueComponentId}",
                  "value": "1"
                },
                {
                  "name": "{optionName}",
                  "stepId": "Step2",
                  "elementId": "{uniqueElementId}",
                  "componentId": "{uniqueComponentId}",
                  "value": "10"
                },
                {
                  "name": "{optionName}",
                  "stepId": "Step2",
                  "elementId": "{uniqueElementId}",
                  "componentId": "{uniqueComponentId}",
                  "value": "1"
                },
                {
                  "name": "{optionName}",
                  "stepId": "Step3",
                  "elementId": "{uniqueElementId}",
                  "componentId": "{uniqueComponentId}",
                  "value": "1"
                },
                {
                  "name": "{optionName}",
                  "stepId": "Step4",
                  "elementId": "{uniqueElementId}",
                  "componentId": "{uniqueComponentId}",
                  "value": "Z okazji urodzin"
                }
              ],
              "price": 544.45
            }
          ],
      "price": 544.45,
      "address": {
        "street": "Testowa 1",
        "city": "Warszawa",
        "zipCode": "00-001",
        "country": "PL"
      },
      "deliveryDate": "2020-12-24"       
    }
    ```

??? "Przykład odpowiedzi"
    === "JSON"
    ``` json
    {
        "message": "The command has been dispatched successfully.",
        "data": [],
        "errors": []
    }
    ```
