![logo](../public/ts.png){width="30", loading=lazy, align=right}
![logo](../public/esm.png){width="30", loading=lazy, align=right}
# **[Basalt Auth](https://www.npmjs.com/package/@basalt-lab/basalt-auth)**

!!! warning

    Basalt est actuellement à ses débuts, s'il vous plaît soyez indulgent et n'hesitez pas à faire un retour sur votre expérience par mail : [basalt-lab@proton.me](mailto:basalt-lab@proton.me) ou par Discord `necrelox`.

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

**Basalt Auth** est conçu pour être utilisé dans un context backend.
Il n'a pas de dépendances, ce qui le rend facile à intégrer dans n'importe quel projet Node.js.


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
