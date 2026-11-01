# PBGC §436 App — Design Contract (v1.0)

**Status:** Governing UI/design specification for this repository. Read before modifying UI, styling, exports or templates. Official agency source governs where this file conflicts with interpretations; record discrepancies for human review. This summary does not replace original files.

## Source of truth (PBGC Book of Job)
1. *PBGC Branding & Editorial Style Guide*, **September 2025**, branding, typography, editorial style, logo, accessibility (relevant pages 7–15, 21 and 24). 
2. *pbgc-logo-guidance.pdf*, logo masters, proportions, format and clear-space.
3. *436 Evaluation (ASTD Updates Nov 2025).docx*, official §436 deliverable: **preserve exact official document layout**, typography, table structures, and section text except explicitly designated data fields.

These sources are in the private PBGC Book of Job; do not commit their full PDFs/DOCX or privileged materials into this public repository. OpenCode cannot assume it has access to the connected ChatGPT/Google Drive materials. Ask the user for authorized local copies where needed.

## Verified PBGC branding rules
- **Official primary web colors:** PBGC blue `#002D72` (Pantone 288 C) and PBGC red `#E4002B` (Pantone 185 C).
- **Supporting palette (secondary):** gray `#81807F`, black `#000000`, light blue gray `#6E93C2`, medium blue `#004B8D`, medium green `#008065`, teal `#00A9A1`, light green `#88B672`. Secondary colors must not dominate the primary brand colors.
- **Documents:** Arial and Garamond are designated typefaces; printed text usually 10–12 pt where the source template does not override. For UI, use accessible local/system font fallback; **never fetch webfonts** at runtime.
- **Logos:** use only agency-approved, unmodified digital artwork; do not redraw, recolor, distort, or rearrange logo components. Preserve aspect ratio. Keep clear space equivalent to the width of the letter “P” in the logo; minimum width 0.625 in. For external use, obtain the approval required by the agency guide. **If approved logo artwork is unavailable, use text-only application identification; never fabricate one.**
- **Accessibility:** follow Section 508 and WCAG 2.2 AA design/test targets. Colors alone must not indicate status.
- **Editorial text:** use plain language, consistent acronyms and dates, and correct “PBGC” agency name usage. Exact official memo template language takes precedence over UI microcopy conventions.

**Source consistency caveat:** The 2025 guide prints some RGB component values that do not numerically match its listed HEX values. For CSS/web, use the published **HEX column** above; flag any use requiring RGB/CMYK for human review rather than silently converting mismatched entries.

## Application-specific UI (not agency document requirements)
- User preference: high-contrast **`#000000` background**; use official agency blue/red in branding elements and restrained accents, but **do not use low-contrast agency-blue text directly on black**; derive accessible tonal variants for links, focus rings and foreground labels. Keep text legible and controls visibly differentiated.
- A guided workflow: Case → Source Evidence → §436(b)/(c)/(d)/(e) Screening → AFTAP Certifications → Presumed/Actual Periods → Restrictions/Exceptions → Preview → Export for Review.
- One main action at a time; visible provenance and “Unknown / Assumed / Supported / Reviewed” statuses. Prioritize keyboard access, responsive layout, review queues, and screen-reader labels.
- No unapproved final-looking output: label draft/unreviewed findings; always show missing evidence and assumption indicators.
- No decorative stock logos, gradients, animations, colored badges or branding that misrepresents the app as an official PBGC-issued product.

## Architecture and asset discipline
- App runs under `file://`, entirely offline; no CDN, remote font, backend, network calls or workstation installation.
- UI CSS tokens and app components should derive from this file. Reuse shared primitives; avoid one-off styling in page components.
- Keep official generated DOCX styling/template fidelity separate from browser UI styling. Never restyle an agency template to match the dark app.
- Record design changes with references and dated version history; screenshot-test with synthetic data at 200% zoom and keyboard only.

## Review gate
Before UI/export merges, confirm: design tokens match verified source, logo rules are respected, typography is readable, official §436 template is unchanged except authorized data slots, the app runs offline, and no sensitive files or PII are committed.
