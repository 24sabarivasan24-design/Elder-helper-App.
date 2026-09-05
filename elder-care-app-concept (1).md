# Sahay — An AI Companion App for Elder Independence

*Working name "Sahay" (Hindi/Tamil-adjacent word for "help/support") — placeholder, swap for your brand.*

## 1. The problem

Elderly users (especially those aging in place, living alone, or separated from family who work/live elsewhere) face a specific gap: they need to get real-world things done — see a doctor, refill a prescription, pay a bill, get to an appointment, restock the kitchen — but most apps that do these things were built for a 25-year-old's thumbs and patience, not a 70-year-old's eyesight, hearing, or trust in technology.

The result today: they either depend entirely on an adult child (who isn't always reachable), or they simply don't do the task — skipped medication, missed appointments, unpaid bills, isolation during emergencies.

**The insight:** this isn't a "simpler UI" problem. It's a *single trusted assistant* problem — one voice-first entry point that quietly handles many different real-world services, backed by an AI that completes multi-step tasks rather than just navigating to a screen.

## 2. Who this is for

- **Primary user:** adults 65+, living independently or semi-independently, comfortable with a phone call but wary of "apps."
- **Secondary user (payer/admin):** adult children or caregivers who want visibility and control (approve payments, get emergency alerts, see task history) without micromanaging.
- **Tertiary:** care homes / community organizations who could deploy this at a facility level.

## 3. Core feature set

| Feature | What it does | Elder-specific design choice |
|---|---|---|
| **Hospital & doctor booking** | Search nearby doctors/hospitals by specialty, book/reschedule appointments, get reminders, store visit history | Pre-filled "usual doctor" shortcuts; appointment confirmations read aloud and sent to a linked family member |
| **Medicine ordering** | Reorder existing prescriptions, upload a new prescription via photo, subscription refills, dosage reminders | OCR reads handwriting on prescriptions; "reorder last month's order" as a single button |
| **Payments** | Utility bills, insurance premiums, rent, subscriptions | Optional "approve before pay" workflow where a linked family member co-signs large or unusual payments |
| **Transport** | Book a cab/auto to a saved destination (hospital, temple, family home) | Pickup/drop pre-filled from history; driver photo + vehicle number read aloud; live trip sharing with family by default |
| **Grocery & essentials** | Reorder a standing list, one-tap "same as last week," staple substitution | Voice-built shopping lists ("I'm out of rice") auto-mapped to catalog items |
| **Emergency assistance** | One-tap SOS: alerts emergency contacts + local ambulance/emergency number, shares live location, surfaces medical ID (allergies, conditions, blood group) | Physical-button-sized always-visible SOS; works even if the rest of the app is mid-task; no login/PIN required to trigger |
| **Voice access (everywhere)** | Every feature above reachable by speaking naturally, in the user's language/dialect | Voice is the *default* input, not an accessibility add-on; typing/tapping is the fallback, not the other way around |
| **AI task assistant** | Understands a goal ("I need to see my eye doctor next week and I'm running low on my BP medicine") and executes the multi-step task end-to-end across the services above, asking only for genuinely necessary confirmations | Confirms out loud before anything irreversible (payment, ride booking); keeps a plain-language log family can review |

## 4. What the AI assistant actually does (this is the differentiator)

Most "senior-friendly" apps are just existing apps with bigger buttons. The AI layer here is what turns six separate services into one relationship:

1. **Understands intent, not commands.** "My knee's been hurting" → offers to book the usual orthopedist, checks if a related medicine needs refilling, checks if a ride will be needed.
2. **Chains tasks.** Booking a hospital visit automatically prompts: "Should I also arrange a cab for 9am that day?"
3. **Remembers context.** Knows the user's regular doctors, pharmacy, standing grocery list, and family contacts, so requests get shorter over time.
4. **Escalates appropriately.** If something sounds like a medical emergency, it doesn't try to be clever — it goes straight to the emergency flow.
5. **Reports back in plain language**, not app notifications: a short spoken or texted summary of what got done each day, optionally shared with a family member.

## 5. Accessibility & trust principles (non-negotiable design rules)

- Minimum 18–20pt text, 7:1 contrast ratio, tap targets ≥ 64px.
- Voice-first, but never voice-*only* — every action has a visible, tappable equivalent.
- No feature should require more than 2 taps beyond the home screen; the AI assistant is the shortcut for everything else.
- Nothing is ever silently auto-charged — payments and bookings always get a spoken/visual confirmation.
- Family "co-pilot" access is opt-in and transparent — the elder always knows what their family can see.
- Works in the user's own language and a local dialect/accent, not just standard-accent English/Hindi.

## 6. Suggested tech architecture (MVP-appropriate, not over-engineered)

- **Mobile app:** React Native or Flutter (single codebase, native voice/mic access, works on low/mid-range Android phones which dominate this user base).
- **Voice layer:** speech-to-text tuned for older voices/accents (e.g., regional-language ASR), text-to-speech for responses; fallback to phone-call-style IVR for users who won't use a smartphone app at all.
- **AI orchestration layer:** an LLM-based agent that maps natural-language intent to the right internal "skill" (booking, ordering, paying, transport, grocery) and asks clarifying questions only when necessary.
- **Service integrations (India-relevant examples, swap per market):**
 - Hospitals/doctors: Practo-style booking APIs or direct hospital partnerships
 - Pharmacy: PharmEasy/1mg-style partner APIs, or local pharmacy network integration
 - Transport: Ola/Uber APIs, or a vetted local driver network for trust-sensitive elder trips
 - Grocery: BigBasket/Instamart-style partner APIs, or local kirana store partnerships
 - Emergency: integration with local emergency numbers (e.g., 108/112 in India) plus direct family contact dialing
 - Payments: UPI/payment-gateway integration with a secondary "family approval" hold for large transactions
- **Data/privacy:** health and location data are the most sensitive things this app touches — plan for compliance with local data protection law (e.g., India's DPDP Act) from day one, and be explicit with users about what's stored and shared.

## 7. Business model options

1. **Freemium + family subscription:** core booking/ordering free (commission-funded), premium tier (family dashboard, priority emergency response, unlimited AI assistant use) sold to the adult child, not the elder.
2. **Commission on transactions:** small cut on hospital bookings, medicine orders, rides, groceries booked through the app.
3. **B2B2C via care homes/RWAs/insurers:** license the platform to senior living communities, health insurers (as a retention/engagement tool), or corporate elder-care benefits programs.
4. **Emergency/SOS as a paid add-on:** a monitored emergency-response tier (like a digital medical-alert pendant) — this is a proven willingness-to-pay category.

## 8. MVP scope (build this first, not everything)

**Phase 1 (3 months):**
- Voice-first home screen + 3 features: medicine reorder, hospital appointment booking, emergency SOS
- Family companion view (read-only: upcoming appointments, SOS alerts)
- One city, one language, 2–3 real service partners

**Phase 2:**
- Add transport, grocery, payments
- AI task-chaining ("book appointment + arrange ride")
- Multi-language voice support

**Phase 3:**
- Family payment approval workflows
- B2B pilot with a care home or hospital chain
- Proactive AI check-ins ("It's been 3 days since your last walk reminder — everything okay?")

## 9. Key risks

- **Trust & adoption:** elders are (rightly) wary of apps that touch money and health — go slow, lead with free/low-stakes features (booking, reminders) before payments.
- **Voice recognition accuracy** for older voices, regional accents, and background noise/hearing aids — budget real testing time here, it will make or break the experience.
- **Family dynamics:** the "family co-pilot" view has to be genuinely opt-in, or it will feel like surveillance rather than support.
- **Service partner reliability:** the app is only as good as the actual hospital/pharmacy/driver network behind it — this is an operations business as much as a software one.
- **Regulatory:** health data, payment data, and emergency-response commitments all carry real liability — get legal input early, especially around what the SOS feature promises to do.

## 10. Early success metrics

- % of tasks completed via voice vs. tap
- Time from "I need X" to task completion
- Weekly active use per elder user (a sign it's becoming a habit, not a novelty)
- Family adoption rate of the companion view
- SOS response time (trigger → contact reached)
