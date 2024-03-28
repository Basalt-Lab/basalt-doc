# **[Basalt Auth](https://www.npmjs.com/package/@basalt-lab/basalt-auth)**

!!! warning

    Basalt is currently in its early stages, so please be patient and feel free to provide feedback on your experience via email: [basalt-lab@proton.me](mailto:basalt-lab@proton.me).

## **Introduction**

**Basalt Auth** is a token-based authentication module designed to be easy to use.

The uniqueness of **Basalt Auth** lies in its key pair system: each token is associated with its own pair, a feature that sets it apart from standard [JWT](https://jwt.io/) tokens.

It is a mix of OAT and JWT, where both tokens and public keys need to be stored on the server side for verification.  
For this purpose, I recommend using a store like [Redis](https://redis.io/) or [DragonFly](https://www.dragonflydb.io/).

## **Why Basalt Auth?**

The goal behind **Basalt Auth** was to develop a custom authentication system that takes inspiration from the structure of [JWT](https://jwt.io/), but with some subtleties.

This approach is not necessarily superior to conventional methods; rather, it is a personal exploration in the design of authentication systems.

It is important to note that security is an evolving discipline, and the merits of this structure compared to established standards have not been fully evaluated.

!!! warning

    **Basalt Auth** does not seek to replace existing solutions, but rather to offer an alternative for specific use cases.

## **Versatility and Compatibility**

**Basalt Auth** is designed to be used in various contexts, whether it's backend or frontend.  
Its independent nature makes it easy to incorporate into different projects without requiring specific external components.
