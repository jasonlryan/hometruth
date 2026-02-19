# HomeTruth brand reference

Single source of truth for this site. Aligned with the [hometruth-styleguide](https://github.com/jasonlryan/hometruth-styleguide) repo and the **HomeTruth Development Style Guide 14.08** PDF in that repo.

## Typography

- **Font:** Gill Sans (Light 300, Regular 400, Bold 700)
- **Fallbacks:** `'Gill Sans', 'Gill Sans MT', -apple-system, 'Helvetica Neue', Arial, sans-serif`
- **Scale (classes in `index.html`):** `.type-hero`, `.type-h1` … `.type-h4`, `.type-body-lg`, `.type-body`, `.type-caption`

## Colors (CSS variables in `index.html`)

| Token | Hex | Use |
|-------|-----|-----|
| **Primary** | | |
| `--ht-orange` | `#E8651A` | Primary brand, CTAs, highlights |
| `--ht-orange-light` | `#F28C4E` | Hover / light variant |
| `--ht-cyan` | `#00B4D8` | Truth wordmark, links, primary accent |
| `--ht-cyan-light` | `#48D1E8` | Hover / light variant |
| `--ht-purple` | `#8B3FA0` | Secondary brand |
| `--ht-purple-light` | `#A966BF` | Hover / light variant |
| **Accent** | | |
| `--ht-green` | `#43B02A` | Success, positive accent |
| `--ht-green-light` | `#6BC955` | Hover / light variant |
| **Neutrals** | | |
| `--ht-black` | `#1A1A1A` | Text |
| `--ht-dark` | `#0F1620` | Page/section background |
| `--ht-mid-grey` | `#8C8C8C` | Secondary text |
| `--ht-light-grey` | `#C4C4C4` | Borders, muted |
| `--ht-white` | `#FFFFFF` | Body text on dark |
| **Aliases (styleguide parity)** | | |
| `--ht-primary` | same as `--ht-cyan` | |
| `--ht-secondary` | same as `--ht-purple` | |

## Brand graduation

- **Gradient (diagonal):** `--grad-brand` — Orange → Purple → Cyan, 135deg
- **Gradient (horizontal):** `--grad-brand-h` — same colours, 90deg  
Use for top bar, underlines, and gradient text.

## Section spacing (from styleguide)

- `.section-y` — `py-16` / `lg:py-24`
- `.section-y-sm` — `py-12` / `lg:py-16`

## Logo & icon

- **Icon:** `images/hometruth-icon.svg` (building-blocks mark)
- **Wordmark:** “Home” + “Truth” (`.truth` in cyan)
- **Full logo:** icon + wordmark as in nav and hero

## External reference

- **Styleguide repo:** https://github.com/jasonlryan/hometruth-styleguide  
- **Full style guide (PDF):** [brand/HomeTruth Development Style Guide 14.08.pdf](https://github.com/jasonlryan/hometruth-styleguide/blob/main/brand/HomeTruth%20Development%20Style%20Guide%2014.08.pdf)  
- **Copy / layout spec:** [brand/hometruth-homepage-copy-spec.html](https://github.com/jasonlryan/hometruth-styleguide/blob/main/brand/hometruth-homepage-copy-spec.html)
