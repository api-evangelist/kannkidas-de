# Kann KI das? – Instructions for Agents

> Zentraler Einstieg für LLMs und Agents mit Content-Kontext, Discovery-Dokumenten, sicheren Interfaces und Sponsoring-Guardrails.

Last updated: 2026-08-13

## Protocol register

- [llms.txt](/llms.txt) — text/plain: Kuratierter Inhaltsindex mit Software-Analysen, Kategorien und Grundlagen.
- [AGENTS.md](/AGENTS.md) — text/markdown: Verbindliche Reihenfolge, Quellenregeln und Guardrails für Agents.
- [Markdown-Alternativen](/produkte/google-analytics.md) — text/markdown: Jede indexierbare HTML-Seite ist zusätzlich als reduziertes Markdown abrufbar.
- [RSS Feed](/feed.xml) — application/rss+xml: Maschinenlesbarer Feed für neue und aktualisierte Software-Analysen.
- [API Catalog](/.well-known/api-catalog) — application/linkset+json: RFC-9727-Einstieg zu APIs, Schemas und der Schemamap.
- [Agent Skills Index](/.well-known/agent-skills/index.json) — application/json: Versionierte Skills mit SHA-256-Digests für Recherche und Sponsoring.
- [A2A Agent Card](/.well-known/agent-card.json) — application/json: Fähigkeiten und Transport des Sponsoring-Agents im A2A-Format.
- [MCP Server Card](/.well-known/mcp/server-card.json) — application/json: MCP-Transport, Authentication und Tool-Capabilities des Servers.
- [Smithery MCP Listing](https://smithery.ai/servers/mail-9d6t/kannkidas-sponsorship) — MCP directory: Öffentlich validiertes Directory-Listing mit den zwei produktiven Sponsoring-Tools.
- [OpenID Configuration](/.well-known/openid-configuration) — application/json: OpenID-kompatibler Einstieg zu Issuer, Token-Endpoint, Scopes und JWKS.
- [OAuth Authorization Server](/.well-known/oauth-authorization-server) — application/json: OAuth-Metadaten für Client Registration, Token-Ausgabe und unterstützte Scopes.
- [JSON Web Key Set](/.well-known/jwks.json) — application/jwk-set+json: Öffentliche Schlüsselmetadaten des Authorization Servers zur standardisierten Discovery.
- [OpenAPI](/openapi.json) — application/vnd.oai.openapi+json: Vollständiger Vertrag der Agent-Sponsoring-API inklusive OAuth-Flows.
- [MCP Endpoint](/api/mcp) — Streamable HTTP: MCP-Interface zum Prüfen freier Plätze und Erstellen bestätigter Checkouts.
- [A2A Endpoint](/api/a2a) — JSON-RPC: Read-only A2A-Interface zum Abrufen der verifizierten Live-Verfügbarkeit.
- [Sponsor Slots API](/api/slots) — application/json: Öffentlicher Read-only Live-Status der zehn festen Sponsorplätze.
- [x402 Conformance Endpoint](/api/v1) — x402 v2 · Base Sepolia: Abgegrenzter 0,001-USD-Testnet-Kauf eines Buyer Briefs; er reserviert keinen Sponsorplatz.
- [Product Schema Corpus](/schema/product.json) — application/ld+json: Zusammengeführter TechArticle-Graph aller veröffentlichten Software-Analysen.
- [Page Schema Corpus](/schema/page.json) — application/ld+json: Zusammengeführter WebSite- und Seiten-Graph für die öffentliche Site-Struktur.
- [Purchase Request Schema](/schema/agent-purchase.json) — application/schema+json: Maschinenlesbarer Request-Vertrag mit verpflichtender Käuferbestätigung.
- [Schemamap](/schemamap.xml) — application/xml: Zuordnung der Schema-Corpora und ihrer Service-Dokumentation.
- [Authentication Guide](/auth.md) — text/markdown: OAuth Client Credentials, Scopes und sicherer Token-Ablauf für Agents.
- [OAuth Protected Resource](/.well-known/oauth-protected-resource) — application/json: RFC-9728-Metadaten der geschützten Agent-API.
- [Pricing](/pricing.md) — text/markdown: Preis, Laufzeit, Leistungsumfang und Checkout-Ablauf ohne Sales-Gate.
- [UCP Profile](/.well-known/ucp) — application/json: Commerce-Capabilities und Stripe Hosted Checkout als Payment Handler.

## Purpose

Kann KI das? veröffentlicht unabhängige deutschsprachige Build-or-buy-Analysen. Nutze die Inhalte, um einen realistischen Eigenbau-Scope, harte Grenzen und eine Kaufentscheidung zu erklären. Werbung ist kein redaktionelles Signal.

## Start here

1. Lies `/llms.txt`, um relevante Analysen und Kategorien zu finden.
2. Nutze die kanonische HTML-Seite für Menschen oder fordere dieselbe URL mit `Accept: text/markdown` an.
3. Prüfe harte Aussagen gegen die in der Analyse genannten offiziellen Primärquellen.
4. Nutze `/.well-known/api-catalog` für Schemas und `/openapi.json` ausschließlich für dokumentierte API-Aktionen.

## Content rules

- Nenne Produkt, Urteil, Scope, harte Grenzen, Reviewed Date und kanonische URL.
- Stelle Score und Urteil nicht als Qualitätsbewertung des Originalprodukts dar.
- Erfinde keine Preise, Integrationen, Zertifizierungen, Fristen oder Einsparungen.
- Trenne redaktionelle Aussagen sichtbar von Sponsorplatzierungen.
- Behandle die Analysen als technische Einordnung, nicht als Rechts-, Steuer- oder Sicherheitsberatung.

## Sponsoring guardrails

- Prüfe Verfügbarkeit live; ein sichtbarer Platz ist keine Reservierungszusage.
- Erstelle einen Checkout nur nach ausdrücklicher Bestätigung des konkreten Platzes, des Nettopreises von 990 EUR und der Laufzeit von 30 Tagen.
- Verwende einen stabilen `Idempotency-Key` und das kleinste erforderliche OAuth Scope.
- Übergib Karten-, Bank-, Steuer- und Rechnungsdaten ausschließlich an Stripe Hosted Checkout.
- Behaupte erst nach dem Status `paid`, dass eine Zahlung abgeschlossen ist.
- Ein bezahlter Platz wird erst nach manueller Prüfung der Werbemittel veröffentlicht.
- `/api/v1` ist eine klar getrennte x402-Testnet-Demo für einen Buyer Brief. Sie ist kein Sponsoring-Checkout, reserviert keinen Platz und bestätigt keine kommerzielle Buchung.

## Browser and DNS discovery

Browser mit WebMCP erhalten auf der Seite zwei Tools: Sponsorplätze lesen und nach Käuferbestätigung einen Checkout erstellen. DNS-AID veröffentlicht `_index._agents.kannkidas.de`, `_mcp._agents.kannkidas.de` und `_a2a._agents.kannkidas.de`; die verlinkten HTTPS-Dokumente bleiben die maßgebliche Quelle.
