---
name: family-trip-planner
description: "Trip planning assistant for the family trip to Cambodia, Vietnam, and Thailand (March-April 2026). Use this skill whenever the user asks about modifying the trip itinerary, updating dates, changing destinations, adding attractions, adjusting budget, or any question related to the Southeast Asia family trip. Also trigger when user mentions: trip, טיול, vacation, itinerary, מסלול, flight, טיסה, hotel, מלון, Cambodia, Vietnam, Thailand, Bangkok, Siem Reap, Hoi An, Hanoi, Ha Long Bay, or Songkran."
---

# Family Trip Planner — Southeast Asia 2026

This skill contains the preferences, constraints, and key data for Yossi's family trip to Cambodia, Vietnam, and Thailand. Use it as context when modifying the trip plan.

## Family Details

- **Family size:** 6 people
- **Composition:** 2 parents + daughter (16), son (14), son (13), daughter (8)
- **Language:** Hebrew (content is RTL)
- **Budget level:** Comfortable — 300-500$/day for the whole family
- **Trip style:** 50% beach/relaxation, 50% touring/sightseeing
- **Food:** Interested in local street food and authentic cuisine
- **Priorities:** Beautiful landscapes, cultural experiences, interesting food, kid-friendly

## Flight Details

### Main Flights (Already Purchased)
| Leg | Date | Time | Route |
|-----|------|------|-------|
| Outbound | 23/3/2026 | Depart 21:30 | TLV → Bangkok (BKK) |
| Arrival | 24/3/2026 | Arrive 13:50 | Bangkok (BKK) |
| Return | 13/4/2026 | TBD | Bangkok (BKK) → TLV |

**Extension option:** Can extend up to 20/4/2026 (+7 days)

### Connection Plan
- Land BKK at 13:50 on 24/3
- Same-day evening flight to Siem Reap (~19:30 Bangkok Airways)
- ~3.5 hour connection time (tight for family of 6 — consider overnight in BKK as backup)

## Current Itinerary Summary

| Dates | Destination | Nights |
|-------|-------------|--------|
| 24/3 evening | Transit: Bangkok → Siem Reap | 0 |
| 24-28/3 | Siem Reap, Cambodia | 4 |
| 29-30/3 | Phnom Penh, Cambodia | 2 |
| 31/3-2/4 | Ho Chi Minh City, Vietnam | 3 |
| 3-6/4 | Hoi An / Da Nang, Vietnam | 4 |
| 7-9/4 | Hanoi + Ha Long Bay, Vietnam | 3 |
| 10-12/4 | Bangkok, Thailand | 3 |
| 13/4 | Fly home | - |

**Total:** 21 days, 20 nights

## Key Dates to Remember
- **Songkran Festival:** 12-13 April (coincides with Bangkok stay — great for the kids!)
- **Pesach 2026:** Starts evening of 1/4 (during HCMC/Hoi An leg)

## Visa Requirements
- **Thailand:** Visa-free for Israelis (30 days)
- **Cambodia:** Visa on Arrival (~30$/person, need passport photo + USD cash)
- **Vietnam:** e-Visa required (apply at evisa.gov.vn, ~25$/person, 3-7 business days)

## Internal Flights to Book
1. 24/3: Bangkok → Siem Reap (Bangkok Airways)
2. 28/3: Siem Reap → Phnom Penh (Cambodia Angkor Air / Lanmei)
3. 30/3: Phnom Penh → HCMC (Vietnam Airlines)
4. 3/4: HCMC → Da Nang (VietJet / Vietnam Airlines)
5. 8/4: Da Nang → Hanoi (VietJet / Vietnam Airlines)
6. 11/4: Hanoi → Bangkok (AirAsia / VietJet)

## File Architecture

The trip data is stored in two files in the `Pesah_2026` folder:

- **`trip_data.json`** — All trip content (dates, attractions, links, budget, checklist, etc.)
- **`trip_guide.html`** — Lightweight HTML viewer that loads and renders `trip_data.json`

### How to Modify the Trip
When the user asks to change the itinerary:
1. **Edit only `trip_data.json`** — the HTML never needs to change
2. The JSON structure has these top-level keys:
   - `trip_info` — basic trip metadata, route display
   - `timeline` — the colored bar segments
   - `overview_table` — the summary table
   - `destinations` — array of destination objects with day_tabs and day_panes
   - `food_guide` — food recommendations by country
   - `flights` — internal flight details
   - `budget` — cost breakdown
   - `practical` — visa, health, apps, currency info
   - `extensions` — optional trip extension ideas
   - `checklist` — pre-trip checklist items
3. Each destination has `day_tabs` (tab buttons) and `day_panes` (content per tab)
4. Links use `maps.google.com/?q=` format for maps, Wikipedia for info, Google Images for photos

### Link Format
- **Map:** `https://maps.google.com/?q=Place+Name`
- **Info:** `https://en.wikipedia.org/wiki/Article_Name`
- **Photos:** `https://www.google.com/search?q=Place+Name&tbm=isch`
- **Tickets:** Direct link to official booking site

## User Preferences for Content
- All attraction names should include **English names** alongside Hebrew
- Local script names (Khmer អក្សរខ្មែរ, Vietnamese Tiếng Việt, Thai อักษรไทย) where relevant
- Each multi-day destination should have **day-by-day tabs** for navigation
- Every attraction should have: 📍 Map link, 📖 Read more, 📸 Photos links
- Tips should be practical and family-oriented
- Budget estimates should account for 6 people (2 hotel rooms)
