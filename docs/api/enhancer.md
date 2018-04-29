<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [reactReduxFirebase][1]

## reactReduxFirebase

Redux store enhancer that accepts configuration options and adds
store.firebase and store.firebaseAuth. Enhancers are most commonly placed in redux's `compose` call
along side applyMiddleware.

**Parameters**

-   `firebaseInstance` **[Object][2]** Initiated firebase instance (can also
    be library following Firebase JS API such as `react-native-firebase`)
-   `config` **[Object][2]** Containing react-redux-firebase specific configuration
    -   `config.userProfile` **[String][3]** Location on firebase to store user profiles
    -   `config.enableLogging` **[Boolean][4]** Whether or not to enable Firebase database logging.
        **Note**: Only works if instance has enableLogging function.
    -   `config.profileFactory` **[Function][5]** Factory for modifying how user profile is saved.
    -   `config.presence` **[Boolean][4]** Location on Firebase to store currently
        online users list. Often set to `'presence'` or `'onlineUsers'`.
    -   `config.sessions` **[Boolean][4]** Location on Firebase where user
        sessions are stored (only if presense is set). Often set to `'sessions'` or `'onlineUsers'`.
    -   `config.updateProfileOnLogin` **[Boolean][4]** Whether or not to update
        profile when logging in. (default: `true`)
    -   `config.resetBeforeLogin` **[Boolean][4]** Whether or not to empty profile
        and auth state on login
    -   `config.perserveOnLogout` **([Object][2] \| [Array][6])** Data parameters to perserve
        when logging out. If Array is passed, each item represents keys
        within `state.firebase.data` to preserve. If an object is passed,
        keys associate with slices of state to preserve, and the values can be either
        an `Array` or a `Function` (argument pattern: `(currentState, nextState)`).
        If passing an array of keys (i.e. `{ auth: ['key1', 'key2'] }`) - those keys
        (`'key1'` and `'key2'`) are preserved from that slice of state (`auth`). If
        passing a function (i.e.
        `{ auth: (currentAuthState, nextAuthState) => ({}) }`),
        whatever is returned from the function is set to that slice of state (`auth`).
        associate with which keys to preserve form that section of state.
        (default: `null`)
    -   `config.preserveOnEmptyAuthChange` **[Object][2]** `null` Data parameters to
        preserve when logging out. Keys associate with parts of state to preserve,
        and the values are Arrays contain keys for keys within that slice of state
        to preserve.
    -   `config.useFirestoreForProfile` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** `false` Write profile
        data to Firestore instead of Real Time Database.
    -   `config.useFirestoreForStorageMeta` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** `false` Write storage
        file metadata to Firestore instead of Real Time Database.
    -   `config.enableRedirectHandling` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Whether or not to enable
        auth redirect handling listener. (default: `true`)
    -   `config.onAuthStateChanged` **[Function][5]** Function run when auth state
        changes. Argument Pattern: `(authData, firebase, dispatch)`
    -   `config.onRedirectResult` **[Function][5]** Function run when redirect
        result is returned. Argument Pattern: `(authData, firebase, dispatch)`
    -   `config.customAuthParameters` **[Object][2]** Object for setting which
        customAuthParameters are passed to external auth providers.
    -   `config.profileFactory` **[Function][5]** Factory for modifying how user profile is saved.
    -   `config.fileMetadataFactory` **[Function][5]** Factory for modifying
        how file meta data is written during file uploads
    -   `config.profileParamsToPopulate` **([Array][6] \| [String][3])** Parameters within
        profile object to populate. As of `v2.0.0` data is only loaded for population, not actually automatically populated
        (allows access to both unpopulated and populated profile data).
    -   `config.autoPopulateProfile` **[Boolean][4]** **NOTE**: Now enabled for v2.0.0. Whether or not to
        automatically populate profile with data loaded through profileParamsToPopulate config. (default: `true`)
    -   `config.setProfilePopulateResults` **[Boolean][4]** Whether or not to
        call SET actions for data that results from populating profile to redux under
        the data path. For example role parameter on profile populated from 'roles'
        root. True will call SET_PROFILE as well as a SET action with the role that
        is loaded (places it in data/roles). (default: `false`)

**Examples**

_Setup_

```javascript
import { createStore, compose } from 'redux'
import { reactReduxFirebase } from 'react-redux-firebase'
import * as firebase from 'firebase'

// React Redux Firebase Config
const config = {
  userProfile: 'users', // saves user profiles to '/users' on Firebase
  // here is where you place other config options
}

// initialize script from Firebase page
const fbConfg = {} // firebase config object
firebase.initializeApp(fbConfig)

// Add react-redux-firebase to compose
// Note: In full projects this will often be within createStore.js or store.js
const createStoreWithFirebase = compose(
 reactReduxFirebase(firebase, config),
)(createStore)

// Use Function later to create store
const store = createStoreWithFirebase(rootReducer, initialState)
```

Returns **[Function][5]** That accepts a component and returns a Component which
wraps the provided component (higher order component).

[1]: #reactreduxfirebase

[2]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[3]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

[4]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean

[5]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function

[6]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array