# Свод — скелет

Учебный скелет сервиса «Свод». Весь путь запроса уже работает:
файл → текст → модель → сохранение → страница. Часть слоёв пока отвечает заглушками.

## Структура

```
app/
  main.py           API: эндпоинты, склейка слоёв
  extract.py        обработка: текст из файла (заглушка)
  llm.py            модель: запрос к Ollama (заглушка или настоящий вызов)
  storage.py        хранение: список в памяти (заглушка)
  templates/
    index.html      интерфейс: форма и результат
requirements.txt    зависимости
```

## Запуск (Windows, PowerShell)

```
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

Открыть в браузере: http://127.0.0.1:8000
Проверить эндпоинты без интерфейса: http://127.0.0.1:8000/docs

## Подключить настоящую модель

Нужна запущенная Ollama и скачанная модель: `ollama pull gemma3:4b`.

```
$env:USE_OLLAMA="1"
uvicorn app.main:app --reload
```

## Что дальше

| Заглушка | Чем заменить |
| --- | --- |
| extract.py | PyMuPDF, python-docx, Tesseract |
| storage.py | PostgreSQL |
