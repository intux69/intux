# Implementierungsplan - Modernisierung Grundbildungszentrum-Halle

Dieser Plan sieht vor, das Projekt "Grundbildungszentrum-Halle" auf den exakt gleichen "perfekten" technischen Stand zu bringen wie die `intuxApp`.

## User Review Required

> [!NOTE]
> **Konsistenz:** Ich übertrage alle Fehlerbehebungen (WhatsApp/E-Mail) und Komfort-Funktionen (Drucken, Java 17, neue Gradle-DSL) auf dieses Projekt.

## Proposed Changes

### Build Konfiguration & Tooling

#### [MODIFY] [gradle.properties](file:///home/intux/AndroidStudioProjects/Grundbildungszentrum-Halle/gradle.properties)
- Aktivierung von `android.newDsl=true` und `android.builtInKotlin=true`.

#### [MODIFY] [app/build.gradle](file:///home/intux/AndroidStudioProjects/Grundbildungszentrum-Halle/app/build.gradle)
- Umstellung auf die neue DSL-Syntax (`compileSdk = 35`).
- Upgrade auf Java 17 (`VERSION_17`).
- Entfernen des veralteten Kotlin-Plugins (Nutzung von Built-in Kotlin).

### Quellcode & UX (MainActivity)

#### [MODIFY] [MainActivity.kt](file:///home/intux/AndroidStudioProjects/Grundbildungszentrum-Halle/app/src/main/java/com/gbz/grundbildungszentrum_halle/MainActivity.kt)
- **Link-Fix:** Priorisierung von `whatsapp:`, `tel:`, `mailto:` vor der Domain-Prüfung.
- **Druckfunktion:** Integration des `AndroidPrintInterface` und des `PrintManager`.
- **Injection:** Automatisches Umbiegen von `window.print()` in JavaScript.

## Verification Plan

### Automated Tests
- Projekt bauen mit `./gradlew :app:assembleDebug`.

### Manual Verification
- Test der Kontakt-Buttons (Mail, WhatsApp) auf der GBZ-Webseite.
- Test des Druckens.
- Prüfung der Ladeanimation und des Offline-Modus.
