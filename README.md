<p align="center">
  <img src="logo_f4cvq.png" alt="F4CVQ" width="220">
</p>

<h1 align="center">ICOM IC-USB UTILITY</h1>

<p align="center">
  <b>Sauvegarde, visualisation et réglages des transceivers Icom par USB (CI-V)</b><br>
  Windows · un seul fichier .exe · rien à installer
</p>

---

## Présentation

**ICOM IC-USB UTILITY** lit par le câble USB tous les réglages des menus d'un poste Icom, les
enregistre sur le PC, les affiche comme sur l'écran du poste, permet de les modifier et de les
**réimplanter** plus tard dans le poste, par exemple après une réinitialisation, une mise à jour du firmware ou
une fausse manœuvre.

![Postes pris en charge](presentation/ICOM_IC-USB_Utility_tableau.png)

## Fonctions

- 🔍 **Détection automatique** du poste : modèle, adresse CI-V et vitesse, grâce à la commande CI-V `19 00`.
- 💾 **Sauvegarde en un clic** des menus, des mémoires du keyer CW et des canaux mémoire, dans un
  fichier daté au nom du modèle (`Documents\ICOM IC-USB Sauvegardes`).
- ↺ **Réimplantation vérifiée** d'une sauvegarde :
  1. copie automatique de l'état actuel du poste (« avant restauration ») ;
  2. liste des différences, chacune pouvant être décochée ;
  3. écriture puis **relecture** de chaque réglage.

  La date et l'heure sont exclues par défaut.
- 🖥️ **Écran façon poste** : grille MENU, pages de 4 lignes, barres de niveau, boutons ▲ ▼ ↩.
  L'arborescence est construite pour chaque modèle d'après son guide CI-V Icom.
- ✏️ **Modification sur le PC**, dans le tableau ou sur l'écran du poste. Les valeurs modifiées
  s'affichent en orange. À l'enregistrement, les anciens réglages sont conservés dans un CSV
  et les nouveaux dans une sauvegarde `…_modifie.json`.
- 🔒 **Sécurité** : le programme refuse d'écrire si le poste branché n'est pas le modèle de la sauvegarde.
- 🕐 **Mise à l'heure** de l'horloge du poste sur celle du PC, au passage de la minute pleine
  (heure locale ou UTC, décalage UTC en option).
- 📄 **Export CSV** pour Excel.

## Postes pris en charge

| Poste | Menus lus (en clair / brut¹) | Canaux mémoire | Keyer CW | Mise à l'heure | Affichage | Remarques |
|---|---|---|:-:|:-:|---|---|
| **IC-7300** | 193 (144 / 49) | 101 | ✅ | ✅ | écran du poste | **testé sur un vrai poste** |
| **IC-7300MK2** | 270 (183 / 87) | 101 | ✅ | ✅ | écran du poste | |
| **IC-705** | 383 (286 / 97) | 10 004 | ✅ | ✅ | écran du poste | lecture des mémoires ~3-4 min |
| **IC-905** | 353 (300 / 53) | 10 012 | ✅ | ✅ | écran du poste | lecture des mémoires ~3-4 min |
| **IC-7610** | 295 (218 / 77) | 101 | ✅ | ✅ | écran du poste | |
| **IC-9700** | 350 (308 / 42) | 321 | ✅ | ✅ | écran du poste | mémoires satellite non incluses |
| **IC-7760** | 368 (265 / 103) | 101 | ✅ | ✅ | écran du poste | |
| **IC-7851 / IC-7850** | 316 (237 / 79) | 101 | ✅ | ✅ | liste | |
| **IC-7100** | 217 (199 / 18) | 545 | ✅ | ✅ | liste | |
| **IC-7600** | 172 (130 / 42) | 102 | ✅ | ⚠️ | liste | heure sans décalage UTC |
| **IC-9100** | 177 (159 / 18) | 424 | ✅ | ❌ | liste | heure non décrite dans le manuel |
| **IC-7410** | 90 (80 / 10) | 101 | ✅ | ❌ | liste | pas d'horloge réglable par CI-V |
| **IC-7200** | 56 (56 / 0) | 201 | ✅ | ❌ | liste | menus par la commande `1A 03` |
| **IC-R8600** (récepteur) | 169 (153 / 16) | 10 200 | — | ❌ | liste | lecture des mémoires ~3-4 min |
| **IC-7700** | brut | ❌ | ✅ | ❌ | numéros | pas d'USB CI-V : câble USB/CI-V (CT-17…) |
| **IC-7800** | brut | ❌ | ✅ | ❌ | numéros | pas d'USB CI-V : câble USB/CI-V (CT-17…) |
| **IC-R15** (récepteur) | brut | ❌ | — | ❌ | numéros | adresse et guide CI-V inconnus |

¹ *Brut* : réglages complexes (filtres, bords du scope, adresses réseau, décalages…). Ils sont
**sauvegardés et restaurés**, mais affichés en hexadécimal et non modifiables depuis le PC.

**Non pris en charge** : ID-52E, ID-50E et ID-5100E. Leurs menus ne sont pas accessibles par CI-V ;
il faut utiliser le logiciel de clonage Icom (CS-52, CS-50 ou CS-5100).

> ⚠️ Seul l'**IC-7300** a été testé sur un vrai poste. Les autres modèles ont été testés avec des postes
> simulés, construits à partir des guides CI-V officiels Icom. Les retours d'essais sont les bienvenus
> (onglet *Issues*).

## Installation et utilisation

1. Télécharger **`ICOM_IC-USB_Utility.exe`** (page *Releases*) et le copier où vous voulez.
2. Brancher le poste en USB. Le pilote USB Icom doit être installé, il est disponible sur le site Icom.
3. **Fermer** JTDX, WSJT-X, le logbook et rigctld : le port COM ne peut servir qu'à un programme à la fois.
4. Lancer l'exe, choisir le port COM, puis cliquer sur **🔍 Détecter le poste**.
5. Cliquer sur **💾 Sauvegarder le poste maintenant**.

Au premier lancement, Windows SmartScreen peut afficher « Windows a protégé votre ordinateur », car
l'exe n'est pas signé. Il faut cliquer sur *Informations complémentaires* puis *Exécuter quand même*.
---

<p align="center">73 de <b>F4CVQ</b></p>
