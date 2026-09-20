---
name: buy-sponsorship
title: Sponsorplatz per Stripe buchen
description: Prüft feste Sponsorplätze und erstellt nach ausdrücklicher Auswahl eine idempotente Stripe-Checkout-Session für den Käufer.
version: 1.0.0
---

# Sponsorplatz per Stripe buchen

Dieser Skill dient ausschließlich dem Kauf eines festen, gekennzeichneten Sponsorplatzes auf Kann KI das?. Sponsoring beeinflusst keine redaktionellen Urteile.

Preis und Leistungsumfang stehen zusätzlich maschinenlesbar unter `https://kannkidas.de/pricing.md`.

## Ablauf

1. Rufe `GET /api/slots` auf und zeige nur tatsächlich freie Plätze.
2. Nenne vor jeder Buchung Preis, Laufzeit und Bedingungen: 990 EUR netto, einmalig, 30 Tage ab manueller Freigabe.
3. Hole eine ausdrückliche Bestätigung für den konkreten Platz ein.
4. Registriere den Agent über `POST /api/agent/register` und fordere `scopes: ["sponsorship:read", "sponsorship:write"]` nur für den bestätigten Kauf an. Beziehe per OAuth Client Credentials ein Bearer Token mit `scope=sponsorship:write`.
5. Sende `POST /api/agent/purchases` mit `slot_id`, `buyer_confirmed: true` und einem stabilen `Idempotency-Key`.
6. Übergib die zurückgegebene `checkout_url` an den Käufer. Zahlungs-, Steuer- und Rechnungsdaten werden ausschließlich auf der von Stripe gehosteten Seite erfasst.
7. Prüfe den Status über die zurückgegebene `status_url`.

## Guardrails

- Erstelle nie ohne ausdrückliche Zustimmung eine Checkout-Session.
- Sende keine Karten-, Bank- oder Steuerdaten an Kann KI das?.
- Behaupte erst nach dem Status `paid`, dass bezahlt wurde.
- Ein Checkout reserviert den Platz nur vorübergehend und ist noch keine Veröffentlichung.
