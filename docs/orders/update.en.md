# Edit order

Editing an order involves changing the values ​​of order attributes or configuration. To edit an order, send a query using the `PATCH` method to the API `/sales-channel-api/v1/orders/{id}`, where `{id}` is the id of the order you want to edit.

???+ warning "Attention"
    If the change concerns options, all options for this configuration must be provided.

??? "Example of a complete order edit body containing one configuration"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/body_update.json"
        ```


??? "Response sample"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/response.json"
        ```


## Step by step

### Order update
Create the order body in JSON format using the updated attribute values.

???+ info "Information"
    You can specify just the attributes you want to update.

### Configuration update

Create an updated order configuration based on the configurator. The configuration update is based on its `externalConfigurationId` attribute. The updated configuration must be complete. It must contain all configuration attributes.
 
???+ warning "Attention"
    If the change concerns options, all options for this configuration must be provided.

??? "Configuration body example"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/configuration.json"
        ```

### Sending order updates

Send the order prepared according to the above guidelines as a query body using the `PATCH` method under the API `/sales-channel-api/v1/orders/{id}`, where `{id}` is the id of your order that you want to update. Place your [authorization data](../../authorization) in the query header.
