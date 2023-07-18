## Authentication

Authentication in Spiral Framework is managed through a set of components that authorize users via temporary or permanent tokens from different sources. It safely manages the user context and does not enforce any specific User entity interface, allowing for flexibility in application design. The authentication extension creates an IoC scope for `Spiral\Auth\AuthContextInterface` which points to the currently authorized actor (User, API Client). The actor is fetched from `Spiral\Auth\ActorProviderInterface` using `Spiral\Auth\TokenInterface`. The token is managed by `Spiral\Auth\TokenStorageInterface` and always includes the payload (for example `["userID" => $id]`, LDAP creds, etc.). The token payload is used to find the current application user via `Spiral\Auth\ActorProviderInterface`.

### Links and materials to read more:
1. [Authentication Documentation](https://spiral.dev/docs/security-authentication/current/en)
