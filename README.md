Purpose: user sign-in to ARIES (an AI-assisted IT operations application hosted in AEP's AWS account, at https://aries.cloud.aep.com). AEP users sign in with their work accounts; ARIES validates the sign-in token and uses the user's group membership to apply their role (for example Administrator or Engineer).

Configuration:

Platform: Single-page application, redirect URI https://aries.cloud.aep.com/
Supported account types: this organisation only (single tenant)
Token claims: group membership (security groups), or app roles for Administrator / Engineer / Viewer, whichever your team prefers
A client secret for the ARIES backend (stored in AWS Secrets Manager)

Permissions (Microsoft Graph, delegated): openid, profile, email, offline_access, User.Read. These are basic sign-in permissions and don't need admin consent beyond the standard user consent.

Optional (only if email notifications are wanted): Mail.Send (application), restricted to a dedicated ARIES mailbox with an application access policy. We can skip this for the initial setup.

Please share with us: the application (client) ID, the tenant ID, and the client secret (through a secure channel), and the AEP groups that should have access.
