# Konfiguracja

## docker_compose.yml
W swoim pliku `docker_compose.yml` dodaj Varnish jako usługę.

???+ Warning "Uwaga"
    Upewnij się, że usługa Varnish nasłuchuje na porcie `80:80`. Aby to tutaj przychodziły zapytania przeglądarki.

???+ Warning "Uwaga"
    Ustaw nasłuchiwanie nginx na port `8080:8080`.

??? "Przykład konfiguracji pliku `docker_compose.yml`"
    === "YML"
        ```yml linenums="1" hl_lines="3-13 19"
        --8<-- "docs/varnish/code/docker_compose.yml"
        ```

## varnish/default.vcl
W katalogu dockera `varnish` utwórz plik `default.vcl` z konfiguracją Varnish.

Konfigurację możesz wygenerować przez Panel Administracyjny Magento 2. 
Wchodzisz w `Stores` -> `Configuration` -> `Advanced` -> `System` -> `Full Page Cache` -> `Varnish Configuration` 
i klikasz `Export VCL for Varnish 5`.

???+ Warning "Uwaga"
    Ustaw backend varnisha na `nginx` port `8080:8080`.

???+ Warning "Uwaga"
    Aby umożliwić czyszczenie ustaw `acl purge` oraz `req.method == "PURGE"`.

??? "Przykład konfiguracji pliku `default.yml`"
    === "VCL"
        ```vcl linenums="1" hl_lines="9 10 21-25 32-49"
        --8<-- "docs/varnish/code/default.vcl"
        ```

## nginx/sites/website.conf
W katalogu dockera `nginx` utwórz plik `website.conf` z konfiguracją serwera nginx.

???+ Warning "Uwaga"
    Skonfiguruj nasłuchiwanie na port `8080`. 

??? "Przykład konfiguracji pliku `website.conf`"
    === "CONF"
        ```conf linenums="1" hl_lines="7"
        --8<-- "docs/varnish/code/website.conf"
        ```

## Magento 2
W Panelu Administracyjnym Magento 2 przejdź do `Stores` -> `Configuration` -> `Advanced` -> `System`
-> `Full Page Cache` -> `Caching Application` i ustaw `Varnish Cache`.

## /etc/hosts
Upewnij się, że wpis do pliku `/etc/hosts` kieruje domenę na lokalny adres IP `127.0.0.1`.
