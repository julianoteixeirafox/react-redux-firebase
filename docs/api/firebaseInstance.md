<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [set][1]
-   [setWithMeta][2]
-   [push][3]
-   [pushWithMeta][4]
-   [update][5]
-   [updateWithMeta][6]
-   [remove][7]
-   [uniqueSet][8]
-   [uploadFile][9]
-   [uploadFiles][10]
-   [deleteFile][11]
-   [watchEvent][12]
-   [unWatchEvent][13]
-   [promiseEvents][14]
-   [login][15]
-   [logout][16]
-   [createUser][17]
-   [resetPassword][18]
-   [confirmPasswordReset][19]
-   [verifyPasswordResetCode][20]
-   [updateProfile][21]
-   [updateAuth][22]
-   [updateEmail][23]
-   [reloadAuth][24]
-   [linkWithCredential][25]
-   [signInWithPhoneNumber][26]
-   [ref][27]
-   [database][28]
-   [storage][29]
-   [auth][30]

## set

Sets data to Firebase.

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to write to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

**Examples**

_Basic_

```javascript
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { firebaseConnect } from 'react-redux-firebase'
const Example = ({ firebase: { set } }) => (
  <button onClick={() => set('some/path', { here: 'is a value' })}>
    Set To Firebase
  </button>
)
export default firebaseConnect()(Example)
```

Returns **[Promise][36]** Containing reference snapshot

## setWithMeta

Sets data to Firebase along with meta data. Currently,
this includes createdAt and createdBy. _Warning_ using this function
may have unintented consequences (setting createdAt even if data already
exists)

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to write to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

Returns **[Promise][36]** Containing reference snapshot

## push

Pushes data to Firebase.

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to push
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to push to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

**Examples**

_Basic_

```javascript
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { firebaseConnect } from 'react-redux-firebase'
const Example = ({ firebase: { push } }) => (
  <button onClick={() => push('some/path', true)}>
    Push To Firebase
  </button>
)
export default firebaseConnect()(Example)
```

Returns **[Promise][36]** Containing reference snapshot

## pushWithMeta

Pushes data to Firebase along with meta data. Currently,
this includes createdAt and createdBy.

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to write to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

Returns **[Promise][36]** Containing reference snapshot

## update

Updates data on Firebase and sends new data.

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to update
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to update to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

**Examples**

_Basic_

```javascript
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { firebaseConnect } from 'react-redux-firebase'
const Example = ({ firebase: { update } }) => (
  <button onClick={() => update('some/path', { here: 'is a value' })}>
    Update To Firebase
  </button>
)
export default firebaseConnect()(Example)
```

Returns **[Promise][36]** Containing reference snapshot

## updateWithMeta

Updates data on Firebase along with meta. _Warning_
using this function may have unintented consequences (setting
createdAt even if data already exists)

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to update
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to update to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

Returns **[Promise][36]** Containing reference snapshot

## remove

Removes data from Firebase at a given path. **NOTE** A
seperate action is not dispatched unless `dispatchRemoveAction: true` is
provided to config on store creation. That means that a listener must
be attached in order for state to be updated when calling remove.

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to remove
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)
-   `options`  

**Examples**

_Basic_

```javascript
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { firebaseConnect } from 'react-redux-firebase'
const Example = ({ firebase: { remove } }) => (
  <button onClick={() => remove('some/path')}>
    Remove From Firebase
  </button>
)
export default firebaseConnect()(Example)
```

Returns **[Promise][36]** Containing reference snapshot

## uniqueSet

Sets data to Firebase only if the path does not already
exist, otherwise it rejects. Internally uses a Firebase transaction to
prevent a race condition between seperate clients calling uniqueSet.

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `value` **([Object][32] \| [String][31] \| [Boolean][33] \| [Number][34])** Value to write to Firebase
-   `onComplete` **[Function][35]** Function to run on complete (`not required`)

**Examples**

_Basic_

```javascript
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { firebaseConnect } from 'react-redux-firebase'
const Example = ({ firebase: { uniqueSet } }) => (
  <button onClick={() => uniqueSet('some/unique/path', true)}>
    Unique Set To Firebase
  </button>
)
export default firebaseConnect()(Example)
```

Returns **[Promise][36]** Containing reference snapshot

## uploadFile

Upload a file to Firebase Storage with the option to store
its metadata in Firebase Database

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `file` **File** File object to upload (usually first element from
    array output of select-file or a drag/drop `onDrop`)
-   `dbPath` **[String][31]** Database path to place uploaded file metadata
-   `options` **[Object][32]** Options
    -   `options.name` **[String][31]** Name of the file

Returns **[Promise][36]** Containing the File object

## uploadFiles

Upload multiple files to Firebase Storage with the option
to store their metadata in Firebase Database

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `files` **[Array][37]** Array of File objects to upload (usually from
    a select-file or a drag/drop `onDrop`)
-   `dbPath` **[String][31]** Database path to place uploaded files metadata.
-   `options` **[Object][32]** Options
    -   `options.name` **[String][31]** Name of the file

Returns **[Promise][36]** Containing an array of File objects

## deleteFile

Delete a file from Firebase Storage with the option to
remove its metadata in Firebase Database

**Parameters**

-   `path` **[String][31]** Path to location on Firebase which to set
-   `dbPath` **[String][31]** Database path to place uploaded file metadata

Returns **[Promise][36]** Containing the File object

## watchEvent

Watch event. **Note:** this method is used internally
so examples have not yet been created, and it may not work as expected.

**Parameters**

-   `type` **[String][31]** Type of watch event
-   `path` **[String][31]** Path to location on Firebase which to set listener
-   `storeAs` **[String][31]** Name of listener results within redux store
-   `options` **[Object][32]** Event options object (optional, default `{}`)
    -   `options.queryParams` **[Array][37]** List of parameters for the query
    -   `options.queryId` **[String][31]** id of the query

Returns **[Promise][36]** 

## unWatchEvent

Unset a listener watch event. **Note:** this method is used
internally so examples have not yet been created, and it may not work
as expected.

**Parameters**

-   `type` **[String][31]** Type of watch event
-   `path` **[String][31]** Path to location on Firebase which to unset listener
-   `queryId` **[String][31]** Id of the listener
-   `options` **[Object][32]** Event options object (optional, default `{}`)

Returns **[Promise][36]** 

## promiseEvents

Similar to the firebaseConnect Higher Order Component but
presented as a function (not a React Component). Useful for populating
your redux state without React, e.g., for server side rendering. Only
`once` type should be used as other query types such as `value` do not
return a Promise.

**Parameters**

-   `watchArray` **[Array][37]** Array of objects or strings for paths to sync
    from Firebase. Can also be a function that returns the array. The function
    is passed the props object specified as the next parameter.
-   `options` **[Object][32]** The options object that you would like to pass to
    your watchArray generating function.

Returns **[Promise][36]** 

## login

Logs user into Firebase. For examples, visit the
[auth section][38]

**Parameters**

-   `credentials` **[Object][32]** Credentials for authenticating
    -   `credentials.provider` **[String][31]** External provider (google |
        facebook | twitter)
    -   `credentials.type` **[String][31]** Type of external authentication
        (popup | redirect) (only used with provider)
    -   `credentials.email` **[String][31]** Credentials for authenticating
    -   `credentials.password` **[String][31]** Credentials for authenticating (only used with email)

Returns **[Promise][36]** Containing user's auth data

## logout

Logs user out of Firebase and empties firebase state from
redux store

Returns **[Promise][36]** 

## createUser

Creates a new user in Firebase authentication. If
`userProfile` config option is set, user profiles will be set to this
location.

**Parameters**

-   `credentials` **[Object][32]** Credentials for authenticating
    -   `credentials.email` **[String][31]** Credentials for authenticating
    -   `credentials.password` **[String][31]** Credentials for authenticating (only used with email)
-   `profile` **[Object][32]** Data to include within new user profile

Returns **[Promise][36]** Containing user's auth data

## resetPassword

Sends password reset email

**Parameters**

-   `credentials` **[Object][32]** Credentials for authenticating
    -   `credentials.email` **[String][31]** Credentials for authenticating

Returns **[Promise][36]** 

## confirmPasswordReset

Confirm that a user's password has been reset

**Parameters**

-   `code` **[String][31]** Password reset code to verify
-   `password` **[String][31]** New Password to confirm reset to

Returns **[Promise][36]** 

## verifyPasswordResetCode

Verify that a password reset code from a password reset
email is valid

**Parameters**

-   `code` **[String][31]** Password reset code to verify

Returns **[Promise][36]** Containing user auth info

## updateProfile

Update user profile on Firebase Real Time Database or
Firestore (if `useFirestoreForProfile: true` config passed to
reactReduxFirebase). Real Time Database update uses `update` method
internally while updating profile on Firestore uses `set` with

**Parameters**

-   `profileUpdate` **[Object][32]** Profile data to place in new profile
-   `options` **[Object][32]** Options object (used to change how profile
    update occurs)
    -   `options.useSet` **[Boolean][33]** Use set with merge instead of
        update. Setting to `false` uses update (can cause issue of profile document
        does not exist). Note: Only used when updating profile on Firestore (optional, default `true`)
    -   `options.merge` **[Boolean][33]** Whether or not to use merge when
        setting profile. Note: Only used when updating profile on Firestore (optional, default `true`)

Returns **[Promise][36]** 

## updateAuth

Update Auth Object

**Parameters**

-   `authUpdate` **[Object][32]** Update to be auth object
-   `updateInProfile` **[Boolean][33]** Update in profile

Returns **[Promise][36]** 

## updateEmail

Update user's email

**Parameters**

-   `newEmail` **[String][31]** Update to be auth object
-   `updateInProfile` **[Boolean][33]** Update in profile

Returns **[Promise][36]** 

## reloadAuth

Reload user's auth object. Must be authenticated.

Returns **[Promise][36]** 

## linkWithCredential

Links the user account with the given credentials.

**Parameters**

-   `credential` **firebase.auth.AuthCredential** The auth credential

Returns **[Promise][36]** 

## signInWithPhoneNumber

Asynchronously signs in using a phone number. This method
sends a code via SMS to the given phone number, and returns a modified
firebase.auth.ConfirmationResult. The `confirm` method
authenticates and does profile handling.

**Parameters**

-   `credential` **firebase.auth.ConfirmationResult** The auth credential

Returns **[Promise][36]** 

## ref

Firebase ref function

Returns **firebase.database.Reference** 

## database

Firebase database service instance including all Firebase storage methods

Returns **firebase.database.Database** Firebase database service

## storage

Firebase storage service instance including all Firebase storage methods

Returns **firebase.database.Storage** Firebase storage service

## auth

Firebase auth service instance including all Firebase auth methods

Returns **firebase.database.Auth** 

[1]: #set

[2]: #setwithmeta

[3]: #push

[4]: #pushwithmeta

[5]: #update

[6]: #updatewithmeta

[7]: #remove

[8]: #uniqueset

[9]: #uploadfile

[10]: #uploadfiles

[11]: #deletefile

[12]: #watchevent

[13]: #unwatchevent

[14]: #promiseevents

[15]: #login

[16]: #logout

[17]: #createuser

[18]: #resetpassword

[19]: #confirmpasswordreset

[20]: #verifypasswordresetcode

[21]: #updateprofile

[22]: #updateauth

[23]: #updateemail

[24]: #reloadauth

[25]: #linkwithcredential

[26]: #signinwithphonenumber

[27]: #ref

[28]: #database

[29]: #storage

[30]: #auth

[31]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

[32]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[33]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean

[34]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number

[35]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function

[36]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise

[37]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array

[38]: /docs/auth.md