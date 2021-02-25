<template>
  <div>
    <Nav />
    <div class="min-h-screen flex items-center justify-center bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
      <iframe src="https://docs.google.com/document/d/1d3ZRPADVxah3MIOPP7nNAL54aMWWCN8_Q8UWvOiYjUI/edit?usp=sharing" height="1000" width="960"></iframe>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Nav from 'components/Nav.vue'

interface netlifyIdentity {
  open: Function,
  close: Function,
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
  window.netlifyIdentity.on('login', (user: User) => {
    window.netlifyIdentity.close();
  })
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
