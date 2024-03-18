# Konfiguracja zamówienia
Zaimplementuj w swoim sklepie otrzymany konfigurator i na jego podstawie wygeneruj konfigurację zamówienia. Następnie wyślij ją pod właściwe API, a OrderHub je przetworzy. W nagłówku zapytania umieść [dane autoryzacyjne](../../authorization).
Oto jak powinna wyglądać przykładowa konfiguracja zamówienia:

```json
{
  "externalOrderId": "1-01/2020",
  "salesChannelId": "123543-34yhgfn-gjkeb4j5hbg",
  "configurations": 
      [
        {
          "configuratorId": "fdbhvjDFHWet34FDHDSetr",
          "configurationName": "Konfiguracja 1",
          "options": 
            [
              {
                "name": "fdbhvjDFHWet34FDHDSetr",
                "configurationId": "fdbhvjDFHWet34FDHDSetr",
                "stepId": "fdbhvj",
                "elementId": "fdbhvjDFHWet34FDHDSetr",
                "componentId": "fdbhvjDFHWet34FDHDSetr",
                "value": "12"
              }
            ],
          "price": "123.45"
        }
      ],
  "price": "123.45",
  "address": {
    "street": "ul. Testowa 1",
    "city": "Warszawa",
    "zipCode": "00-001",
    "country": "PL"
  },
  "deliveryDate": "2020-12-24"       
}
```
