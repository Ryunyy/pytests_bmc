# Лабораторная работа №6. Сентюров МГ-311

## Отчет.

При выполнении лабораторной работы были написаны два класса пользователей: OBMCAPI и PublicAPI, описанные в файле [locustfile.py](https://github.com/Ryunyy/pytests_bmc/blob/main/locustfile.py). Каждый из них запускался через командную строку командой ```locust -f locustfile.py [classname]```

Ниже представлены скриншоты WebUI Locust при нагрузочном тестировании

### График параметров OpenAPI сайтов погоды и JSON плейсхолдеров, график статистики нагрузочного тестирования при 500 пользователях:
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/openAPI_Charts.png)
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/openAPI_Stats.png)

Как видно, API этих сайтов не особо подвержено большому количеству запросов, хотя в какой-то момент все-таки мы получили ошибки.

### График параметров OpenBMC API, график статистики нагрузочного тестирования и список ошибок при 100 пользователях:
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/OpenBMC_API_Charts_100.png)
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/OpenBMC_API_Stats_100.png)
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/OpenBMC_API_Failures_100.png)

Как видим, в какой-то момент вместо нормальных ответов мы стали плучать ошибки. Сервер перестал отвечать и выдавать доступ пользователям, из-за чего пояились ошибки аутентификации. Проверим, на какойм количестве пользователей появляются ошибки - запустим тестирование для 50 и для 75 пользователей.

### График параметров OpenBMC API, график статистики нагрузочного тестирования и список ошибок при 100 пользователях:
### (На графике слева указаны параметры для 50 пользоветелей, справа - для 75)
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/OpenBMC_API_Charts_50_75.png)
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/OpenBMC_API_Stats_75.png)
![plot](https://github.com/Ryunyy/pytests_bmc/blob/main/images/OpenBMC_API_Failures_75.png)

Как видимо, ошибки на 50 пользователях не появляются, но для 75 их уже достаточно. Следовательно, делаем вывод, что в районе 65-75 пользователях, одновременно подающих запросы на сервер, API падает и не отвечает на запросы некоторое время.
