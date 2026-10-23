# Nebula Theme for OpenWebUI

A modern, dark-first theme for [OpenWebUI](https://github.com/open-webui/open-webui) featuring glassmorphism, a violet/teal palette, and full customization via CSS custom properties.

![Nebula Theme Preview](preview.png)

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Dark-first** | Optimized for dark mode, beautiful in light mode too |
| **Auto color scheme** | Respects `prefers-color-scheme` automatically |
| **Manual toggle** | Add `[data-theme="light"]` or `[data-theme="dark"]` to `<html>` |
| **Glassmorphism** | `backdrop-filter: blur(16px) saturate(180%)` on surfaces |
| **CSS Variables** | 100% customizable — change colors, radii, fonts in one place |
| **Variable Fonts** | Inter Variable (UI) + JetBrains Mono Variable (code) |
| **Accessible** | WCAG AA contrast, focus rings, reduced motion, high contrast, RTL |
| **Responsive** | Fluid sidebar, breakpoints as variables |
| **Print styles** | Clean output for printing conversations |

## 🚀 Quick Install

### Option 1: Via OpenWebUI UI (Easiest)
1. Open OpenWebUI → **Settings** → **Interface** → **Theme**
2. Click **Import Theme**
3. Paste the contents of `theme.css`
4. Save

### Option 2: Static File Serving (Recommended for VPS)
```bash
# On your VPS
mkdir -p /opt/openwebui/themes/nebula
# Upload theme.css, theme-light.css, manifest.json to this folder
# Add .woff2 fonts to fonts/ (optional but recommended)
```

```nginx
# In your nginx config
location /static/themes/nebula/ {
    alias /opt/openwebui/themes/nebula/;
    expires 1y;
    add_header Cache-Control "public, immutable";
}
```

Then in OpenWebUI → **Settings** → **Interface** → **Custom CSS**:
```css
@import url('/static/themes/nebula/theme.css');
```

### Option 3: Fork OpenWebUI
Copy `theme.css` to `open-webui/src/styles/themes/nebula.css` and add to the theme selector.

## 🎨 Customization (30 seconds)

Create `theme-overrides.css` loaded **after** `theme.css`:

```css
:root {
  --color-accent: #00d4aa;        /* Teal instead of violet */
  --color-accent-hover: #00ffcc;
  --radius-md: 14px;              /* Softer corners */
  --font-sans: 'Geist Var', var(--font-sans);
  --glass-blur: blur(24px) saturate(200%);
}
```

### Key Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `--color-accent` | `#a855f7` | Primary accent (violet) |
| `--color-teal` | `#00d4aa` | Secondary accent |
| `--color-bg` | `#0a0a12` | Main background |
| `--font-sans` | `Inter Variable` | UI font |
| `--font-mono` | `JetBrains Mono Variable` | Code font |
| `--radius-md` | `10px` | Default border radius |
| `--glass-blur` | `blur(16px) saturate(180%)` | Glass effect |
| `--transition-base` | `160ms ease-out` | Animation speed |

## 📦 Fonts (Recommended)

Download variable font `.woff2` files and place in `fonts/`:

- **Inter Variable**: https://github.com/rsms/inter/releases → `Inter-VariableFont.woff2`
- **JetBrains Mono Variable**: https://github.com/JetBrains/JetBrainsMono/releases → `JetBrainsMono-VariableFont.woff2`

The theme references them in `theme.css` and will use them automatically.

## 📁 Structure

```
nebula/
├── theme.css          # Main theme (~450 lines)
├── theme-light.css    # Light mode override (optional)
├── manifest.json      # Theme metadata
├── preview.png        # 1920×1080 screenshot (add your own)
├── README.md          # This file
└── fonts/
    ├── Inter-VariableFont.woff2
    └── JetBrainsMono-VariableFont.woff2
```

## 🔧 Development

```bash
# Clone and edit
git clone https://github.com/xtrem21-source/openwebui-theme-nebula
cd openwebui-theme-nebula

# Test locally: import theme.css in OpenWebUI UI
# Make changes, preview, commit
git add .
git commit -m "feat: adjust accent color"
git push
```

## 📄 License

MIT — free for personal and commercial use.

## 🤝 Contributing

PRs welcome! Open an issue first for significant changes.

---

**Made with 💜 by [xtrem21-source](https://github.com/xtrem21-source)**