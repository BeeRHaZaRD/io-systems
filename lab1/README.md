# Лабораторная работа 1
## Вариант 3

**Название:** "Разработка драйверов символьных устройств"

**Цель работы:** получение знаний и навыков разработки драйверов символьных устройств для ОС GNU/Linux.

## Описание функциональности драйвера

При записи в файл символьного устройства текста, содержащего цифры, должен запоминаться результат суммы всех чисел, разделенных другими символами (буквы, пробелы и т.п.). Последовательность полученных результатов с момента загрузки модуля ядра должна выводиться при чтении созданного файла /proc/varN в консоль пользователя.

При чтении из файла символьного устройства в кольцевой буфер ядра должен осуществляться вывод тех же данных, которые выводятся при чтении файла /proc/varN.

## Инструкция по сборке

Сборка драйвера
```
make all
```
Создается файл драйвера lab1.ko

Загрузка драйвера в ядро:
```
sudo insmod lab1.ko
```

Выгрузка драйвера из ядра:
```
sudo rmmod lab1.ko
```
Очистка директории от файлов сборки:
```
make clean
```

## Инструкция пользователя

Запись строки, содержащей числа:
```
echo "a123b456c" > /dev/lab
```

Результат операции будет записан в /proc/VAR3. Прочитать результат:
```
cat /proc/VAR3
```

## Примеры использования

```
echo "aaa1bbb2ccc3" > /dev/lab
cat /proc/VAR3 
# 6
```

```
echo "123" > /dev/lab
cat /proc/VAR3 
# 6 123
```

```
echo "123abc456" > /dev/lab
cat /proc/VAR3
# 6 123 579
```
