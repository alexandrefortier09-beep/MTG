# Color Pie — Compteur de vie Magic (Android)

Application Android native (WebView) qui emballe le compteur de vie Commander :
vie, commander damage, poison, dé d20, soundboard avec 4 sons embarqués
(remplaçables), 2 à 6 joueurs, écran maintenu allumé, plein écran.
Aucune permission Internet : tout est local.

L'app web autonome se trouve dans `app/src/main/assets/index.html`.
Pour la mettre à jour, remplace simplement ce fichier et recompile.

---

## Option 1 — Obtenir l'APK SANS rien installer (GitHub Actions)

1. Crée un dépôt GitHub (privé ou public).
2. Pousse tout le contenu de ce dossier dans le dépôt.
3. Onglet **Actions** → le workflow « Build APK » se lance tout seul
   (sinon, clique « Run workflow »).
4. À la fin, ouvre le run → section **Artifacts** → télécharge
   **ColorPie-debug-apk** → dézippe → `app-debug.apk`.
5. Transfère l'APK sur ton téléphone et installe-le
   (autorise « sources inconnues » si demandé).

## Option 2 — Android Studio (build local)

1. **Android Studio** → *Open* → sélectionne ce dossier.
2. Laisse la synchronisation Gradle se terminer
   (télécharge Gradle, le plugin Android et les dépendances).
3. Menu **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
4. Clique « locate » → récupère `app/build/outputs/apk/debug/app-debug.apk`.
   (Ou branche ton téléphone et clique ▶ Run.)

## Option 3 — Ligne de commande (JDK 17 + Android SDK installés)

```
./gradlew assembleDebug
```

APK généré : `app/build/outputs/apk/debug/app-debug.apk`

---

## Notes

- **APK de debug** : signé avec la clé de debug, parfait pour un usage perso /
  sideload. Pour le Play Store, il faudrait un build *release* signé.
- **minSdk 26** (Android 8.0+). Couvre la quasi-totalité des téléphones récents.
- **Sons** : les 4 sons par défaut sont dans le HTML (base64). Le bouton ✎
  permet d'en charger d'autres ; ils sont mémorisés sur l'appareil.
- **Persistance** : les sons personnalisés persistent (origine https interne via
  WebViewAssetLoader). L'état de la partie en cours, lui, n'est pas persisté.

## Versions

- Android Gradle Plugin 8.6.1 · Gradle 8.9 · Kotlin 2.0.20
- compileSdk/targetSdk 34 · minSdk 26 · JDK 17
