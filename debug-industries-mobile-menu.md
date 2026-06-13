# Debug Session: industries-mobile-menu

Status: [OPEN]

## Symptom
- On mobile view, the `Industries` menu does not open.
- `Our Services` and `About` do open.

## Scope
- Primary page observed: `index.html`
- Shared behavior likely affected via `assets/js/main.js` and `assets/js/bootsnav.js`

## Hypotheses
1. The `Industries` top-level click handler is not firing on mobile because Bootsnav intercepts it before the delegated handler runs.
2. The `Industries` dropdown opens, but its inner mega-menu content remains hidden because Bootsnav expects a different mobile structure for `.col-menu` sections.
3. Another handler closes the `Industries` dropdown immediately after open due to event bubbling or outside-click logic.
4. The `Industries` markup differs from `Our Services`/`About` in a way that prevents the intended mobile open state from being applied consistently.
5. A CSS/mobile display rule hides the relevant `Industries` content even after the `on` class and dropdown visibility are applied.

## Evidence Plan
- Instrument top-level dropdown clicks for `Industries`, `Our Services`, and `About`
- Instrument resulting parent/menu class state after click
- Instrument inner mega-menu visibility for `.col-menu` sections
- Reproduce on mobile and compare event/state flow across the three menus

## Fix Criteria
- `Industries` opens on first tap in mobile view
- Inner industry links are visible and tappable
- `Our Services` and `About` continue to behave correctly
