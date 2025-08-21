# Radio_Binaries

Radio Internetowe dla ESP32-S3 i ESP32-P4 (płytka rozwojowa Waveshare).

Opis funkcji:

URUCHAMIANIE RADIA (podłączanie do zasilania)
A) Przyciski OBU enkoderów wciśnięte jednocześnie podczas uruchamiania radia -> uruchomienie portalu konfiguracyjnego do: a) konfiguracji sieci WiFi, b) wgranie firmware’u w postaci pliku *.bin. Należy podłączyć się do sieci „RadioInternetoweAP”, po czym wejść na stronę „192.168.4.1” i wybrać odpowiednią opcje: Configure WiFI lub Update.

B) Przycisk LEWEGO enkodera wciśnięty podczas uruchamiania radia -> uruchomienie portalu konfiguracyjnego (jak w p. 1A), ale po podłączeniu się do skonfigurowanej wcześniej sieci WiFi. Do portalu można zalogować się tak jak opisano w p.1A lub po wpisaniu w przeglądarkę internetową adresu IP radia w obecnie połączonej sieci WiFi.

C) Przycisk PRAWEGO enkodera wciśnięty podczas uruchamiania radia -> uruchomienie portalu wczytywania list odtwarzania do radia po podłączeniu się do skonfigurowanej wcześniej sieci WiFi. Do portalu można zalogować się po wpisaniu w przeglądarkę internetową adresu IP radia w obecnie połączonej sieci WiFi. Do radia można wczytać listy odtwarzania z pliku tekstowego, który musi być dostępny z internetu, np. mój plik: https://raw.githubusercontent.com/cniedzi/Internet_Radio_Playlisty/main/_Playlisty.txt (nie gwarantuję dostępności tego pliku w nieskończoność 🙂 ).

Format pliku konfiguracyjnego z listami odtwarzania:

Playlist=Nazwa listy odtwarzania 1 Nazwa stacji 1; adres_stacji_1 Nazwa stacji 2; adres_stacji_2 … Nazwa stacji n; adres_stacji_n Playlist=Nazwa listy odtwarzania 2 Nazwa stacji 1; adres_stacji_1 Nazwa stacji 2; adres_stacji_2 … Nazwa stacji n; adres_stacji_n …

NORMALNA PRACA RADIA
A) LEWY enkoder

obrót lewo/prawo -> regulacja głośności
przycisk krótko -> włączenie/wyłączenie mute
przycisk długo -> wyświetlenie/wyłączenie wskaźnika VU na całym ekranie. Obrót prawego enkodera w trybie wskaźnika VU na całym ekranie przełącza wyświetlanie wskaźnika VU i informacji o radiu)
czterokrotne naciśnięcie przycisku w ciągu 1 sekundy przełącza tryby pracy wbudowanej diody LED RGB (która miga do rytmu muzyki:) - wyłączona / stale włączona / włączona tylko, gdy aktywny jest wskaźnik VU na całym ekranie. Uwaga - dioda LED RGB musi być aktywowana poprzez zalutowanie zworki w module ESP32-S3 DevKit.
B) PRAWY enkoder

obrót lewo/prawo -> wybór stacji z aktualnej listy odtwarzania
przycisk krótko -> wyświetlenie listy stacji z aktualnej listy odtwarzania. Obrót prawego enkodera w tym trybie wybiera stację; krótkie naciśnięcie dekodera aktywuje wybraną stację z listy
przycisk długo -> przełączenie trybu wyboru stacji / listy odtwarzania. W trybie wyboru listy odtwarzania, obrót prawego enkodera powoduje wybór listy odtwarzania i wczytanie stacji z tej listy. Po wybraniu listy odtwarzania, po 2 sekundach, radio automatycznie powraca do trybu wyboru stacji z listy odtwarzania.
C) Wciśnięcie przycisków OBU enkoderów jednocześnie powoduje ponowne uruchomienie radia.

D) Wejście na stronę http://adres_ip_radia -> portal konfiguracyjny

/************************************************************************************************************************************************************************************************

Function Description:

STARTING THE RADIO (connecting to power)
A) Pressing both encoder buttons simultaneously while starting the radio → launches the configuration portal for: a) WiFi network setup, b) uploading firmware in the form of a *.bin file. Connect to the “RadioInternetoweAP” network, then go to “192.168.4.1” in your browser and choose the appropriate option: Configure WiFi or Update.

B) Pressing the LEFT encoder button while starting the radio → launches the configuration portal (as in point 1A), but connects to the previously configured WiFi network. You can log in to the portal as described in point 1A or by entering the radio’s IP address in the browser within the currently connected WiFi network.

C) Pressing the RIGHT encoder button while starting the radio → launches the playlist upload portal after connecting to the previously configured WiFi network. You can log in to the portal by entering the radio’s IP address in the browser within the currently connected WiFi network. Playlists can be uploaded from a text file that must be accessible via the internet, e.g., my file: https://raw.githubusercontent.com/cniedzi/Internet_Radio_Playlisty/main/_Playlisty.txt (note: I do not guarantee permanent availability of this file 🙂).

Playlist configuration file format:

markdown Kopiuj Edytuj

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

NORMAL RADIO OPERATION
A) LEFT encoder

Rotate left/right → adjusts volume

Short press → toggles mute on/off

Long press → toggles full-screen VU meter on/off. (While in full-screen VU meter mode, rotating the right encoder toggles between the VU meter and radio info display.)

Pressing the button four times within 1 second switches the operating mode of the built-in RGB LED (which flashes to the music beat🙂): off / always on / on only when full-screen VU meter is active. Note: The RGB LED must be enabled by soldering a jumper on the ESP32-S3 DevKit module.

B) RIGHT encoder

Rotate left/right → selects station from the current playlist

Short press → displays the station list from the current playlist. While in this mode, rotating the right encoder selects a station; short press activates the selected station

Long press → switches between station selection mode and playlist selection mode. In playlist selection mode, rotating the right encoder selects and loads a playlist. After selecting a playlist, the radio automatically returns to station selection mode after 2 seconds.

C) Pressing both encoder buttons simultaneously → restarts the radio.

D) Opening http://radio_ip_address in a web browser → opens the configuration portal.
