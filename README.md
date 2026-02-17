# cryptoCMD: cryptoCurrency Market Data

[![PyPI Version][]][1] [![CI Status][]][2] [![License][]][3] [![Downloads][]][4] [![Ruff][]][5] [![GitHub Sponsors][]][6]


Cryptocurrency historical market price data scraper written in Python.

## Installation

```sh
pip install cryptocmd
```

to install from the latest source use following command

```sh
pip install git+git://github.com/guptarohit/cryptoCMD.git
```

## Usage

### CoinMarketCap Scraper

Following methods are available to get data in multiple formats from
<https://coinmarketcap.com>

#### To get all time historical data of a cryptocurrency

```python
from cryptocmd import CmcScraper

# initialise scraper without time interval
scraper = CmcScraper("XRP")

# get raw data as list of list
headers, data = scraper.get_data()

# get data in a json format
xrp_json_data = scraper.get_data("json")

# export the data as csv file, you can also pass optional `name` parameter
scraper.export("csv", name="xrp_all_time")

# Pandas dataFrame for the same data
df = scraper.get_dataframe()
```

#### To get data of a cryptocurrency which have same coin code as others

```python
from cryptocmd import CmcScraper

# initialise scraper with coin name as well
scraper = CmcScraper(coin_code="sol", coin_name="solana")

# get raw data as list of list
headers, data = scraper.get_data()

# get data in a json format
solana_json_data = scraper.get_data("json")

# export the data as csv file, you can also pass optional `name` parameter
scraper.export("csv", name="solana_all_time")

# Pandas dataFrame for the same data
df = scraper.get_dataframe()
```

#### To get data of a cryptocurrency for some days

```python
from cryptocmd import CmcScraper

# initialise scraper with time interval
scraper = CmcScraper("XRP", "15-10-2017", "25-10-2017")

# get raw data as list of list
headers, data = scraper.get_data()

# get data in a json format
json_data = scraper.get_data("json")

# export the data to csv
scraper.export("csv")

# get dataframe for the data
df = scraper.get_dataframe()
```

##### Following are the columns of the data

`Date, Open, High, Low, Close, Volume, Market Cap, Time Open, Time High, Time Low, Time Close`

## Acknowledgements

The data is being scrapped from
[coinmarketcap](https://coinmarketcap.com) :v: and it\'s
[free](https://coinmarketcap.com/faq/) to use. :tada:

## Contributing

Feel free to make a pull request! :octocat:

If you found this useful, I\'d appreciate your consideration in the
below. ✨☕


[PyPI Version]: https://img.shields.io/pypi/v/cryptoCMD.svg
[1]: https://pypi.python.org/pypi/cryptoCMD
[CI Status]: https://github.com/guptarohit/cryptoCMD/actions/workflows/ci.yml/badge.svg
[2]: https://github.com/guptarohit/cryptoCMD/actions/workflows/ci.yml
[License]: https://img.shields.io/pypi/l/cryptoCMD.svg
[3]: https://github.com/guptarohit/cryptoCMD/blob/master/LICENSE
[Downloads]: https://pepy.tech/badge/cryptoCMD
[4]: https://pepy.tech/project/cryptoCMD
[Ruff]: https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json
[5]: https://github.com/astral-sh/ruff
[GitHub Sponsors]: https://img.shields.io/github/sponsors/guptarohit?color=%23FF5733
[6]: https://github.com/sponsors/guptarohit
[![Buy Me A Coffee](https://img.buymeacoffee.com/button-api/?text=Buy%20me%20a%20coffee&emoji=&slug=rohitgupta&button_colour=5F7FFF&font_colour=ffffff&font_family=Lato&outline_colour=000000&coffee_colour=FFDD00)](https://www.buymeacoffee.com/rohitgupta)

17.02.26
Ось результати аналізу та стратегія трансформації для проекту **cryptoCMD**, підготовлені у форматі для копіювання в Notion.

---

# 📑 Звіт AI-консультанта: Проект "cryptoCMD"

Проект **cryptoCMD** — це спеціалізована Python-бібліотека для отримання історичних даних про ціни криптовалют безпосередньо з сайту CoinMarketCap.

## 🧬 Частина 1: "ДНК" Проекту

Логіку коду **cryptoCMD** можна розкласти на такі **атомарні функції**:

*   **Ініціалізація скрепера (Scraper Config):** Налаштування параметрів запиту, включаючи символ монети (наприклад, "XRP"), часові інтервали та, за необхідності, повну назву монети для усунення конфліктів однакових кодів.
*   **Веб-парсинг (Data Ingestion):** Автоматизований збір сирих даних з веб-сторінок CoinMarketCap без використання офіційного API.
*   **Форматування даних (Format Transformation):** Перетворення отриманих даних у різні структури: список списків (raw data), JSON-об'єкти або Pandas DataFrames для аналітики.
*   **Експорт даних (Persistence):** Функція запису зібраної інформації у фізичні CSV-файли з можливістю кастомного іменування.
*   **Обробка часових рядів:** Витягування конкретних колонок даних, таких як ціна відкриття/закриття, максимуми, мінімуми, об’єм торгів та ринкова капіталізація.

### 💎 Головна технічна цінність
Головна цінність проекту полягає в **абстрагуванні складності веб-скрейпінгу**. Він надає розробникам простий програмний інтерфейс (Python API) для безкоштовного отримання історичних ринкових даних, які зазвичай доступні лише через платні API-тарифи.

---

## 🚀 Частина 2: "Трансформація" (Інтеграція з Gemini LLM)

Інтеграція з LLM (наприклад, **Gemini**) через інструменти **GitHub Models** перетворює статичний скрепер на **інтелектуальну аналітичну платформу**.

### Як зміниться функціонал?
1.  **Семантичні запити:** Замість написання коду для вибору дат, користувач зможе запитати: *"Порівняй волатильність Solana та Ripple під час останнього піку ринку"*. Gemini автоматично переведе це в параметри для `CmcScraper`.
2.  **Прогнозний аналіз:** LLM зможе аналізувати отримані `Pandas DataFrame` на предмет патернів та аномалій, генеруючи текстові висновки про стан ринку.
3.  **Автоматична генерація звітів:** Після завантаження CSV-файлу AI миттєво створює резюме з ключовими показниками (Market Cap, Volume) людською мовою.

### Сценарій сервісу (cryptoCMD + Gemini + ID_{$})

Створення сервісу **"Crypto Insights Terminal"** на вашому сайті:
1.  **Користувацький ввід:** Відвідувач сайту запитує: *"Якою була динаміка біткоїна за останні 10 днів?"*.
2.  **Обробка наміру (Gemini):** Через **GitHub Models** Gemini розпізнає символ ("BTC") та часовий інтервал.
3.  **Виконання (ID_{$}):** Ваш Python-скрипт `ID_{$}` отримує параметри від AI та викликає `CmcScraper(coin, start, end)`.
4.  **Аналіз даних:** Отриманий `dataframe` передається назад до Gemini для пошуку трендів.
5.  **Візуалізація (GitHub Spark):** Використовуючи **GitHub Spark**, ви створюєте інтерфейс, де користувач отримує не просто файл, а інтерактивний графік із текстовим поясненням від AI.

---

## 📋 План дій для Notion
| Крок | Дія | Результат |
| :--- | :--- | :--- |
| **1** | Встановлення: `pip install cryptocmd` | Готовий інструмент збору даних |
| **2** | Створення скрипта `ID_{$}` для парсингу JSON | Автоматизація обробки результатів |
| **3** | Підключення Gemini API через **GitHub Models** | Додавання інтелектуального аналізу |
| **4** | Налаштування експорту в CSV для звітів | Формування бази даних для сайту |

---

### 💡 Резюме

**Суть:** **Бібліотека для збору історичних крипто-даних**.

**AI-Роль:** **Інтелектуальна аналітика та семантичний інтерфейс**.

*(Примітка: Пропозиції щодо ШІ-функціоналу та використання GitHub Spark/Models базуються на технічному потенціалі проекту та сучасних інструментах розробки, згаданих у джерелах).*
