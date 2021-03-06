
# RescueMe

Projekt "RescueMe" im Rahmen der Vorlesung Entwicklung mobiler Applikationen an der DHBW Stuttgart Campus Horb.
#### Projektmitglieder
Marius Armbruster, Jakub Cielecki, Robin Herrmann, Simon Meltzer, Nico Riedlinger, Kevin Schock, Lukas Sieber

Die primäre Aufteilung war dabei wie folgt:
##### Frontend: Simon Meltzer, Nico Riedlinger, Lukas Sieber
##### Backend: Marius Armbruster, Robin Herrmann, Kevin Schock

#### Hintergrund
App zur Verwaltung personenbezogener Gesundheitsdaten wie bspw. Name, Blutgruppe, Organspendestatus, Notfallkontakt, Vorerkrankungen, Allergien, Impfstatus, … und Auslesen dieser über QR-Code oder NFC-Chip
## Ausführen der Applikation
### Die eigentliche App für Benutzer:
![QR Code](https://qr.expo.dev/expo-go?owner=simonmeltzer&slug=RescueMe&releaseChannel=default&host=exp.host)
* https://expo.dev/@simonmeltzer/RescueMe

### Die App für Sanitäter:
![QR Code](https://qr.expo.dev/expo-go?owner=simonmeltzer&slug=RescueMeScanner&releaseChannel=default&host=exp.host)
* https://expo.dev/@simonmeltzer/RescueMeScanner

Die Idee: Sanitäter müssen sich zunächst verifizieren, da mit dieser App personenbezogene Daten ausgelesen werden können. Die Scanner-App ist daher wirklich nur für Ersthelfer / Sanitäter gedacht. Die Evaluation wird hierbei vom RescueMe-Team vorgenommen.\
@Torsten: Die Zugangsdaten für die Sanitäter-App erhälst du per Mail.

Die Applikation wurde mit Expo erstellt, hierzu einfach den QR-Code scannen in der Expo-App.

## App-Kriterien
### Muss-Kriterien:
- [x]  Loginfunktionalität
- [x]  Erfassung von Gesundheitsdaten in App
- [x]  Auslesen der Daten über QR-Code

### Soll-Kriterien:
- [ ]  Schreiben der Daten auf und Lesen von NFC-Chip

### Wunsch-Kriterien:
- [ ]    2-Faktor-Authentifizierung
- [x]      Benachrichtigung Notfallkontakt
- [x]     Benachrichtigung über Notfall von Benutzenden
- [x]   Guide zu Ersthilfemaßnahmen
- [x]    Three Words zur Lokalisierung von Benutzenden
### Weitere Aspekte:
- [x] Darkmode / Lightmode in der App
- [x] Google API Abfragen, um nahegelegene Krankenhäuser anzeigen zu lassen
- [x] Lauffähigkeit auf Android / iOS

### Informationen:
Die 2-Faktor-Authentifizierung über SMS konnte nicht implementiert werden, da pro SMS bereits nicht-geringe Kosten anfallen. Auch um Spam zu vermeiden, wurde entschieden, die 2-Faktor-Authentifizierung nicht zu veröffentlichen. Im aktuellen Stand ist bisher auch noch das Lesen und Schreiben auf einen NFC-Chip nicht implementiert.

### Schaubild zur Datenverschlüsselung im QR-Code
![verschlüsselung (1)](https://user-images.githubusercontent.com/67149095/173415495-07aadb3a-def7-4eb1-884a-522201e611d5.jpg)\
Jeder Anwender bekommt beim ersten Login einen LocalKey erstellt. Dieser wird verschlüsselt, durch den GlobalKey, in die Datenbank geschrieben. Beim QR-Code-Erstellen wird der verschlüsselte QR-Code aus der Datenbank gelesen und mit dem GlobalKey entschlüsselt. Mit Hilfe des entschlüsselten LocalKey werden die Daten des Anwenders verschlüsselt und in einen QR Code umgewandelt.  
