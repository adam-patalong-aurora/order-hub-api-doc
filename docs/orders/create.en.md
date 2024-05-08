# Create an order

??? "Example of a complete order body containing one configuration"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/create.json"
        ```
??? "Response sample"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/response.json"
        ```

## Step by step

### Create order
Create an order body in JSON format using attributes and values appropriate for your store.

??? "Example of what an order should look like"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/order_body_structure.json"
        ```

## Configuration

Create an order configuration based on the configurator. An order may contain several configurations. A properly created configuration consists of a configuration body and has options on the basis of which the order value will be calculated.

??? "Configuration body example"
    === "JSON"
        ```json
        --8<-- "docs/orders/code/configuration_body_structure.json"
        ```

??? info "Information"
    The entire order may be large in size. It depends on the number of configurations the order has and the options included in them.

## Sending the order

Send the order prepared according to the above information as a query body using the `POST` method under the API `/api/v1/sales-channels-orders`. Place [authorization data](../../authorization) in the query header.
