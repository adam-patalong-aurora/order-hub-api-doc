# Create an order

??? "Example of a complete order body containing one configuration and some additional photo prints"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/body_create.json"
        ```
??? "Response sample"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/response.json"
        ```

## Step by step

### Create order
Create an order body in JSON format using attributes and values appropriate for your store.
Next, add the configurations or photo prints to the order body.

??? "Example of what an order should look like"
    === "JSON"
        ```json linenums="1" hl_lines="2-44"
        --8<-- "docs/orders/code/body_create.json"
        ```

## Configuration

Create an order configuration based on the configurator. An order may contain several configurations. A properly created configuration consists of a configuration body and has options on the basis of which the order value will be calculated.

If you do not want to add configurations, do not add the `configurations` attribute to the order body.

??? "Configuration body example"
    === "JSON"
        ```json linenums="1"
        --8<-- "docs/orders/code/configuration.json"
        ```

??? info "Information"
    The entire order may be large in size. It depends on the number of configurations the order has and the options included in them.

### Photo prints

Based on your configurator, create data for additional prints of the order. Additional prints are identified by the `externalPhotoPrintId` attribute. In the `formats` attribute, you have to add all additional print data for this `externalPhotoPrintId`. 

If you do not want to add additional prints, do not add the `photoPrints` attribute to the order body.

??? "Body example of additional prints"
    === "JSON"
        ```json linenums="1" hl_lines="2"
        --8<-- "docs/orders/code/photo_prints.json"
        ```

## Sending the order

???+ warning "Information"
    The order must have at least one of the options: configuration or photo prints.

Send the order prepared according to the above information as a query body using the `POST` method under the API `{{ domain.base_url }}/api/v1/sales-channels-orders`. Place [authorization data](../../authorization) in the query header.
