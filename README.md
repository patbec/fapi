# fapi

Hiermit können Dateien von Sharehostern mithilfe des Dienstes **premiumize.me** in HTTPS Links verwandelt und via Kommandozeile heruntergeladen werden. Weitere Informationen finden Sie unter der Webseite [Premiumize](https://www.premiumize.me).

## Getting Started

Das Modul **fapi** ist die Basis und bietet folgende Funktionen:

```
# Prüfen ob der Account gültig ist
get_account_status(username, password)
```

```
# Einen Link mithilfe der API umwandeln
getFile(url, user, password)
```

Die Erweiterung **run.py** bietet zusätzliche Funktionen um das Modul z.B in einer Kommandozeile zu benutzen:
```
python -m fapi.run --help

Usage: run.py [options]

Options:
  -h, --help            show this help message and exit
  -u username, --username=username
                        Benutzen Sie hier Ihre Kundennummer
  -p password, --password=password
                        Benutzen Sie hier Ihren PIN-Code
  -f folder, --folder=folder
                        Ordner indem die heruntergeladenen Dateien gespeichert
                        werden
```
				
Nach dem Aufruf von **run.py** wird der Accountstatus geprüft, anschließend werden alle Links die sich in der **Zwischenablage** befinden in dem mit **--folder** angegebenen Ordner heruntergeladen.

### Voraussetzungen

Das Modul setzt Python Version 2.x mit folgenden Modulen voraus:

**fapi.py**
* json
* requests
* urllib

**run.py**
* fapi
* pyperclip
* urllib2
* progressbar

Die jeweiligen Module finden Sie unter [PyPI](https://pypi.python.org/pypi) und können mit **pip install <paket name>** installiert werden.

### Vorbereitung

**Linux**

Python ist in einer Ubuntu-Standardinstallation bereits enthalten, falls nicht kann es mit folgendem Befehl installiert werden:
```
sudo apt-get install python
sudo apt-get install python-pip
```

**Windows**

Python herunterladen und installieren:
[Download Python 2.x](https://www.python.org/downloads/)

### Installation

Installieren Sie die benötigeten Module mit den folgendem Befehl:
```
pip install fapi requests
```

Soll auch **run.py** benutzt werden, müssen noch diese zusätzlichen Pakete installiert werden:
```
pip install pyperclip urllib2 progressbar
```

## Beispiel

Kopieren Sie die zu herunterladenen Links in die Zwischenablage und führen Sie den folgenden Befehl aus:
```
python -m fapi.run --username <Kundennummer> --password <PIN> --folder <Ordner>
```

Mit **python -m fapi.run --help** erhalten Sie mehr Informationen.

Beispiel-Ausgabe:
```
Benutzerkonto 0000000000 (premium)
Fair-Use Status: 0%

Meine-Test-Dateien.part01.rar: 100% [000000000000000000] Time: 0:01:02   2.54 MB/s
Meine-Test-Dateien.part02.rar: 100% [000000000000000000] Time: 0:01:04   2.44 MB/s
Meine-Test-Dateien.part03.rar: 100% [000000000000000000] Time: 0:01:04   2.45 MB/s
Meine-Test-Dateien.part04.rar: 100% [000000000000000000] Time: 0:01:01   2.59 MB/s
Meine-Test-Dateien.part05.rar: 100% [000000000000000000] Time: 0:00:59   2.64 MB/s
Meine-Test-Dateien.part06.rar: 100% [000000000000000000] Time: 0:01:01   2.57 MB/s
Meine-Test-Dateien.part07.rar: 100% [000000000000000000] Time: 0:01:00   2.61 MB/s
Meine-Test-Dateien.part08.rar: 100% [000000000000000000] Time: 0:01:04   2.44 MB/s
Meine-Test-Dateien.part09.rar: 100% [000000000000000000] Time: 0:01:00   2.64 MB/s
Meine-Test-Dateien.part10.rar: 100% [000000000000000000] Time: 0:00:42   2.64 MB/s

Drücken Sie eine beliebige Taste . . .
```

## Extra

Um nicht jedes mal Kundennummer und Passwort eingeben zu müssen, legen Sie eine Datei mit folgendem Inhalt an:

Linux - 'start.sh'
```
python -m fapi.run --username 000000000 --password xxxxxxxxxxxxxxxx --folder /home/Downloads/
read -rsp $'Press [Enter] key to close...\n'
```

Windows - 'start.bat'
```
@echo off
python -m fapi.run --username 000000000 --password xxxxxxxxxxxxxxxx --folder %USERPROFILE%\Downloads\
echo.
pause
```

Gehen Sie nach [Account](https://www.premiumize.me/account) um Ihre Zugangdaten herauszufinden. Tragen Sie anschließend Ihre **Kundennummer** in **--username**, Ihre **PIN** in **--password** und das Download-Verzeichnis in **--folder** ein.

Info: Benutzername und Passwort werden verschlüsselt übertragen

Die Webseite [dcrypt](https://dcrypt.it) ermöglicht das entschlüsseln von DLC Dateien. Kopieren Sie die Links anschließend in die Zwischenablage und rufen Sie die jeweilige 'start' Datei auf um das herunterladen zu beginnen.

## Autor

* **Patrick Becker** - [GitHub](https://github.com/patbec)

E-Mail: [github@bec-wolke.de](mailto:github@bec-wolke.de)

## Lizenz

Dieses Projekt ist unter der MIT-Lizenz lizenziert - Weitere Informationen finden Sie in der Datei [LICENSE](LICENSE)

## tl;dr
```
pip install fapi requests pyperclip urllib2 progressbar
python -m fapi.run --username <Kundennummer> --password <PIN> --folder <Ordner>
```
