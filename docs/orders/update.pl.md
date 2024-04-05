# Edycja zamówienia
## Aktualizacja zamówienia
Stwórz ciało zamówienia w formacie JSON stosując zaktualizowane wartości atrybutów.

Poniżej znajdziesz przykład jak powinno wyglądać zamówienie:

=== "JSON"
```json
{
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
  "state": "draft",
  "deliveryDate": "2020-12-24"       
}
```

## Aktualizacja konfiguracji

Na podstawie konfiguratora stwórz zaktualizowaną konfigurację zamówienia. Aktualizacja konfiguracji opiera się na jej atrybucie `externalConfigurationId`, który jest wymagany. Pozostałe atrybuty są opcjonalne, ale jeżeli występują muszą być zgodne z konfiguratorem. 
 
???+ warning "UWAGA"

    Jeżeli zmiana dotyczy opcji, to należy podać wszystkie opcje tej konfiguracji.

Przykład ciała konfiguracji:

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

## Wysyłanie aktualizacji zamówienia

Przygotowane według powyższych wytycznych zamówienie wyślij jako ciało zapytania metodą `PATCH` pod API `/sales-channel-api/v1/orders/{id}`, gdzie `{id}` to id Twojego zamówienia, które chcesz aktualizować. W nagłówku zapytania umieść swoje [dane autoryzacyjne](../../authorization).

Przykład ciała kompletnego zamówienia zawierającego jedną konfigurację, w której zmieniono nazwę konfiguracji, cenę oraz wartość jednej z opcji w step4:

=== "JSON"
```json
{
  "configurations": 
      [
        {
          "externalConfigurationId": "{yourUniqueConfigurationId}",
          "configuratorId": "{configuratorId}",
          "configurationName": "Konfiguracja 1 - update 1",
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
              "value": "Z okazji imienin"
            }
          ],
          "price": 128.00
        }
      ],
  "price": 128.00
}
```

Przykład odpowiedzi:

=== "JSON"
``` json
{
    "message": "The command has been dispatched successfully.",
    "data": [],
    "errors": []
}
```
