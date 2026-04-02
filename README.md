# Portail Captif MikroTik

Portail captif générique prêt à déployer sur routeurs MikroTik (RouterOS).

## Fichiers

| Fichier | Rôle MikroTik |
|---|---|
| `login.html` | Page d'authentification principale |
| `status.html` | Dashboard session active |
| `logout.html` | Confirmation de déconnexion |
| `alogin.html` | Succès post-connexion (avec compte à rebours) |
| `error.html` | Affichage des erreurs |
| `radvert.html` | Message affiché avant redirection |
| `redirect.html` | Page de redirection intermédiaire |
| `rlogin.html` | Redirect vers le portail login |
| `hotspot.css` | Feuille de styles commune |
| `md5.js` | Librairie MD5 pour l'authentification CHAP |

## Déploiement sur MikroTik

1. Connecte-toi à ton MikroTik via **WinBox** ou **WebFig**
2. Va dans **Files** et navigue vers `/flash/hotspot/`
3. Supprime (ou sauvegarde) les fichiers HTML/CSS existants
4. Upload tous les fichiers de ce repo dans `/flash/hotspot/`
5. Va dans **IP > Hotspot > Server Profiles**, sélectionne ton profil et vérifie que le `HTML Directory` pointe vers `hotspot`

## Personnalisation

Pour adapter le portail à une marque spécifique :

- **Couleurs** : modifier les variables dans `hotspot.css` (lignes 1-4)
  - Couleur principale : `#2563eb`
- **Logo** : remplacer les emojis par une balise `<img>` dans chaque page
- **Textes** : modifier directement les fichiers HTML

## Variables MikroTik utilisées

| Variable | Description |
|---|---|
| `$(username)` | Nom d'utilisateur connecté |
| `$(ip)` | Adresse IP du client |
| `$(uptime)` | Durée de la session |
| `$(bytes-in-nice)` | Données montantes |
| `$(bytes-out-nice)` | Données descendantes |
| `$(session-time-left)` | Temps restant (si limité) |
| `$(remain-bytes-total-nice)` | Quota restant (si limité) |
| `$(error)` | Message d'erreur MikroTik |
| `$(link-login-only)` | URL de login |
| `$(link-logout)` | URL de logout |
| `$(link-redirect)` | URL de redirection post-login |
| `$(link-orig)` | URL originale demandée |
| `$(chap-id)` / `$(chap-challenge)` | Données CHAP pour l'auth MD5 |
