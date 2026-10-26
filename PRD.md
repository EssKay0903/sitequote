# Product Requirements Document (PRD)

## Product
**SiteQuote — Building Materials Quote Comparison**

## 1. Problem
Site managers at small and mid-size contractors collect supplier quotes over calls and messaging apps. Quotes can use different units and may include separate freight charges. Comparing sticker prices manually can be slow and error-prone; the cheapest quoted price may not be the cheapest delivered option.

## 2. Users
- **Primary:** Site manager or site engineer purchasing materials for a construction site.
- **Secondary:** Purchase head or owner who reviews and approves the decision.

## 3. Goals
- Show comparable normalized prices and total landed cost for three supplier quotes.
- Make the recommendation explainable in a shareable message.
- Support a broad range of building materials, not only cement and steel.
- Make the common workflow usable in under three minutes.

## 4. Non-goals for v1
- Negotiation chat or automatic quote capture from WhatsApp.
- Supplier ratings.
- Saved comparison history or shared multi-user data.
- More than three supplier quotes per comparison.
- Automatic retrieval of real supplier prices.

## 5. User flow — maximum three screens

### Screen 1: Requirements and quotes
The user selects a category, material, specification, comparison unit, and required quantity. The selected material and required quantity apply to all three suppliers.

Each supplier quote includes:
- Supplier name.
- Quoted price and price unit.
- Package size, weight, volume, length, or coverage where needed.
- Freight amount and freight method (fixed total, per comparison unit, or percentage of material cost).
- Optional additional charges.
- Delivery time in days.
- Available quantity and its unit.
- Optional notes.

**Credit period / credit days are intentionally excluded from this version.**

### Screen 2: Comparison
Show the three suppliers side by side, including:
- Quoted price and normalized unit price.
- Material subtotal.
- Freight and additional charges.
- Total landed cost and landed cost per comparison unit.
- Available quantity and delivery time.
- Flags for incomplete quotes and insufficient supply.

Highlight the cheapest supplier capable of fulfilling the complete order and separately identify the fastest viable supplier.

### Screen 3: Decision summary
Generate a shareable message that includes:
- Material and specification.
- Required quantity and comparison unit.
- Recommended supplier.
- Total landed cost and landed cost per unit.
- Delivery time.
- Comparison with other viable suppliers.
- Fastest alternative, if different.
- Quotes not considered and the reasons.
- A working **Copy summary** action.

Credit terms must not appear in forms, comparisons, calculations, recommendation logic, or summaries.

## 6. Material catalogue
Provide searchable categories and allow an **Other / Custom material** option.

Initial categories and representative materials:
- **Cement and binders:** OPC, PPC, PSC, white cement, lime, fly ash, tile adhesive.
- **Concrete:** ready-mix concrete by grade.
- **Steel and metals:** TMT bars, structural steel, binding wire, plates, beams, angles and channels.
- **Sand and aggregates:** river sand, M-sand, stone aggregates and gravel.
- **Bricks and blocks:** clay bricks, fly-ash bricks, AAC blocks.
- **Tiles and flooring:** vitrified tiles, ceramic tiles, tile adhesive.
- **Plumbing and electrical:** PVC pipes, copper wire and related supplies.
- **Paints and finishes:** interior emulsion, wall putty and coatings.
- **Timber and boards:** plywood and related products.
- Extendable catalogue for waterproofing, roofing, doors and windows, insulation, hardware, safety supplies and other construction materials.

For custom materials, the user can enter a name, specification, comparison unit, package name and units per package.

## 7. Units and normalization
Use a suitable canonical comparison unit for the material; do not force every material into tonnes.

Examples:
- Cement, steel and suitable bulk materials: kg or tonnes.
- Paint and liquid products: litres.
- Powder products: kg or tonnes.
- Bricks and fittings: pieces.
- Pipes and cables: metres.
- Tiles and flooring: square feet or square metres.
- Ready-mix concrete: cubic metres.
- Packaged products: convert only when package contents or coverage are known.

Core conversions:
- 1 tonne = 1,000 kg.
- A 50 kg cement bag = 0.05 tonnes.
- 20 bags of 50 kg = 1 tonne.
- Convert cubic metres to tonnes only when an appropriate density is known.
- Convert boxes to area only when coverage per box is known.
- Convert pieces to weight only when per-piece weight is known.

Do not silently assume density, package size, coverage or piece weight. Mark quotes as not comparable or request the missing conversion data.

## 8. Landed-cost calculations
- Normalize each supplier's price to the shared comparison unit.
- Calculate material subtotal, freight, explicitly entered additional charges, total landed cost and landed cost per unit.
- Freight must be interpreted using its selected method and must not be double-counted.
- Clearly distinguish required quantity from available quantity.
- A supplier unable to provide the full order is not eligible to be the sole-supplier recommendation.
- Do not treat missing values as zero or divide by zero.
- Do not include unknown taxes or charges as if they were confirmed.

Formula:

`Total landed cost = material subtotal + freight + explicitly entered additional charges`

`Landed cost per comparison unit = total landed cost / comparable delivered quantity`

## 9. Recommendation rules
- Default to the lowest total landed cost among suppliers with complete, valid quotes and sufficient stock.
- Show the fastest viable supplier separately.
- Explain the cost and delivery trade-off.
- If no supplier can fulfil the order, explain that no full-order supplier is viable. Do not claim to optimize a split order unless that logic has actually been implemented.

## 10. Edge cases and validation
- Required quantity must be greater than zero.
- Supplier names are required.
- Reject negative prices, freight, charges, delivery days and available quantities.
- Require essential package conversion information.
- Handle quotes entered in different supported units.
- Flag partial supply and zero available stock.
- Prevent division by zero.
- Clearly explain why a quote is excluded.
- Label sample values as illustrative in project documentation; never imply they are live supplier prices.

## 11. Success metrics
- Target decision time: under three minutes.
- Correct unit conversions and landed-cost arithmetic for supported, valid inputs.
- Recommendation can be copied and understood by an approver in one message.

## 12. Future possibilities
- Saved comparison history.
- Pasted WhatsApp quote parsing.
- Support for more than three suppliers.
- Supplier integrations, if validated as useful.
