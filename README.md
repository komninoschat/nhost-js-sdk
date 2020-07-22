# Nhost JS SDK

Nhost JS SDK to handle **Auth** and **Storage**.

## Installation

`npm install --save nhost-js-sdk`

## Setup

In ex `/src/nhost/index.js`:

```js
import nhost from "nhost-js-sdk";

const config = {
  base_url: 'https://backend-xxxx.nhost.app',
};

nhost.initializeApp(config);

const auth = nhost.auth();
const storage = nhost.storage();

export { auth, storage };
```

## Usage auth and storage across in your app

`import { auth, storage } from 'src/nhost/index.js';`

## Auth

### Register

```js
auth.register(email, password);
```

### Login

```js
auth.login(email, password);
```

### Logout

```js
auth.logout();
```

### onAuthStateChanged

```js
auth.onAuthStateChanged((logged_in) => {
  console.log("auth state changed!");
  console.log({ logged_in });
});
```

### Check if user is authenticated

```js
auth.isAuthenticated();
```

### Get JWT token

```js
auth.getJWTToken();
```

### Get JWT claim

```js
auth.getClaim("x-hasura-user-id");
```

### Activate account

```js
auth.activate(<ticket>);
```

### Change email address

Note: The user must be logged in.

```js
auth.changeEmail(new_email);
```

### Request new email change

```js
auth.changeEmailRequest(new_email);
```

### Change to requested email

```js
auth.changeEmailChange(ticket);
```

### Change password

```js
auth.changePassword(old_password, new_password);
```

### Request new password

```js
auth.changePasswordRequest(email);
```

### Change password using ticket

```js
auth.changePasswordChange(new_password, ticket);
```

### Generate MFA QR-code

Note: User must be logged in.

```js
auth.MFAGenerate();
```

### Enable MFA

```js
auth.enable(code);
```

### Disable MFA

```js
auth.enable(code);
```

### Login using TOTP

Note: `ticket` comes from the `auth.login()` response if the user has MFA enabled.

```js
auth.MFATotp(code, ticket);
```

## Storage

### Upload

```
storage.put(path, file, metadata?, onUploadProgress?);
```

### Delete

```
storage.delete(path);
```

### Get metadata

```
storage.getMetadata(path);
```
