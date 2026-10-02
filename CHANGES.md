# order-form-dual-signature: OLD → NEW

The new version follows the Document Crunch Order Form Design Standard v1.0. It uses the Appendix A reference template, with the Appendix B dual signature block swapped in, because the old form is countersigned by Document Crunch.

- `OLD_2026-10-02.html`: the original template, kept as it was.
- `NEW.html`: paste this into Subskribe using **Open in Code Editor**, with Full HTML off. Never use the Edit builder, because it overwrites custom HTML.

## Changes

| Block | Old | New (SOP section) |
|---|---|---|
| Style | None | Switzer fonts, draft watermark, page-break rules (3.1) |
| Header | Showed `tenantEmail` (prakash@subskribe.com). Logo was 100×50. No order date. | Shows `orderOwner` instead of the email. Logo is 100×100. Adds Order Date, Expiration Date, Bill To CC (3.2) |
| Draft watermark | `<h1>` inside the header cell | Fixed overlay, hidden in doc output (3.2) |
| Customer info | Always printed "City," even when there was no city | City and its comma only print when set (3.3) |
| Contract terms | 3×2 grid | One row of six columns (3.4) |
| Rate table | 7 columns, including UoM, List and Discount | 4 columns: Plan Name, Quantity, Annual Total, Total. Adds the plan description (3.5) |
| Rate table bug | `{{#value}}` sat inside `<tr>`, which put every line item on a single row | `{{#value}}` now wraps the `<tr>`, so each item gets its own row |
| Totals | Grand Total came before the year totals | Year totals come first, then Grand Total (3.5) |
| T&C line | None | Trimble Offering Terms v4.0 link (3.6) |
| Order terms | Not wrapped | Wrapped in `.table-section`. Adds the Customer Parties field (3.7) |
| Signature | Unfixed widths and a stray `&nbsp` row | Fixed 12/33/10/12/33 layout. E-sign anchors are unchanged (Appendix B) |

## Subskribe configuration (SOP 6.2 / Appendix C)

- `primaryColor`: `#5350ed`
- `secondaryColor`: `#daebfd`
- `lineItemColumns`: `PLAN_NAME, QUANTITY, YEARLY_AMOUNT`
- `isFullHtml`: `false`

## After you paste it

1. Preview it against a real order (template → Select order).
2. Re-save any draft orders that use this template (Edit Order → Save Draft). Stored PDFs only refresh when an order is saved again.
