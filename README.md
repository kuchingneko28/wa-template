# Template WhatsApp Generator

A tiny, dependency‑free web app to generate consistent WhatsApp report messages from predefined templates. Built with **HTML + CSS + JS** (no framework) and styled with a Catppuccin‑inspired palette.

## Features

- Three templates: Unit Banjarmasin Masuk, Patroli, Loker (Inventaris Security)
- Date → day auto‑mapping; date defaults to **today**
- 24‑hour time input with smart normalization (e.g., `2000` → `20:00`, `745` → `07:45`), capped at `HH:MM`
- Auto greeting (Pagi/Siang/Malam) based on time
- `Nopol` auto‑uppercase
- Copy and “Open in WhatsApp”; both disabled when output is empty
- Toast validation on **Generate** only

## Files

```
root/
├─ index.html   # App markup + logic (organized in a small App namespace)
└─ css/
   └─ style.css # Theme + components (inputs, card, toast, etc.)
```

## Usage

1. Open `index.html` in a browser.
2. Pilih _Template_ → isi field (Tanggal/Jam/Nopol/Vendor) → **Generate**.
3. **Copy** hasil atau **Buka di WhatsApp**.

## How it works (quick)

- **Templates** are defined in an array with their fields and a `render()` that returns the final text.
- **Date** is parsed locally to avoid timezone shifts; **day name** is derived automatically.
- **Time** accepts `HH:MM` or compact digits (`2000`, `745`) and is normalized to `HH:MM`.
- **WhatsApp** button tries `navigator.share` → `whatsapp://send` → `wa.me` as fallback.

## Customize

- Edit the `templates` array in `index.html` to add/change fields and output.
- Adjust greeting thresholds in `greetByHour()`.
- Edit vendor options in `<datalist id="vendor-list">`.
- Change timezone label (`WITA`) directly in template strings.

## Troubleshooting

- 🇮🇩 flag missing in preview: use an emoji‑capable font for the textarea (see `style.css`).
- Flag missing via WA button: app uses share/app‑scheme first to preserve emoji; `wa.me` is a fallback.
- Colons not perfectly aligned: WhatsApp uses proportional fonts; use a code block if you need fixed‑width.

## License

MIT (or your preference).
