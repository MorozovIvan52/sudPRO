# ПарсерСуд (parserSupreme)

Парсер документов и сервис определения территориальной подсудности (мировые суды РФ).

## Сервис подсудности (court_locator)

Поиск мирового суда по **GPS-координатам (WGS84)** или по **текстовому адресу**. REST API, экспорт границ в GeoJSON.

**Режим только бесплатные источники** (без коммерческих API):

- Документация: **[docs/court_locator_free_sources.md](docs/court_locator_free_sources.md)**
- Быстрый старт: [docs/court_locator_quickstart.md](docs/court_locator_quickstart.md)
- В `.env` не задавать `DADATA_TOKEN` и `YANDEX_GEO_KEY` — используется Nominatim (OSM) и локальная БД.

### Запуск API

```bash
pip install -r requirements.txt
python run_court_locator_api.py
```

Или: `uvicorn court_locator.api:app --host 0.0.0.0 --port 8000`

Документация API: http://localhost:8000/docs

### Первый тест (подготовка БД + один пример)

```bash
python first_test_jurisdiction.py
```

Используются пример: **Петрова Мария Сергеевна**, адрес **г. Санкт-Петербург, Невский проспект, д. 5**, паспорт 780 (СПб). Вывод: суд № 45 Центрального района СПб, госпошлина, источник.

### Все тесты

```bash
python tests_run.py
```

---

Интеграция модуля court_locator: [docs/court_locator_integration.md](docs/court_locator_integration.md).
