# Starter Project Spec

**Workshop:** From Figma to Function · Design to Live Interface with Claude Code
**Purpose:** the pre-prepared Figma file every participant builds from, so nobody spends the evening deciding what to make.
**Owner:** Hooman · build in Figma before the event, share as a duplicatable community file.

---

## 1. The product

**Signal** · a support inbox for a small team. One screen.

It was chosen on four constraints, not on taste:

1. **Nobody needs briefing.** Every designer in the room already understands an inbox. Zero minutes lost to the domain.
2. **It is variant-rich.** Four status values force real component variants rather than four copies.
3. **It is state-rich.** Empty, loading and error are natural here, not contrived. That is rung three.
4. **It survives a change request.** Density and accent are the two things a client changes on a screen like this, which makes rung four honest rather than staged.

Deliberately **not** a landing page (no component reuse), **not** a settings panel (no states worth building), **not** an analytics dashboard (charts eat the whole evening).

---

## 2. Naming convention

The convention is the lesson. Fix it before you draw anything.

| Layer type | Pattern | Example |
|---|---|---|
| Component | `Category/Name` | `Card/Metric` |
| Variant | `Category/Name/Variant` | `Badge/Status/Open` |
| Frame | `Screen/Context` | `Inbox/Desktop` |
| Token, color | `color/role/level` | `color/surface/raised` |
| Token, space | `space/N` | `space/16` |
| Token, type | `type/role` | `type/body/default` |

Rule for the file: **if a name does not say what the thing is for, it is wrong.** No `Frame 427`, no `Rectangle 12 copy`, with the single planted exception in §6.

---

## 3. Tokens

Build these as Figma variables, not styles, so the token path is real.

**Color**

| Token | Value | Role |
|---|---|---|
| `color/surface/base` | `#FAFAFA` | Page background |
| `color/surface/raised` | `#FFFFFF` | Cards, rows |
| `color/surface/sunken` | `#F2F1EE` | Filter bar, skeletons |
| `color/ink/primary` | `#1E1E2E` | Headings, primary text |
| `color/ink/secondary` | `#4A4A52` | Body, metadata |
| `color/ink/muted` | `#9A988F` | Timestamps, counts |
| `color/border/default` | `#E8E6E0` | All dividers and card borders |
| `color/accent/default` | `#514EA8` | Primary action, selection |
| `color/accent/hover` | `#413E93` | Primary action hover |
| `color/status/open` | `#514EA8` | Badge, open |
| `color/status/pending` | `#7A6A00` | Badge, pending |
| `color/status/resolved` | `#1F7A45` | Badge, resolved |
| `color/status/escalated` | `#CC112C` | Badge, escalated |
| `color/focus/ring` | `#514EA8` | Focus outline, 2px |

**Space** · `space/4`, `space/8`, `space/12`, `space/16`, `space/24`, `space/32`, `space/48`
Nothing outside the scale. This is what pass one of the critique tests against.

**Radius** · `radius/none 0`, `radius/sm 6`, `radius/md 12`, `radius/pill 999`

**Type** · five steps only

| Token | Size / line height / weight |
|---|---|
| `type/display` | 28 / 34 / 600 |
| `type/heading` | 20 / 26 / 600 |
| `type/body/strong` | 15 / 22 / 600 |
| `type/body/default` | 15 / 22 / 400 |
| `type/caption` | 13 / 18 / 400 |

**Density** · `density/row-padding` = `space/16`
One token, one job. It is half of the rung-four change request, so give it its own name now.

---

## 4. Components

Nine components. Build every variant. Anything missing here gets invented by the model, which is the point of pass four.

| Component | Variants | States to draw |
|---|---|---|
| `Button/Primary` | default, secondary, ghost | default, hover, focus, disabled |
| `Badge/Status` | open, pending, resolved, escalated | default only |
| `Input/Search` | default | default, focus, filled |
| `Chip/Filter` | default | unselected, selected |
| `Avatar` | sm, md | default |
| `Card/Metric` | positive, neutral, negative | default |
| `Row/Ticket` | default | default, unread, selected, hover |
| `EmptyState` | default | default |
| `Skeleton/Row` | default | default |

`Row/Ticket` composes `Avatar`, `Badge/Status` and `type/caption`. That composition is what rung two proves: the model should reference the badge component, not rebuild a coloured pill.

---

## 5. Frames

| Frame | Size | Contents |
|---|---|---|
| `Inbox/Desktop` | 1440 × 900 | Header with search, filter chip row, metric row of three `Card/Metric`, list of eight `Row/Ticket` |
| `Inbox/Mobile` | 390 × 844 | Same screen, stacked. Metric row scrolls horizontally, filters collapse to a single control |
| `States/Empty` | 1440 × 900 | `EmptyState` in place of the list |
| `States/Loading` | 1440 × 900 | Six `Skeleton/Row` in place of the list |
| `States/Error` | 1440 × 900 | Error banner above a retained, dimmed list |
| `Change Request` | 1440 × 900 | The rung-four target. See §7 |

---

## 6. The two planted faults

Both are deliberate. Both are documented here and nowhere in the participant file.

**Trap one · an unnamed component.** The metric row's trend indicator is a real component named `Group 12`. It renders correctly, so nothing looks wrong. In the build it becomes a component nobody can reference, extend or find again. Surfaces in critique pass two.

**Trap two · a hardcoded value.** The third `Card/Metric` uses a raw `#2E7D32` fill instead of `color/status/resolved`. It looks identical to the token value at a glance. It survives the rung-four accent change untouched while every other card follows, which makes it visible only after the change, not before. Surfaces in critique pass one, and again in rung four.

Do not tell the room the traps exist until at least one person has found one.

---

## 7. The change request

The rung-four target frame. Exactly two tokens move, and nothing else.

| Token | From | To |
|---|---|---|
| `color/accent/default` | `#514EA8` | `#1F7A45` |
| `density/row-padding` | `space/16` | `space/8` |

Pass condition: the participant changes two values and the whole screen follows.
Fail condition, and the better lesson: they have to edit components, which means the system leaked. Trap two guarantees at least one visible failure for everyone in the room, so nobody leaves thinking their build was clean.

---

## 8. The build ladder, mapped to this file

| Rung | Build | Proves |
|---|---|---|
| 1 | `Button/Primary` and its variants | The token path is real, not coincidence |
| 2 | Metric row from `Card/Metric` | Reuse by reference, not by cloning |
| 3 | `Inbox/Desktop` plus all three state frames | The states nobody gets for free |
| 4 | `Change Request` | Whether it is a system or a tidy screenshot |

---

## 9. Build checklist before the event

- [ ] Variables created as variables, not styles, with the exact names in §3
- [ ] All nine components built with every variant in §4
- [ ] `Row/Ticket` composes the real `Avatar` and `Badge/Status` components
- [ ] Six frames drawn, all named per §2
- [ ] Trap one in place: the trend indicator left as `Group 12`
- [ ] Trap two in place: third metric card on raw `#2E7D32`
- [ ] Eight tickets written with realistic, uneven content lengths, so critique pass three has something to bite on
- [ ] One ticket subject deliberately long enough to test overflow
- [ ] File set to duplicatable, link tested in a private window
- [ ] A clean reference copy kept separately, in case someone corrupts theirs mid-build
