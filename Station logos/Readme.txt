// W głównym pliku projektu (Projekt.ino lub main.cpp) dodajemy poniższe linie.

#include "Loga_Stacje.h"

int znajdzLogoStacji(String nazwaStacji);



void setup() {
  int iii = znajdzLogoStacji("RMF");
  if (iii != -1) {
    displayImage(STACJA_LOGO_SRODEK_X - stationLogoList[iii].w/2, STACJA_LOGO_SRODEK_Y - stationLogoList[iii].h/2, stationLogoList[iii].w, stationLogoList[iii].h, (unsigned short *)stationLogoList[iii].bitmap);
  }
}


void loop () {}


int znajdzLogoStacji(String nazwaStacji) {
  for (int i = 0; i < stationLogoList.size(); i++) {
    String _stationNameVector = stationLogoList[i].stationName;
    if (_stationNameVector == nazwaStacji) {
      return i; // Znaleziono! Zwracamy indeks w wektorze
    }
  }
  return -1; // Nie znaleziono stacji z logo
}
