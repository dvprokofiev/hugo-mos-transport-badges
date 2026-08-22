# 🚇 Иконки Московского Транспорта для Hugo

Простой Hugo-модуль без JavaScript, который позволяет легко вставлять четкие SVG-иконки линий московского метро и диаметров прямо в Markdown-статьи Hugo.

Просто используйте шорткод: 
`Пересадка на {{< mos-transport "m5" >}} Кольцевую линию.`

## 📦 Установка

1. **Инициализируйте ваш Hugo-сайт как модуль** (если еще не сделали этого):
   ```bash
   hugo mod init example.com/my-site
   ```

2. **Добавьте этот модуль в конфигурацию** (`hugo.toml`):
   ```toml
   [module]
     [[module.imports]]
       path = "github.com/dvprokofiev/hugo-mos-transport-badges"
   ```

3. **Подключите стили**
   Чтобы иконки красиво выравнивались по тексту, добавьте этот код в `<head>` вашего сайта (обычно это файл `layouts/partials/head.html`):
   ```html
   {{ $css := resources.Get "mos-transport/mos-transport.css" }}
   {{ with $css }}
     <link rel="stylesheet" href="{{ .RelPermalink }}">
   {{ end }}
   ```

4. **Загрузите модуль**
   ```bash
   hugo mod get -u
   ```

## ✍️ Использование

Просто используйте шорткод `mos-transport` в любом Markdown-файле, к примеру:

```markdown
Едем по {{< mos-transport "m1" >}} до Комсомольской,
пересадка на {{< mos-transport "m5" >}}.

Затем по {{< mos-transport "d2" >}} до Нахабино.
```

### Какие линии поддерживаются?

В качестве ID в шорткоде можно использовать:

* **Линии метро:** от `m1` до `m12`, а также `m15` и `m16`. 
* **Ветки метро:** `m4a` (Филевская), `m8a` (Солнцевская)
* **Монорельс:** `m13`
* **МЦК (Московское центральное кольцо):** `mck` или `m14`
* **МЦД (Московские центральные диаметры):** `d1`, `d2`, `d3`, `d4`, `d5`

### Как использовать в шаблонах сайта (вместо Markdown)?

Если вы верстаете страницу (например, шапку сайта) и хотите вставить иконку напрямую из `.html` шаблона, используйте partial:

```html
<!-- Внутри HTML шаблона, например, single.html -->
{{ partial "mos-transport/icon.html" (dict "id" "m1") }}
```

## 📜 Авторы и Лицензия

* SVG иконки метро и МЦД взяты с [Wikimedia Commons](https://commons.wikimedia.org/wiki/Category:Line_numbers_of_Moscow_Metro) и являются общественным достоянием.
* Код модуля (шорткоды, шаблоны и CSS) распространяется по лицензии [MIT License](LICENSE).
* Код по большому счету написан Google Antigravity.

---

# 🚇 Moscow Transport Icons for Hugo

A simple, zero-JavaScript Hugo module that lets you easily insert crisp SVG icons for Moscow's metro lines and transport hubs right into Hugo Markdown articles.

Just use a shortcode: 
`Transfer to {{< mos-transport "m5" >}} Koltsevaya line.`

## 📦 How to install

1. **Initialize your Hugo site as a module** (if you haven't already):
   ```bash
   hugo mod init example.com/my-site
   ```

2. **Add this module to your config** (`hugo.toml`):
   ```toml
   [module]
     [[module.imports]]
       path = "github.com/dvprokofiev/hugo-mos-transport-badges"
   ```

3. **Include the styling**
   To make the badges align nicely with your text, add this snippet to your site's `<head>` (usually found in `layouts/partials/head.html`):
   ```html
   {{ $css := resources.Get "mos-transport/mos-transport.css" }}
   {{ with $css }}
     <link rel="stylesheet" href="{{ .RelPermalink }}">
   {{ end }}
   ```

4. **Pull the module**
   ```bash
   hugo mod get -u
   ```

## ✍️ How to use

Just use the `mos-transport` shortcode in any of your Markdown files!

```markdown
Take {{< mos-transport "m1" >}} to Komsomolskaya station,
then transfer to {{< mos-transport "m5" >}}.

If you prefer overground, you can use the new {{< mos-transport "d2" >}} diameter.
```

### What lines are supported?

You can use the following IDs in your shortcode:

* **Metro lines:** `m1` through `m12`, plus `m15` and `m16`. 
* **Metro branches:** `m4a` (Filyovskaya branch), `m8a` (Solntsevskaya branch)
* **Monorail:** `m13`
* **MCC (Moscow Central Circle):** `mck` or `m14`
* **MCD (Moscow Central Diameters):** `d1`, `d2`, `d3`, `d4`, `d5`

### Need to use it inside a layout instead of Markdown?

If you're building a custom page layout (like a header or a station directory) and want to call the icon directly from your `.html` template, you can use the underlying partial:

```html
<!-- Inside a layout file, e.g., single.html -->
{{ partial "mos-transport/icon.html" (dict "id" "m1") }}
```

## 📜 Credits and License

* The SVG icons for the Metro and MCD lines are public domain assets sourced from [Wikimedia Commons](https://commons.wikimedia.org/wiki/Category:Line_numbers_of_Moscow_Metro).
* The module code (shortcodes, templates, and CSS) is released under the [MIT License](LICENSE).
* Code was written by Google Antigravity
