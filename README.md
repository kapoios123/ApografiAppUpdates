
Ο κύκλος update — 4 βήματα, πάντα με αυτή τη σειρά
Ας πούμε ότι τώρα είσαι στην v1 (versionCode 1). Το επόμενο θα είναι v2. Παντού όπου λέω «2», βάζεις τον επόμενο αριθμό.
Βήμα 1 — Άλλαξε τα νούμερα στο Gradle
Άνοιξε app/build.gradle.kts, μέσα στο defaultConfig:
kotlinversionCode = 2        // +1 κάθε φορά. ΠΑΝΤΑ μεγαλύτερο από πριν.
versionName = "1.1"    // ό,τι θες, για ανθρώπους
Πάτα Sync Now πάνω δεξιά.

Ο versionCode είναι ο αριθμός που κρίνει το update. Αν δεν τον αυξήσεις, κανένα κινητό δεν θα δει ενημέρωση.

Βήμα 2 — Φτιάξε Signed APK (ίδιο keystore πάντα)

Build → Generate Signed Bundle / APK
APK → Next
Keystore: my-new-release-key, alias apografi, οι κωδικοί σου
Next → release → Finish
Πάρε το αρχείο από app/release/app-release.apk


Πάντα my-new-release-key. Ποτέ άλλο. Αλλιώς τα κινητά απορρίπτουν το update.

Βήμα 3 — Νέο Release στο GitHub με το APK

Repo → Releases → Create a new release
Tag: v2 → Create new tag
Title: v2
Attach binaries: ρίξε εκεί το app-release.apk
Publish release


Το APK πάει ΠΑΝΤΑ μέσα σε Release (όχι «Upload files» — εκεί είναι το όριο 25MB).

Βήμα 4 — Ενημέρωσε το version.json
Στο repo, άνοιξε το version.json → μολυβάκι (Edit) → άλλαξέ το σε:
json{
  "versionCode": 2,
  "versionName": "1.1",
  "apkUrl": "https://github.com/ΤΟ_USERNAME_ΣΟΥ/ApografiAppUpdates/releases/download/v2/app-release.apk"
}
Commit changes.
