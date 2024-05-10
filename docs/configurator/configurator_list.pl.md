# Dane konfiguratora
Dane (ciała) konfiguratorów dostępne są pod adresem `{{ configurator_source_path }}{configuratorId}.json`

Wszystko co musisz zrobić aby otrzymać dane to wysłać zapytanie GET pod wskazany adres, gdzie {configuratorId} to id konfiguratora, którego dane chcesz pobrać.

Numery Id dostępnych konfiguratorów uzyskasz poprzez zapytanie `GET` pod API `{{ domain.base_url }}/api/v1/configurators/ids`

Teraz wystarczy zastąpić `{configuratorId}` rzeczywistym numerem id aby otrzymać ciało konfiguratora.
