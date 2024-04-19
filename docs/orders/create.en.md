# Create an order
## Order
Create an order body in JSON format using attributes and values appropriate for your store.

??? "Example of what an order should look like"
    === "JSON"
    ```json
    {
      "externalOrderId": "1-01/2020",
      "salesChannelId": "{your-sales-channel-id}",
      "configurations": 
          [
              { configuration 1 },
              { configuration 2 }
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

## Configuration

Create an order configuration based on the configurator. An order may contain several configurations. A properly created configuration consists of a configuration body and has options on the basis of which the order value will be calculated.

??? "Configuration body example"
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

??? info "Information"
    The entire order may be large in size. It depends on the number of configurations the order has and the options included in them.

## Sending the order

Send the order prepared according to the above information as a query body using the `POST` method under the API `/api/v1/sales-channels-orders`. Place [authorization data](../../authorization) in the query header.

??? "Example of a complete order body containing one configuration"
    === "JSON"
    ```json
    {
      "externalOrderId": "1-01/2020",
      "salesChannelId": "{your-sales-channel-id}",
      "configurations": 
          [
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

??? "Response sample"
    === "JSON"
    ``` json
    {
        "message": "The command has been dispatched successfully.",
        "data": [],
        "errors": []
    }
    ```
