Микросервис для запуска ML-модели 

Пример запуска из директории mle-sprint3-docker:

```bash
$ uvicorn app.churn_app:app --reload --port 8081 --host 0.0.0.0
```
Для просмотра документации API и совершения тестовых запросов зайти на  http://127.0.0.1:8081/docs


Если используется другой порт, то заменить 8081 на этот порт

Построить образ:
```bash
$ docker build . --tag fast_api:1
```

Запуск:
```bash
$ docker run --rm -p 4601:8081 --name churn fast_api:1
```

Запуск с переменными окружения и volume:
```bash
$ docker run \
  --rm \
  -p 4601:8081 \
  --env-file .env \
  -v ./models:/models \
  --name churn fast_api:2
```