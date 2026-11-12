# FIT LEBEN PLUS für das iPhone

Capacitor-8-Hülle für https://fit-leben-plus.floot.app, auf Basis des exportierten Floot-iOS-Projekts. Die App lädt die aktuelle veröffentlichte Web-App. Internet ist erforderlich.

## Build und Installation

1. Auf `main` pushen oder unter **Actions → iPhone-App bauen (.ipa zum Sideloaden) → Run workflow** starten.
2. Nach erfolgreichem Lauf das Artefakt **FIT-LEBEN-PLUS-ipa** herunterladen und entpacken.
3. `FIT_LEBEN_PLUS.ipa` unter Windows in Sideloadly öffnen, das angeschlossene iPhone und dieselbe Apple-ID wie bei MIXWERK auswählen und installieren.

Der Workflow baut auf einem macOS-Runner mit Node 22 und Xcode 26 oder neuer. Die IPA ist unsigniert; Apple-Zugangsdaten oder Zertifikate werden im Repository und im Build nicht benötigt. Die Floot-Bundle-ID bleibt erhalten und unterscheidet sich von MIXWERK.

## Native Funktionen und kostenlose Apple-ID

| Funktion | In diesem Projekt | Einschränkung |
| --- | --- | --- |
| Dateizugriff, Teilen | Capacitor Filesystem und Share | Mit kostenloser Apple-ID nutzbar; Funktionen auf dem iPhone prüfen. |
| Sprachausgabe | Community Text-to-Speech | Mit kostenloser Apple-ID nutzbar. |
| Kamera und Barcode-Scanner | Kamera-Berechtigung; ZXing in der Floot-Web-App | Mit kostenloser Apple-ID nutzbar; Kamerazugriff erlauben. |
| Apple Health | Capgo Health, HealthKit-Entitlements und Nutzungstexte | Apple unterstützt HealthKit auch für kostenlose Entwicklerkonten. Der tatsächliche Zugriff hängt davon ab, ob Sideloadly beim erneuten Signieren die benötigte Berechtigung mit passendem Profil erhält. Ein erfolgreicher Build belegt das nicht. |
| Remote-Push (APNs) | Kein APNs-Plugin oder Push-Entitlement für diesen kostenlosen Testbuild eingerichtet | Mit kostenloser Apple-ID nicht verfügbar; ein Sideloadly-Schalter hebt diese Grenze nicht auf. |

Für die normalen Funktionen sind dieselben Sideloadly-Einstellungen wie bei MIXWERK vorgesehen. Die kostenlose Signatur gilt üblicherweise sieben Tage. Lokale Erinnerungen sind eine separate Funktion und werden durch diesen Build nicht automatisch ergänzt.

## Grundlage

- Floot-Projekt: `01bb6bca-7f6b-47b0-bbfe-d6cff84dd031`
- Native Swift-Dateien, Storyboards und Grafiken aus dem Floot-Export.
- Info.plist und HealthKit-Entitlements aus dem geprüften Quellcode-Export vom 12. November 2026.
- Aktueller Web-Quellcode-Digest: `40877b4da81dd2514cf00a5793ef0b9ae3a5fd928f53835e50d66a9b3b3c2319`.

Die nativen Abhängigkeiten sind fest versioniert. Filesystem und Share wurden gegenüber dem älteren nativen Export ergänzt. Der vollständige Floot-Backend-Quellcode gehört nicht zu diesem iOS-Build-Repository.

Quellen: [Apple: unterstützte iOS-Funktionen](https://developer.apple.com/help/account/reference/supported-capabilities-ios), [Apple: kostenlose Entwicklungsprofile](https://developer.apple.com/support/compare-memberships/), [Sideloadly FAQ](https://sideloadly.io/faq).
