# Visual Itinerary Specification
Purpose: a one-page, phone-friendly picture of the trip for the group text.

When:
- **DRAFT** — as soon as the first itinerary exists (Step 7), with a visible “DRAFT — not final” label. Regenerate after each revision.
- **Final** — after the itinerary is locked (Step 9), with the DRAFT label removed.

Required:
- title, dates, base(s)
- one panel per day: date, destination/base, major activities
- approximate timing when useful
- optional items clearly labeled “Optional”
- paid activities highlighted — color the whole activity line, not just the price marker
- cost legend
- readable on a phone

Cost colors (defaults; use the user's tiers if they set their own):
| Tier | Per person | Highlight | Text-only marker |
|---|---|---|---|
| FREE / INCLUDED | — | None | (none) |
| $ | Under $25 | Light green | 🟢 |
| $$ | $25–$75 | Light orange | 🟠 |
| $$$ | Over $75 | Light red | 🔴 |

## Output format, best available first
### 1. PNG (one page)
If you can run code:
1. Write a self-contained HTML file (inline CSS, no external fonts or images). Put all content in one wrapper element with a **fixed width of 540px** and `box-sizing: border-box`. Use a 15–16px base font.
2. Add a script at the end of the body that records the wrapper's height:
   `<script>document.body.setAttribute('data-h', Math.ceil(document.querySelector('.wrap').getBoundingClientRect().height));</script>`
3. Measure the height with a headless Chrome or Edge (`--dump-dom` prints the page after scripts run):
   `"<browser>" --headless=new --disable-gpu --window-size=540,800 --dump-dom "file:///<path>/itinerary.html"` → read `data-h`.
4. Render the PNG at that height, at 2× scale for sharp text on phones:
   `"<browser>" --headless=new --disable-gpu --hide-scrollbars --force-device-scale-factor=2 --window-size=540,<height> --screenshot="<path>/itinerary.png" "file:///<path>/itinerary.html"`
5. If you can view images, open the PNG and check for clipped edges, cut-off text or empty space; fix and re-render.

Browser locations:
- Windows: `C:\Program Files\Google\Chrome\Application\chrome.exe` or `C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe`
- macOS: `/Applications/Google Chrome.app/Contents/MacOS/Google Chrome`
- Linux: `google-chrome`, `chromium` or `chromium-browser`

Keep the HTML file too; the user can open it if they prefer.

### 2. HTML page
If you can't render a PNG: give the self-contained HTML file (or publish it as a page if your platform supports that). Tell the user they can open it on their phone or screenshot it.

### 3. Text
If you can't produce files: a compact text version using the emoji markers above, short enough to paste into a group text.

## Rules
- Use the current plan; never invent activities or prices.
- Don't mark something paid just because a general admission or pass exists.
- Keep text short.
- Regenerate whenever the itinerary changes.
