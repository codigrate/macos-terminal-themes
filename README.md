# Codigrate macOS Terminal Themes

Color themes for the built‑in **macOS Terminal.app**, generated from the
canonical [Codigrate JetBrains themes](https://github.com/codigrate). Like the
[Ghostty themes](https://github.com/codigrate), these are terminal profiles, so
they share the exact same JetBrains‑semantic‑field → ANSI palette mapping — only
the file format differs.

Each theme ships as a `.terminal` profile: an XML property list whose colors are
base64‑encoded, `NSKeyedArchiver`‑archived `NSColor` objects, exactly the form
Terminal writes itself.

## Themes

| Nature | Cities |
|---|---|
| Aurora Borealis | Istanbul |
| Autumn | Miami |
| Everest | Paris |
| Roraima | Rio de Janeiro |
| Sakura | Tallinn |
| Sequoia | Tokyo |

```
nature/<theme>/Codigrate <Name>.terminal
cities/<theme>/Codigrate <Name>.terminal
```

## Install

**From Terminal's UI**

1. Open **Terminal → Settings… → Profiles**.
2. Click the **⋯ (gear)** menu at the bottom of the profile list → **Import…**.
3. Pick a `Codigrate <Name>.terminal` file from this repo.
4. Select the imported profile and click **Default** to make it your default.

**From the command line**

```bash
open "nature/aurora-borealis-theme/Codigrate Aurora Borealis.terminal"
```

This opens a new Terminal window using the profile and adds it to your profile
list. Set it as default from **Settings → Profiles**.

## Regenerating

The themes are derived; do not hand‑edit the `.terminal` files. Re‑run the
generator after the JetBrains source changes:

```bash
node generate-from-jetbrains-themes.js
# optional: custom source / output roots
node generate-from-jetbrains-themes.js /path/to/jetbrains-themes /path/to/output
```

The generator (`generate-from-jetbrains-themes.js`) reads each
`*.theme.json` + editor scheme `*.xml` from the JetBrains source, maps the fixed
semantic fields to ANSI slots, enforces per‑family contrast against the
background, and writes a `.terminal` profile plus a copied `icon.png` per theme.

### ANSI mapping

| ANSI | JetBrains field |
|---|---|
| Red | `DEFAULT_LOCAL_VARIABLE` |
| Green | `DEFAULT_STRING` |
| Yellow | `DEFAULT_METADATA` |
| Blue | `DEFAULT_INSTANCE_FIELD` |
| Magenta | `DEFAULT_KEYWORD` |
| Cyan | `DEFAULT_PARAMETER` |

Bright ANSI colors are slightly brighter siblings of their base color. Black,
bright‑black, white and bright‑white are derived from the background/foreground
pair. Background, foreground, selection and cursor come from the editor scheme
with JSON palette fallbacks.

## License

See [LICENSE](LICENSE).

For the color theory behind the palettes: https://codigrate.com
