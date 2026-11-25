Name: ARIES-AEP, for user sign-in to ARIES at https://aries.cloud.aep.com (single tenant, SPA redirect URI https://aries.cloud.aep.com/).
Expose an API: Application ID URI api://<client ID>, with a delegated scope User.Read (admin consent granted); access token version 2 in the manifest.
App roles (exact values): App.Admin, App.Manager, App.Engineer, App.Practitioner, App.User, assigned to users or groups under Enterprise applications.
Permissions: Microsoft Graph delegated openid, profile, email, offline_access, User.Read. Please share the client ID, the tenant ID and the client secret (securely), plus the role assignments.
