# Inspekcja kontenerów 
Ćwiczenie pokaże w jaki sposób uzyskać informacje o konfiguracji kontenerów i parametrach jego pracy.

1. Pokaż pełną informację o kontenerze "internal-wordpress"
```
sudo docker inspect internal-wordpress
```
![Docker Inspect](img/lab5_1.png)

2. Pokaż zajętość dysku przez kontener "internal-wordpress"
```
sudo docker inspect --size internal-wordpress -f '{{ .SizeRootFs }}'
```
![Docker Inspect](img/lab5_2.png)

3. Pokaż zajętość dysku przez kontener "internal-wordpress" ale tylko dopisanych od czasu uruchomienia. 
```
sudo docker inspect --size internal-wordpress -f '{{ .SizeRw }}'
```
![Docker Inspect](img/lab5_3.png)

4. Pokaż konfigurację sieciową kontenera "internal-wordpress"
```
sudo docker inspect --format='{{range .NetworkSettings.Networks}}{{.MacAddress}}{{end}}' internal-wordpress
```
![Docker Inspect](img/lab5_4.png)

5. Pokaż adress IP kontenera "internal-wordpress"
```
sudo docker inspect --format='{{json .NetworkSettings}}' internal-wordpress
```
![Docker Inspect](img/lab5_5.png)

6. Pokaż Nazwę kontnera oraz status dla wszystkich kontenerów
```
sudo docker ps -a --format '{{.Names}}\t{{.Status}}'
```
![Docker Inspect](img/lab5_6.png)

7. Pokaż nazwę kontenera oraz ścieżkę do LogPath dla wszystkich kontnerów
```
sudo docker inspect --format='{{.Name}} {{.LogPath}}' $(sudo docker ps -qa)
```
![Docker Inspect](img/lab5_7.png)

8. Sprawdź ile zajmuja wszystkie logi kontenerów
```
sudo su
du -sh /var/lib/docker/containers/*/*-json.log
```
![Docker Inspect](img/lab5_8.png)
