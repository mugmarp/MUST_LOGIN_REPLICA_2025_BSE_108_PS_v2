# MUST Application Portal — UI/UX Redesign

**SWE2106 Internet Technology and Web Design**
Mugendawala Mark Paul · 2025/BSE/108/PS
Mbarara University of Science and Technology

Redesign of two screens from the MUST Online Application Portal: the **Login** screen and the **Account Creation** screen. Content, field names and wording are kept as they are in the live system; the visual design is new.

---

## What I changed, and why

### 1. Layout — from one centred card to a two-part screen

The current portal centres a single card on a purple gradient. On a wide monitor that leaves a lot of empty space and gives the screen no hierarchy.

The redesign splits the viewport into two columns:

- **Left — identity.** The crest, the university name, the portal name, a one-line explanation and three short reassurance points.
- **Right — the task.** The form, in a card.

This puts branding and the actual job in separate places instead of stacking them, and it is the pattern most people already recognise from modern login screens. Below 900px the two columns stack and the identity block becomes a compact header, so the crest stays visible without competing with the inputs.

### 2. Colour — taken from the crest, not invented

The palette is sampled from the university crest itself rather than chosen at random:

| Token | Value | Where it is used |
| --- | --- | --- |
| Crest blue | `#2e3192` | Buttons, links, field focus |
| Crest blue (hover) | `#23266f` | Button hover |
| Deep indigo | `#1f2260` | Identity panel background |
| Crest gold | `#ffd543` | Portal label, accents, icons |
| Ink | `#1c1e3a` | Body text |
| Muted indigo | `#5a5d8a` | Helper text, secondary text |
| Panel | `#f7f8fd` | Page background |

The old portal's purple radial gradient is replaced with two soft radial washes in indigo and gold, which gives the panel depth without needing a background image.

Every foreground/background pair was checked against the WCAG AA minimum of **4.5:1** for normal text before it was used. The weakest pair in the stylesheet is **5.88:1**, so nothing falls below the threshold.

### 3. Form fields — real labels instead of placeholders

The live portal identifies its fields only with placeholder text. That text disappears the moment someone starts typing, and it gives screen readers nothing to announce.

The redesign uses a real `<label>` for every field, tied to its input with `for`/`id`, with the placeholder kept only as an example. Required fields carry a visible asterisk. Helper text that the live system shows in a pop-up — *"Use an active phone number to receive notifications"* — sits directly under the field it describes.

### 4. A bug in the live system, fixed

The live login form renders the password field as `type="text"`, so the password is visible on screen while it is typed. The redesign uses `type="password"`.

### 5. Typography and spacing

A system font stack (no webfont download), a 16px base, and 1.6 line height. Spacing comes from a small set of tokens so the gaps between fields, the card padding and the section spacing stay consistent across both pages.

### 6. Responsive

- **Below 900px** — one column; the identity block becomes a compact header.
- **Below 520px** — Surname and Other Names stack instead of sitting side by side, since two narrow columns are too cramped to type into comfortably on a phone.

### 7. Accessibility

- Visible `:focus-visible` outline on every interactive element, in amber over the dark panel where an indigo ring would disappear.
- Decorative icons marked `aria-hidden`.
- No information is carried by colour alone — required fields are marked with an asterisk as well as colour.
- Motion is removed for users who have asked for reduced motion.

---

## What is deliberately not included

The live portal has a chat assistant (MISA), a maintenance banner, and modals for changing and recovering a password. Those are not part of the two screens being redesigned, so they are left out rather than rebuilt. The form `action` attributes point at `#` as placeholders — this is a front-end redesign only, with no backend behind it.

## Files

| File | Purpose |
| --- | --- |
| `login.html` | Sign-in screen |
| `signup.html` | Account creation screen |
| `styles.css` | All styling, shared by both pages |
| `media/campus_logo.png` | University crest |
| `screenshots/` | Desktop and mobile captures of both screens |
