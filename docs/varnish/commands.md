# Przydatne polecenia

## Wejście w bash kontenera varnisha

Używając terminala sprawdź nazwę kontenera varnisha
```bash
docker ps
```

Wejście w bash varnisha

```bash
docker exec -ti magento246_varnish bash
```

## Dostępne narzędzia

### varnishlog
Pozwala na przeglądanie logów varnisha w czasie rzeczywistym.

```bash
varnishlog
```

### varnishadm
To narzędzie wiersza poleceń do zarządzania serwerem Varnish Cache. Umożliwia administratorom i użytkownikom Varnish interakcję z serwerem Varnish poprzez wysyłanie poleceń administracyjnych. Można go używać do wykonywania różnych zadań, takich jak czyszczenie cache, ładowanie i weryfikowanie plików konfiguracyjnych VCL (Varnish Configuration Language), monitorowanie stanu serwera i wiele innych.
```bash
varnishadm
```

### varnishstat
To narzędzie wiersza poleceń służące do monitorowania i wyświetlania statystyk serwera Varnish Cache w czasie rzeczywistym. Dostarcza szczegółowe informacje o działaniu serwera, takie jak liczba żądań, cache hits, cache misses, wykorzystanie pamięci i inne wskaźniki wydajności.
```bash
varnishstat
```

### varnishlist
Varnishlist pozwala na zbieranie i wizualizację danych dotyczących czasu odpowiedzi, opóźnień, trafień i missów w cache.
Umożliwia to identyfikowanie wąskich gardeł i problemów z wydajnością.
```bash
varnishlist
```

## Czyszczenie cache
Aby wyczyścić cache varnisha, należy wysłać zapytanie `PURGE` na adres URL, który chcemy wyczyścić.

Używając terminala wprowadź polecenie:
```bash
 curl -X PURGE -H 'X-Magento-Tags-Pattern: .*' http://domena.local
```
