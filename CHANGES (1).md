# order-form-without-discount: OLD → NEW

The new version follows the Document Crunch Order Form Design Standard v1.0. It uses the Appendix A reference template with the §7.2 "Entitlement summary" variant: the "Customer has up to…" line under the rate table. It has a customer-only signature (§3.8).

- `OLD_2026-10-02.html`: the original template, kept as it was.
- `NEW.html`: paste this into Subskribe using **Open in Code Editor**, with Full HTML off.

## Kept from the old form

- `{{#sortByCustomField}}rank{{/sortByCustomField}}`, which sorts line items by the plan's rank field.
- The entitlement logic for uploads, Projects/Playbooks and CrunchAI checklists. It is unchanged: same `templateState` sums, same custom fields.
- The line "By executing below, this Order Form and Agreement has been executed…"

## Changes

| Block | Old | New (SOP section) |
|---|---|---|
| Style | No `strong`/`b` or signature-table rules | Full §3.1 style block |
| Header | "Expiration Date:" printed even when empty | Prints only when set (§3.2) |
| Customer info | "Bill to" / "Ship to" hard-coded | Switches to Reseller / Customer when there is a reseller (§3.3) |
| Rate table bug | `{{#value}}` sat inside `<tr>`, which put every line item on a single row | Each line item gets its own row (§3.5) |
| Plan description | Always printed, which left an empty line when blank | Prints only when set (§3.5) |
| Entitlement line | Spanned 3 of the 4 columns. Printed an empty row when there was no entitlement. Its calculation sat in an invalid spot inside `<table>` | Spans all 4 columns and is hidden when empty. The calculation runs before the table |
| Totals | Per ramp period (`rampedItemDateGroups`) | Per billing year (`invoicePreviews`), then Grand Total (§3.5) |
| T&C line | Plain `<div>` | `.table-section` wrapper (§3.6) |
| Signature | 40%-wide table with stray `&nbsp` rows. The "By executing…" text sat inside `<table>` | Fixed 12/38/50 layout (§3.8). The "By executing…" text now sits directly above the signature table |

## ⚠ Check before you go live

**Totals:** the old form showed one total per *ramp interval*. The SOP shows one total per *billing year*. For non-ramped orders the two match. For a ramped deal where prices change mid-year, the subtotals will differ. Preview a ramped order before you save the template.

## Subskribe configuration (SOP 6.2 / Appendix C)

- `primaryColor`: `#5350ed`
- `secondaryColor`: `#daebfd`
- `lineItemColumns`: `PLAN_NAME, QUANTITY, YEARLY_AMOUNT`
- `isFullHtml`: `false`

After you paste it, preview it against a real order. Then re-save any draft orders that use this template.
