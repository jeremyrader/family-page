<template>
  <div class="container">
    <div data-netlify-identity-menu></div>
    <div data-netlify-identity-button>Login with Netlify Identity</div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

interface netlifyIdentity {
  open: Function,
  currentUser: Function,
  on: Function
}

interface User {
  id: string
  email: string
}

declare global {
    interface Window {
        netlifyIdentity: netlifyIdentity;
    }
}

// Available after on('init') is invoked
const user = window.netlifyIdentity.currentUser()


if (!user) {
  window.netlifyIdentity.open()

  window.netlifyIdentity.on('init', (user: User) => console.log('init', user))
  window.netlifyIdentity.on('login', (user: User) => console.log('login', user))
}

export default Vue.extend({})
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
