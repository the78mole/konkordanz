# Praktische Konkordanz

[![Build PDF](https://img.shields.io/github/actions/workflow/status/the78mole/konkordanz/build-pdf.yml?branch=main&label=Build%20PDF)](https://github.com/the78mole/konkordanz/actions/workflows/build-pdf.yml)
[![Lizenz](https://img.shields.io/github/license/the78mole/konkordanz)](LICENSE)
[![Open in Codespaces](https://img.shields.io/badge/Codespaces-Open-181717?logo=github)](https://github.com/the78mole/konkordanz/codespaces)

Ein System-Strategiepapier zur verfassungskonformen, wirtschaftlichen und sozial
gerechten Klimatransformation Deutschlands – als Antwort auf die Zukunftsklage
vor dem Bundesverfassungsgericht.

## Inhalt

| Datei / Verzeichnis | Beschreibung |
|---|---|
| [`konkordanz.md`](konkordanz.md) | **Zentrales Dokument:** Der 15-Punkte-Plan „Praktische Konkordanz" (Quarto-Quelldatei) |
| [`modellrechnungen/`](modellrechnungen/) | Quantitative Modellrechnungen und Anhänge |
| [`modellrechnungen/biomasse-kaskade.md`](modellrechnungen/biomasse-kaskade.md) | Anhang I: Biomasse-Kaskade, Pyrolyse-Ökonomie & Wasserstoff/HVO100 |
| [`modellrechnungen/zeitplan-co2-pfade.md`](modellrechnungen/zeitplan-co2-pfade.md) | Anhang II: Implementierungs-Roadmap 2026–2035, CO₂-Pfade & Finanzierungsarchitektur |

## PDF generieren

Das zentrale Papier kann mit [Quarto](https://quarto.org) und dem integrierten
Typst-Backend als PDF gerendert werden:

```bash
# Quarto installieren: https://quarto.org/docs/get-started/
quarto render konkordanz.md --to typst
# → _output/konkordanz.pdf
```

## CI/CD Workflows

| Workflow | Trigger | Beschreibung |
|---|---|---|
| [Build PDF](.github/workflows/build-pdf.yml) | Push/PR auf `main`, manuell | Rendert das PDF mit Quarto + Typst und stellt es als Artefakt bereit |
| [Create Release](.github/workflows/release.yml) | **Nur manuell** (`workflow_dispatch`) | Erstellt ein versioniertes Release (paulhatch semantic version) mit dem PDF und den Commit-Kommentaren als Release-Notes |

## Diskussion

Dieses Repository dient als offene Diskussionsgrundlage. Beiträge, Korrekturen
und alternative Perspektiven sind ausdrücklich erwünscht – via
[Issues](../../issues) oder [Pull Requests](../../pulls).

## Lizenz

Siehe [LICENSE](LICENSE).
