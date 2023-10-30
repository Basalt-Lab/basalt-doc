# **Contributing to Basalt Auth**

## **Introduction**

**Basalt Auth** is a part of the Basalt ecosystem, offering a convenient method for managing authentication through tokens.

At the core of this module is the BasaltToken class, whose primary function is the generation and verification of tokens.

What sets Basalt Auth apart is its key pair system: each token is associated with its own pair, a feature that distinguishes it from standard [JWTs](https://jwt.io/).

## **Why Basalt Auth?**

The goal behind **Basalt Auth** was to develop a custom authentication system that draws inspiration from the structure of [JWTs](https://jwt.io/), but with a distinct twist: each token has its own key pair.

This approach isn't necessarily superior to conventional methods; it's more of a personal exploration in authentication system design.

It's important to note that security is an evolving discipline, and the merits of this structure compared to established standards haven't been fully assessed.

!!! warning

    **Basalt Auth** isn't aiming to replace existing solutions, but rather to offer an alternative for specific use cases.

## **Key Features**

Beyond its token management method, **Basalt Auth** is fairly simple, with a few key features:

- **Unique key pairs per token:** This feature can offer interesting aspects in terms of session management.
- **Generation and verification process:** These functions follow a simplified logic, making their use quite straightforward.

It's not about claiming to compete or replace existing solutions, but rather about offering an alternative for specific scenarios.

## **Versatility and Compatibility**

**Basalt Auth** is designed to be used in various contexts, whether backend or frontend.
Its independent nature makes it easy to incorporate into different projects, without requiring specific external components.

## **Conclusion**

**Basalt Auth** offers a different approach to tokenized authentication.
Without seeking to revolutionize the field, this module offers additional features that may be of interest for specific use cases.

Its journey will be dictated by feedback and emerging needs, and it remains a tool to consider for projects looking for an authentication method slightly different from the norm.
