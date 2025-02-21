![logo_esm](../public/esm.png){width="30", loading=lazy, align=right}
![logo_ts](../public/ts.png){width="30", loading=lazy, align=right}
![logo_bun](../public/bun.svg){width="40", loading=lazy, align=right}

# **[Basalt Logger](https://www.npmjs.com/package/@basalt-lab/basalt-logger)**

!!! warning

    Basalt est mon premier petit projet que je publie. S'il vous plaît, soyez indulgent et n'hésitez pas à me faire un retour sur votre expérience : [basalt-lab@proton.me](mailto:basalt-lab@proton.me) ou via Discord `necrelox`.

## **🏗️ Introduction**
**Basalt Logger** est un package de logging flexible et non bloquant.  
Il offre la possibilité d'implémenter plusieurs stratégies de redirection des logs et permet de sélectionner une ou plusieurs stratégies selon vos besoins.

**Basalt Logger** s'adapte parfaitement à tout projet nécessitant une journalisation détaillée, personnalisable et performante. Sa conception modulaire en fait un outil idéal pour gérer efficacement les logs de votre application.

## **❓ Pourquoi Basalt Logger ?**

Le choix de **Basalt Logger** repose sur plusieurs avantages clés :

- **Performance et Légèreté** : Zéro dépendance externe et une empreinte mémoire minimale
- **Simplicité** : API intuitive et documentation claire pour une prise en main rapide
- **Flexibilité** : Architecture modulaire permettant l'ajout de stratégies de logging personnalisées
- **Non-Bloquant** : Conçu pour ne pas impacter les performances de votre application
- **Polyvalence** : S'adapte à tous les environnements (console, fichiers, services externes)
- **Extensibilité** : Créez vos propres stratégies de logging selon vos besoins spécifiques

## 📦 Informations du package

Les packages Basalt sont disponibles en deux versions :

- **Stable** : Version par défaut, recommandée pour la production (`@basalt-lab/basalt-logger`)
- **Canary** : Version de développement la plus récente, avec les dernières fonctionnalités (`@basalt-lab/basalt-logger@canary`)

Pour installer une version spécifique, utilisez les tags correspondants lors de l'installation.

| Version | Unpacked Size | Minified Gzipped |
|---------|--------------|------------------|
| [![NPM Latest version](https://img.shields.io/npm/v/@basalt-lab/basalt-logger.svg?style=for-the-badge)](https://www.npmjs.com/package/@basalt-lab/basalt-logger/v/latest) | ![NPM Unpacked Size](https://img.shields.io/npm/unpacked-size/%40basalt-lab%2Fbasalt-logger?style=for-the-badge&label=Unpacked%20Size) | ![NPM Package minimized gzipped size](https://img.shields.io/bundlejs/size/%40basalt-lab%2Fbasalt-logger?style=for-the-badge&label=Minified%20Gzipped%20Size) |
| [![NPM canary version](https://img.shields.io/npm/v/@basalt-lab/basalt-logger/canary.svg?style=for-the-badge&color=darkcyan)](https://www.npmjs.com/package/@basalt-lab/basalt-logger/v/canary) | ![NPM Unpacked Size (Canary)](https://img.shields.io/npm/unpacked-size/%40basalt-lab%2Fbasalt-logger/canary?style=for-the-badge&label=Unpacked%20Size%20(Canary)&color=darkcyan) | - |

## **⚡ Installation**
Intégrer **Basalt Logger** dans votre projet est un jeu d'enfant.

Package : [@basalt-lab/basalt-logger](https://www.npmjs.com/package/@basalt-lab/basalt-logger)

Suivez ces étapes pour l'ajouter à votre projet :

Bun:
```bash
bun add @basalt-lab/basalt-logger
```
Or canary version
```bash
bun add @basalt-lab/basalt-logger@canary
```

<!-- termynal -->

```bash
$ bun add @basalt-lab/basalt-logger
---> 100%
installed @basalt-lab/basalt-logger@[version]
```

Vous êtes prêt à commencer ! Bon développement 🚀

<script data-name="BMC-Widget"
    data-cfasync="false"
    src="https://cdnjs.buymeacoffee.com/1.0.0/widget.prod.min.js"
    data-id="necrelox"
    data-description="Support me on Buy me a coffee!"
    data-message="Merci de votre visite!"
    data-color="#5F7FFF"
    data-position="Right"
    data-x_margin="18"
    data-y_margin="22" />
