# Configurator data
Data (bodies) of configurators are available at `{{ configurator_source_path }}{configuratorId}.json`

All you need to do to receive the data is send a GET request to the indicated address, where {configuratorId} is the id of the configurator whose data you want to download.

You can obtain the ID numbers of available configurators via the `GET` query under API `{{ domain.base_url }}/api/v1/configurators/ids`

Now just replace `{configuratorId}` with the actual id number to get the configurator body.
