# Radio_Binaries

## SPRZĘT / HARDWARE
MCU: **ESP32-S3 N16R8**<br>
Wyświetlacz / Display SPI: **ILI9341** / **ST7789** (240x320)
<br><br>
## KONFIGURACJA PINÓW / PINS CONFIGURATION

**I2S:**
```
I2S_DOUT  5    
I2S_BCLK  7    
I2S_LRC   6    
```
**Enkodery/Encoders:**
```
buttonEncoderR 15
S1_EncoderR    16
S2_EncoderR    17
buttonEncoderL  4
S1_EncoderL     1
S2_EncoderL     2
```
**TFT ILI9341 lub/or ST7789:**
```
TFT_DC   14
TFT_RST  18
TFT_CS   10
TFT_BL   21
TFT_MOSI 11 
TFT_SCLK 12 
TFT_MISO 13
```
<br>

## URUCHAMIANIE RADIA (podłączanie do zasilania)

**A) Przyciski OBU enkoderów** wciśnięte jednocześnie podczas uruchamiania radia.
- Następnie, jeżeli w ciągu 3 sekund naciśnięty zostanie przycisk prawego enkodera, będzie można wybrać startowe: listę odtwarzania i stację (np. w przypadku, gdy ostatnio wybrana stacja nie działa - po restarcie, w trakcie normalnego uruchomienia, radio zawsze wybiera ostatnią stację)
- Jeżeli w ciągu 3 sekund nie zostanie naciśnięty przycisk prawego enkodera, nastąpi uruchomienie portalu konfiguracyjnego pozwalającego na: a) konfigurację sieci WiFi, b) wgranie firmware’u w postaci pliku *.bin. Należy podłączyć się do sieci „RadioInternetoweAP”, po czym wejść na stronę „192.168.4.1” i wybrać odpowiednią opcje: Configure WiFI lub Update.

**B) Przycisk LEWEGO enkodera** wciśnięty podczas uruchamiania radia -> uruchomienie portalu konfiguracyjnego (jak w p. 1A), ale po podłączeniu się do skonfigurowanej wcześniej sieci WiFi. Do portalu można zalogować się tak jak opisano w p.1A lub po wpisaniu w przeglądarkę internetową adresu IP radia w obecnie połączonej sieci WiFi.

**C) Przycisk PRAWEGO enkodera** wciśnięty podczas uruchamiania radia -> uruchomienie portalu wczytywania list odtwarzania do radia po podłączeniu się do skonfigurowanej wcześniej sieci WiFi. Do portalu można zalogować się po wpisaniu w przeglądarkę internetową adresu IP radia w obecnie połączonej sieci WiFi. Do radia można wczytać listy odtwarzania z pliku tekstowego, który musi być dostępny z internetu, np. mój plik: https://raw.githubusercontent.com/cniedzi/Internet_Radio_Playlisty/main/_Playlisty.txt (<ins>uwaga:</ins> nie gwarantuję dostępności tego pliku w nieskończoność :smile:).

Format pliku konfiguracyjnego z listami odtwarzania:
```
Playlist=Name of Playlist 1
Station Name 1; station_address_1
Station Name 2; station_address_2
…
Station Name n; station_address_n

Playlist=Name of Playlist 2
Station Name 1; station_address_1
Station Name 2; station_address_2
…
Station Name n; station_address_n
…
```
<br>

## NORMALNA PRACA RADIA

**A) LEWY enkoder**
- Obrót lewo/prawo -> regulacja głośności
- Przycisk krótko -> włączenie/wyłączenie mute
- Przycisk długo -> włączenie/wyłączenie trybu dodatkowych informacji; obrót prawego enkodera w tym trybie przełącza wyświetlanie:<br>
  a) wskaźnika VU,<br>
  b) analogowych wskaźników VU,<br>
  c) 32-segmentowego analizatora widma ze wskaźnikiem VU,<br>
  d) 16-segmentowego analizatora widma,<br>
  c) pełnego widma,<br>
  d) spektrogramu,<br>
  e) ustawień parametrów dźwięku,<br>
  f) ustawień trybów wyświetlania wskaźnika poziomu i trybu Led RGB (dla ESP32-S3)<br>
  g) informacji o radiu<br>
  Długie wciśnięcie przycisku lewego enkodera podczas wyświetlania: wskaźnika VU, 7-segmentowego analizatora widma, pełnego widma lub spektrogramu powoduje zapisanie do pamięci domyślnego ekranu, który będzie wyświetlony po wejściu do trybu dodatkowych informacji pod warunkiem, że wyciszenie dźwięku "Mute" nie jest aktywne. Jeżeli "Mute" jest aktywne, defaultowym trybem jest ekran ustawień parametrów dźwięku.
- Czterokrotne naciśnięcie przycisku w ciągu 1 sekundy przełącza tryby pracy wbudowanej diody LED RGB (która miga w rytm muzyki :smile:): wyłączona / stale włączona / włączona tylko w trybie dodatkowych informacji. <ins>Uwaga:</ins> dioda LED RGB musi być aktywowana poprzez zalutowanie zworki w module ESP32-S3 DevKit.

**B) PRAWY enkoder**
- Obrót lewo/prawo -> wybór stacji z aktualnej listy odtwarzania
- Przycisk krótko -> wyświetlenie listy stacji z aktualnej listy odtwarzania. Obrót prawego enkodera w tym trybie wybiera stację; krótkie naciśnięcie dekodera aktywuje wybraną stację z listy
- Przycisk długo -> przełączenie trybu wyboru stacji / listy odtwarzania. W trybie wyboru listy odtwarzania, obrót prawego enkodera powoduje wybór listy odtwarzania i wczytanie stacji z tej listy. Po wybraniu listy odtwarzania, po 2 sekundach, radio automatycznie powraca do trybu wyboru stacji z listy odtwarzania.

**C) Wciśnięcie przycisków OBU enkoderów** jednocześnie powoduje ponowne uruchomienie radia.

**D)** Wejście na stronę http://adres_ip_radia -> portal konfiguracyjny

<br><br>
