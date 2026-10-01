# Практическая работа 2 — ТРПО

Адаптивный каталог учебных материалов на HTML и SCSS.

**Студент:** Юшин Максим  
**Группа:** ЭПБО-01-25

## Результат

Одностраничный каталог с:

- разметкой (шапка, фильтры, сетка карточек, информационный блок, подвал);
- минимум 12 карточками из `catalog.csv`;
- стилями на SCSS (переменные, partial-файлы, mixin, функция);
- адаптивом: фильтры слева на широком экране, сверху на узком;
- двумя breakpoint (768px и 480px).

## Технологии

- HTML
- SCSS (Sass)

## Запуск

1. Откройте папку проекта в VS Code.
2. Установите зависимости:

```bash
npm install
```

Если PowerShell ругается на скрипты, используйте:

```bash
npm.cmd install
```

3. Соберите CSS из SCSS:

```bash
npm run sass
```

или

```bash
npm.cmd run sass
```

4. Откройте `index.html` в браузере или через Live Server.

### Режим наблюдения за SCSS

При правках стилей удобно держать сборку включённой:

```bash
npm run sass:watch
```

или

```bash
npm.cmd run sass:watch
```

## Структура проекта

- `index.html` — разметка каталога
- `scss/` — исходные SCSS-файлы
- `css/styles.css` — скомпилированный CSS
- `data/` — копии данных
- `dataset/` — исходный dataset задания
- `images/` — картинки товаров
- `package.json` — команды сборки Sass
- `.gitignore` — исключает `node_modules` и служебные файлы

### SCSS-файлы

- `scss/_variables.scss` — цвета и размеры из `theme.json`, функция `spacer`
- `scss/_mixins.scss` — mixin `container` и `panel`
- `scss/_base.scss` — базовые стили страницы
- `scss/_layout.scss` — шапка, сетка, подвал, media queries
- `scss/components/_card.scss` — карточка
- `scss/components/_button.scss` — кнопка
- `scss/components/_filter.scss` — фильтры
- `scss/styles.scss` — главный файл, подключает остальные

## Как использованы данные dataset

- `catalog.csv` — названия, категории, цены и рейтинги карточек
- `theme.json` — цвета, радиус и отступы (перенесены в SCSS-переменные)
- `assets/product-01.svg`, `product-02.svg`, `product-03.svg` — изображения карточек

## SCSS: переменные, partials и mixin

### Чем SCSS-переменная отличается от CSS custom property

- **SCSS-переменная** (`$accent`) живёт только на этапе сборки. После `npm run sass` в CSS остаётся уже готовое значение, например `#315efb`.
- **CSS custom property** (`--accent`) хранится в браузере и может меняться на лету. В этой работе используются SCSS-переменные из `theme.json`.

### Зачем нужны partial-файлы

Файлы с подчёркиванием (`_variables.scss`, `_card.scss` и т.д.) — части стилей. Их подключает главный `styles.scss`. Так проще искать код: переменные отдельно, карточка отдельно, раскладка отдельно.

### Где применён mixin

- `container` — в `.page` (`_layout.scss`)
- `panel` — в `.info`, `.filters`, `.card`

Функция `spacer($n)` объявлена в `_variables.scss` и используется для отступов (например `spacer(1.5)` = `$space * 1.5`).

## Что проверить вручную

- на ширине около 1440px фильтры слева, карточки сеткой;
- на 768px фильтры над каталогом;
- на 375px карточки в одну колонку;
- после изменения `$accent` и `npm run sass` меняется цвет кнопки и категории.
