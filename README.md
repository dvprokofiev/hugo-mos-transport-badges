# 🚇 Hugo Moscow Transport Badges

A simple, zero-JavaScript Hugo module that lets you easily insert crisp SVG icons for Moscow's metro lines and transport hubs right into your Markdown articles.

Instead of writing custom HTML or dealing with blurry images, just use a shortcode: 
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
     <style>{{ .Content | safeCSS }}</style>
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
* **Metro branches:** `m8a` (Solntsevskaya branch)
* **MCC (Moscow Central Circle):** `mck`
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
