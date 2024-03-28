# **[Basalt Auth](https://www.npmjs.com/package/@basalt-lab/basalt-auth)**

!!! warning

    Basalt est actuellement à ses débuts, s'il vous plaît soyez indulgent et n'hesitez pas à faire un retour sur votre expérience par mail : [basalt-lab@proton.me](mailto:basalt-lab@proton.me).

## **Introduction**

**Basalt Auth** est un module d'authentification basé sur des tokens, conçu pour être simple à utiliser.

La particularité de **Basalt Auth** réside dans son système de paire de clés : chaque token est associé à sa propre paire, une caractéristique qui le différencie des [JWT](https://jwt.io/) standards.

C'est un mélange entre de l'OAT et des JWT, les tokens ainsi que les clefs publiques doivent être stockées côté serveur pour être vérifiées.  
Pour cela je conseille l'utilisation d'un store comme [Redis](https://redis.io/) ou [DragonFly](https://www.dragonflydb.io/)

## **Pourquoi Basalt Auth ?**

L'objectif derrière **Basalt Auth** était de développer un système d'authentification personnalisé qui s'inspire de la structure des [JWT](https://jwt.io/), mais avec quelques subtilités.

Cette approche n'est pas nécessairement supérieure aux méthodes conventionnelles, c'est plutôt une exploration personnelle dans la conception de systèmes d'authentification.

Il est important de noter que la sécurité est une discipline évolutive, et les mérites de cette structure par rapport aux standards établis n'ont pas été pleinement évalués.

!!! warning

    **Basalt Auth** ne cherche pas à remplacer les solutions existantes, mais plutôt à offrir une alternative pour des cas d'utilisation spécifiques.


## **Polyvalence et Compatibilité**

**Basalt Auth** est conçu pour être utilisé dans des contextes variés, que ce soit backend ou frontend.  
Sa nature indépendante facilite son incorporation dans différents projets, sans nécessiter de composants externes spécifiques.
