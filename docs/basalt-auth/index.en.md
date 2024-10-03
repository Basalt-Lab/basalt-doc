![logo](../public/ts.png){width="30", loading=lazy, align=right}
![logo](../public/esm.png){width="30", loading=lazy, align=right}
# **[Basalt Auth](https://www.npmjs.com/package/@basalt-lab/basalt-auth)**

!!! warning

    Basalt is currently in its early stages, so please be patient and feel free to provide feedback on your experience via email: [basalt-lab@proton.me](mailto:basalt-lab@proton.me) or on Discord `necrelox`.

## **Introduction**

**Basalt Auth** is a token-based authentication module designed to be easy to use.

The uniqueness of **Basalt Auth** lies in its key pair system: each token is associated with its own pair, a feature that sets it apart from standard [JWT](https://jwt.io/) tokens.

It is a combination of OAT and JWT, where both tokens and public keys need to be stored on the server side for verification.  
For this, I recommend using a store like [Redis](https://redis.io/) or [DragonFly](https://www.dragonflydb.io/).

## **Why Basalt Auth?**

The goal behind **Basalt Auth** was to develop a custom authentication system inspired by the structure of [JWT](https://jwt.io/), but with some nuances.

This approach is not necessarily superior to conventional methods; it is rather a personal exploration in the design of authentication systems.

It is important to note that security is an evolving discipline, and the merits of this structure compared to established standards have not been fully evaluated.

!!! warning

    **Basalt Auth** does not seek to replace existing solutions, but rather to offer an alternative for specific use cases.

## **Versatility and Compatibility**

**Basalt Auth** is designed to be used in a backend context.
It has no dependencies, making it easy to integrate into any Node.js project.

<script data-name="BMC-Widget"
    data-cfasync="false"
    src="https://cdnjs.buymeacoffee.com/1.0.0/widget.prod.min.js"
    data-id="necrelox"
    data-description="Support me on Buy me a coffee!"
    data-message="Thank you for visiting!"
    data-color="#5F7FFF"
    data-position="Right"
    data-x_margin="18"
    data-y_margin="22" />

