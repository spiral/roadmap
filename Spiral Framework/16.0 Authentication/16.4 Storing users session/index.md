### Storing users session

Storing user sessions in Spiral Framework is managed through the `SessionInterface`. This interface provides methods to control the session lifecycle, including resuming, committing, aborting, getting the session ID, destroying, and regenerating the ID of a session.

Sessions in Spiral are stored in the file system in the `runtime/session` directory by default. If your application will be load balanced across multiple web servers, you should choose a centralized store that all servers can access, such as Redis.

### Links and materials to read more:
1. [Basics - Session Guide](https://spiral.dev/docs/basics-session/current/en)
