# Edit order

Editing an order involves changing the values of order attributes or configuration. To edit an order, send a query using the `PATCH` method to the API `{{ domain.base_url }}/sales-channel-api/v1/orders/{id}`, where `{id}` is the externalId of the order you want to edit and you set them when creating the order.

??? "Example of a complete order edit body containing one configuration and additional photo prints"
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

???+ warning "Attention"
    By editing the configuration, you can completely change its options, but they must be based on the same configurator as before.

???+ warning "Attention"
    You cannot delete a previously created configuration.

???+ tip "Hint"
    When editing a configuration, you must provide it with `externalConfigurationId`, which is a unique configuration identifier.
    By providing a new `externalConfigurationId` you can create a new configuration for the same order.


??? "Configuration body example"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/configuration.json"
        ```

### Additional prints updated

Based on your configurator, create updated data for additional prints of the order. Updating additional prints is based on their `externalPhotoPrintId` attribute. In the `formats` attribute, you must re-enter all additional print data for this `externalPhotoPrintId`.

??? "Body example of additional prints"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/photo_prints.json"
        ```

### Sending order updates

Send the order prepared according to the above guidelines as a query body using the `PATCH` method under the API `{{ domain.base_url }}/sales-channel-api/v1/orders/{id}`, where `{id}` is the id of your order that you want to update. Place your [authorization data](../../authorization) in the query header.
