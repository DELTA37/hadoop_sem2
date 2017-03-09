# Второй семинар по курсу Hadoop
Демонстрация работы вторичной сортировки в Hadoop.
Используем открытые данные метеостанций для нахождения максимумов температур за год.

# Сборка
Для сборки запустите `./gradlew jar`

# Запуск
Для запуска запустите на кластере
``hadoop jar hadoop_sem2.jar SecondarySortDemo /data/seminar2/meteo/*.gz``

# Просмотр на Google Maps
Чтобы визуализировать полученные результаты за определенный день на карте:  
- выберите из вывода reducer-а данные о нужном дне:
-- `fgrep 09.03 part-r-00000 >filtered.txt`
- подготовьте CSV с координатами и данными станций:  
-- `cat filtered.txt | ./ids2coords.py >temps.csv`
- подготовьте файл формата KML:
-- `gpsbabel -i csv -f temps.csv -o kml -F temps.kml`
- Используйте полученный файл в http://www.gpsvisualizer.com/
