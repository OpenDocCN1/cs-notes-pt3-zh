# # (5) Revoking Authorization in SQL

+   - The revoke statement is used to revoke authorization.

REVOKE<privilege list> ON <relation name or view name> FROM <user list> [ restrict | cascade ]

+   - Example:

revoke select on branch from U₁, U₃ cascade;

+   - Revocation of a privilege from a user may cause other users also to lose that privilege; referred to as cascading of the revoke.

+   - We can prevent cascading by specifying restrict:

revoke select on branch from U₁, U₃ restrict;

With restrict, the revoke command fails if cascading revokes are required.