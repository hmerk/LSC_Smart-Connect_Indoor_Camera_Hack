# LSC_Smart-Connect_Indoor_Camera_Hack
Hack zum Aktivieren von ONVIF (und RTSP) auf der LSC Smart Connect Innenkamera von Action

## Grundlegendes Tutorial 
https://github.com/guino/BazzDoorbell/issues/2

## Rooten der Kamera
- Legen Sie die Datei [ppsFactoryTool.txt](https://github.com/n3odym3/LSC_Smart-Connect_Indoor_Camera_Hack/blob/main/ToRoot) auf einer SD-Karte ab (FAT32)
- WLAN-SSID und PASSWORT einrichten
- Legen Sie die SD-Karte in die Kamera ein
- Kamera starten
- Finden Sie Ihre IP-Adresse mit dem [ONVIF Device Manager](https://sourceforge.net/projects/onvifdm/)
- Stellen Sie die folgenden HTTP-Anforderungen
  - http://admin:admin@CAMERA.IP:8090/devices/deviceinfo => Antwort : ppstrong-a3-tuya2_lsc-4.0.6.20210311
  - http://admin:admin@CAMERA.IP:8090/proc/cmdline => Antwort speichern
  - http://admin:admin@CAMERA.IP:8090/proc/self/root/etc/init.d/S90PPStrong => Stellen Sie sicher, dass MTDNUM=5 nicht auskommentiert ist (ohne #)
- Wenn alles in Ordnung ist, schalten Sie die Kamera aus und stellen Sie die SD-Karte wieder her
- Platzieren von [ToRoot](https://github.com/n3odym3/LSC_Smart-Connect_Indoor_Camera_Hack/blob/main/ToRoot) auf der SD-Karte
  - env
  - initrun.sh
  - ppsMmcTool.txt
- Legen Sie die SD-Karte in die Kamera ein
- Drücken Sie die Reset-Taste
- Schließen Sie die Kamera an (halten Sie die Reset-Taste gedrückt)
- Halten Sie die Taste 5 Sekunden lang gedrückt (die Kamera sollte zwischen rot und blau blinken)
- Die Kamera sollte dann booten
- Testen Sie, ob der Hack mit der folgenden HTTP-Anfrage funktioniert hat 
  - http://admin:admin@CAMERA.IP:8090/proc/self/root/mnt/mmc01/hack => Antwort: erledigt
 
## Hacken der Kamera

- ToHack-Dateien auf SD-Karte ablegen
  - cgi-bin
  - busybox
  - custom.sh
  - dropbearmulti
  - httpd.conf
  - index.html
  - jpeg-arm
  - passwd
  - set
  - upload.html
- Kopieren Sie die ppsapp-Datei aus /home/app
- Stellen Sie sicher, dass die MD5 [ici](https://github.com/guino/ppsapp-rtsp/issues/1) (suchen Sie ppstrong-a3-tuya2_lsc-4.0.6.20210311) 
- Gehe zu https://www.marcrobledo.com/RomPatcher.js/
- ppsapp-Datei auswählen
- ppsapp-Datei auswählen [aus](https://github.com/guino/ppsapp-rtsp/files/6880255/ppsapp-onvif.zip)
- Benennen Sie die heruntergeladene ppsapp.txt-Datei nach dem Patch in ppsapp um
- Platzieren Sie die gepatchte ppsapp-Datei im Stammverzeichnis der SD-Karte
- Legen Sie die SD-Karte in die Kamera ein und schließen Sie die Kamera an
- Die Kamera sollte zweimal booten!
- Bravo, die Kamera ist gepatcht
- Versuchen Sie, den RTSP-Stream im ONVIF-Geräte-Manager zu öffnen.
