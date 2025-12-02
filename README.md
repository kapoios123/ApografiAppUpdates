Κάθε update cycle έχει 3 υποχρεωτικά βήματα, πάντα με τη σωστή σειρά:


ΒΗΜΑ 1 — Αλλάζεις versionCode + versionName στο Gradle
defaultConfig {
    applicationId = "com.example.apografiapp"
    minSdk = 21
    targetSdk = 36

    versionCode = 2       // 🔥 ΠΡΕΠΕΙ ΝΑ ΑΥΞΑΝΕΤΑΙ ΠΑΝΤΑ !!!
    versionName = "1.1"   // optional but recommended
}


ΒΗΜΑ 2 — Κάνεις νέα Signed Release APK
Με τον ίδιο keystore όπως ΠΑΝΤΑ
(Αν αλλάξεις keystore → καταστροφή = το κινητό δεν επιτρέπει την αναβάθμιση).

Άρα:

✔️ Build → Generate Signed Bundle/APK
✔️ APK
✔️ Release
✔️ Ίδιο keystore
✔️ Πατάς Finish
👉 Παίρνεις app-release.apk


ΒΗΜΑ 3 — Ανεβάζεις το νέο APK + νέο version.json στο GitHub
ΠΡΟΣΟΧΗ:
Πρέπει να αντικαταστήσεις το παλιό APK με το νέο.

Το version.json πρέπει να έχει:

{
  "versionCode": 2,
  "apkUrl": "https://github.com/kapoios123/ApografiAppUpdates/releases/download/v2/app-release.apk"
}



----->το apkUrl δεν είναι απαραίτητο να αλλάξει καθώς δεν αλλάζουμε όνομα στο apk και το ανεβάζουμε στο ίδιο σημείο (αντικαθιστώντας το παλιό)
