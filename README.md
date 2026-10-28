# Ecovacs T50 Gen3 Patch

Custom component override van de kernintegratie **Ecovacs** uit Home Assistant
2026.10.4, met één toevoeging: ondersteuning voor apparaatklasse **tquqs3**
(DEEBOT T50 OMNI Gen3, o.a. model FARADAYS_SE_BLACK_GEN3_INT).

## Waarom

deebot-client 18.7.0 (de versie in HA 2026.10.4) kent klasse tquqs3 nog niet,
waardoor een T50 OMNI Gen3 door Home Assistant wordt overgeslagen
("Device class tquqs3 not recognized"). Upstream voegt de klasse toe als
symlink naar het bestaande T50 OMNI-capabilitiesbestand `fd60kt`
(DeebotUniverse/client.py, PR #1917). Deze override doet hetzelfde in
`__init__.py`: hij registreert de fd60kt-module onder de naam
`deebot_client.hardware.tquqs3`. Verder is de integratie byte-identiek aan de
kernversie.

## Installatie

1. HACS > Integrations > ⋮ > Custom repositories: voeg deze repo toe,
   categorie **Integration**.
2. Download "Ecovacs T50 Gen3 Patch" en herstart Home Assistant.
3. De bestaande Ecovacs-config-entry werkt ongewijzigd door; de Gen3 verschijnt
   als vacuum met extra entiteiten (status, accu, kaart, station, kamers).

## Verwijderen

Zodra deebot-client tquqs3 zelf meelevert (en HA die versie pint), is deze
patch overbodig: verwijder de integratie in HACS en herstart Home Assistant.
De kernintegratie neemt het dan weer over.
