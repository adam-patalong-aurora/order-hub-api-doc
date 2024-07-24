# Sprawdzenie działania

1. W terminalu uruchom komendę `curl -I http://domena.local` lub wejdź na stronę `http://domena.local` w przeglądarce.
2. W odpowiedzi zobaczysz nagłówek `X-Magento-Cache-Debug` z informacją o cache'owaniu:
    - `HIT` - strona została zwrócona z cache.
    - `MISS` - strona została zwrócona z serwera.
