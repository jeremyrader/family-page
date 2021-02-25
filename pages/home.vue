<template>
<div>
  <Nav />

  <header class="bg-white shadow">
    <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
      <h1 class="text-3xl font-bold text-gray-900">
        Feed
      </h1>
    </div>
  </header>
  <main>
    <div class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
      <!-- Replace with your content -->
      <div class="min-h-screen flex items-center justify-center bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
            <div id="logged-in" class="max-w-md w-full space-y-8">
            <img src="https://73v3u36iopz178i0z3a33g7d-wpengine.netdna-ssl.com/wp-content/uploads/2019/03/Lucky-Litmos-Lenny_Day-768x461.png" />
            <p>Hi everyone!</p>

            <p>I bet you thought you were going to find a video of me saying it, right? Nope! That's only on Christmas!</p>
            
            <p>
                I thought it'd be fun to setup a family page. Quite a few of us aren't on Facebook anymore so
                I thought it'd be nice to have a place to share updates, photos, and Nicholas Cage memes with each other.
                There's quite a bit of work to do to make that happen so I thought we could put it to a vote what I
                should work on first.
            </p>
            <!---
            <p class="font-bold">Things to work on next:</p>
            <form name="requests" method="POST" data-netlify="true">
                <div class="mb-2">
                    <input type="radio" id="posts" name="request" value="Posts">
                    <label for="posts">Post updates (just text for now)</label>
                </div>
                <div class="mb-2">
                    <input type="radio" id="photos" name="request" value="Photos">
                    <label for="photos">Share family photos</label>
                </div>
                <div class="mb-2">
                    <input type="radio" id="memes" name="request" value="Memes">
                    <label for="memes">Post dumb memes</label>
                </div>
                <div class="mb-5">
                    <input type="radio" id="chat" name="request" value="Chat">
                    <label for="chat">Chat room</label>
                </div>
                <div class="mb-7">
                    <input class="border" type="text" name="other" placeholder="Other" autocomplete="off">
                </div>
                <div class="mb-2">
                    <input name="submit" id="submit" class="px-8 py-3 border border-transparent rounded-md text-white cursor-pointer bg-blue-600 hover:bg-blue-700" type="submit"></button>
                </div>
            </form>
            --->
            </div>
        </div>
      <!-- /End replace -->
    </div>
  </main>
</div>
<!---
  
  --->
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
