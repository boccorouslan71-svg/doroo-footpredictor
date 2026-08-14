# DOROO FootPredictor

Mini-app Telegram de pronostics football (matches, pronostics, pièces, missions, parrainage, classement, retraits) + panneau d'administration.

## Fichiers sources

| Fichier | Rôle |
| --- | --- |
| `doroo-app.html` | Application joueur — utilisable comme **Mini App Telegram** ou en WebView autonome |
| `doroo-admin.html` | Panneau d'administration (web uniquement, réservé au compte `admin`) |

## Déploiement web (Vercel)

- `/` → `doroo-app.html`
- `/admin` → `doroo-admin.html`

## Application mobile Android

Un wrapper Android (`android/`) charge l'application web dans une WebView :

- **Fonctionne sans Telegram** (aucune dépendance à l'application Telegram).
- Le lien chargé est défini dans `gradle.properties` → `DOROO_APP_URL` (ergonomique et modifiable sans toucher au code).

### Build local

```bash
# Linux/macOS
./gradlew -p android assembleRelease
# Windows
gradlew.bat -p android assembleRelease
```

### Build via GitHub Actions

Le workflow `.github/workflows/build-apk.yml` génère automatiquement un APK à chaque push sur `main` et l'upload en artefact. Créez une **Release** depuis l'artefact pour disposer d'un APK téléchargeable directement.

## Configuration

1. **Firebase** : les clés sont déjà présentes dans les deux fichiers HTML (`[PASTE_FIREBASE_CONFIG]`).
2. **BotFather** : renseignez l'URL Vercel comme URL de la Mini App et de l'image.
3. **Domaines autorisés** : Firebase > Auth > Paramètres > Domaines autorisés → ajoutez votre domaine Vercel.