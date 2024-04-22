# Edit order
## Order update
Create the order body in JSON format using the updated attribute values.

???+ info "Information"
    You can specify only the attributes you want to update.

??? "Example of what an order should look like"
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
      "shippingMethod": "{shippingMethod}",
      "deliveryDate": "2020-12-24"       
    }
    ```

## Configuration update

Create an updated order configuration based on the configurator. The configuration update is based on its `externalConfigurationId` attribute, which is required. The remaining attributes are optional, but if present, they must be compatible with the configurator.
 
???+ warning "Attention"
    If the change concerns options, all options for this configuration must be provided.

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

## Sending order updates

Send the order prepared according to the above guidelines as a query body using the `PATCH` method under the API `/sales-channel-api/v1/orders/{id}`, where `{id}` is the id of your order that you want to update. Place your [authorization data](../../authorization) in the query header.

??? "Example of a complete order body containing one configuration, in which the configuration name, price and value of one of the options have been changed"
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

??? "Response sample"
    === "JSON"
    ``` json
    {
        "message": "The command has been dispatched successfully.",
        "data": [],
        "errors": []
    }
    ```
