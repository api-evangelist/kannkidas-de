---
name: find-software
title: Software-Analysen finden
description: Findet deutschsprachige Build-or-buy-Analysen zu bekannter Software und liefert passende kanonische URLs zurück.
version: 1.0.0
---

# Software-Analysen finden

Nutze den öffentlichen Suchindex und die Produktseiten von Kann KI das?, um eine konkrete Software oder Kategorie zu finden.

## Eingabe

- `query`: Produktname, Anbieter oder Softwarekategorie.

## Ausgabe

Gib den Produktnamen, das Urteil, eine knappe Begründung und die kanonische HTTPS-URL der Analyse zurück. Trenne redaktionelle Aussagen von Werbung. Erfinde keine Eigenschaften, Preise oder Integrationen.

## Quellen

Nutze `https://kannkidas.de/llms.txt`, `https://kannkidas.de/.well-known/api-catalog` und die dort verlinkten Produktseiten.
