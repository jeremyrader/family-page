<template>

</template>

<script lang="ts">
import Vue from 'vue'

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

export default Vue.extend({
  mounted: function() {

    window.netlifyIdentity.on('init', (user: User) => {
      
    })
    window.netlifyIdentity.on('login', (user: User) => {
      window.netlifyIdentity.close()
        this.$router.push({
          path: '/home'
        })
    })

    const user = window.netlifyIdentity.currentUser()


    if (!user) {
      window.netlifyIdentity.open()
    }
    else {
      this.$router.push({
        path: '/home'
      })
    }
    
  }
})
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
