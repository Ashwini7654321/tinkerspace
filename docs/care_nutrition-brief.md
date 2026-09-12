# care_nutrition — Project-Specific Brief

- Backend package: care_nutrition
- Frontend slug: care_nutrition_fe
- Settings prefix: NUTRITION
- i18n prefix: nutrition__
- Preview port: 4174

## Purpose
Manage growth monitoring and nutritional supplementation for public health programmes: record anthropometric measurements (weight, height, MUAC), compute indicators (BMI-for-age, stunting/wasting risk), and schedule/track supplement distribution (e.g., IFA, vitamin A).

## Scope (MVP)
- Capture periodic growth measurements for a patient.
- Calculate and surface nutrition risk flags.
- Log supplementation events with dose, schedule, and adherence.
- Basic dashboards: due today/overdue supplementation.

## Data model (initial)
- NutritionRecord: patient, date, weight_kg, height_cm, muac_mm, z_scores(JSON), notes.
- SupplementEvent: patient, programme (IFA/VitA/Other), dose, planned_date, given_date, status(planned|given|missed), notes.

Prefer extending core Patient via meta where feasible; keep FKs to core only where necessary.

## UI placement (extension points)
- FacilityHomeActions: quick link to “Nutrition dashboard”.
- Patient profile tab: “Nutrition” tab showing latest measurements and supplementation log.

## Auth and roles
- care-nurse, care-staff: create/update NutritionRecord and SupplementEvent.
- care-admin: manage configurations.

## Patient portal
Not in v1; consider OTP-scoped views later for self-tracking.

## Third-party services
None for MVP.

## Next steps
- Scaffold backend and frontend from care_scaffold templates.
- Wire into core: plug_config.py + REACT_ENABLED_APPS (port 4174).
- Build models → serializers/viewsets → verify API → frontend types/components → i18n.
