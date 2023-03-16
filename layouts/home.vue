<template>
  <v-app>
    <v-app-bar app dark dense>
      <v-spacer />

      <v-app-bar-title>
        <v-hover v-slot="{ hover }">
          <nuxt-link to="/" class="mr-2 no-underline " :class="{ 'pink--text text--accent-2': hover }">
            <span>
              Home
            </span>
          </nuxt-link>
        </v-hover>
        <span>|</span>
        <v-hover v-slot="{ hover }">
          <nuxt-link to="/" class="ml-2 no-underline " :class="{ 'pink--text text--accent-2 ': hover }">
            Test Api
          </nuxt-link>
        </v-hover>
      </v-app-bar-title>
      <v-spacer />
    </v-app-bar>
    <nuxt />
  </v-app>
</template>
<style lang="scss">
 .no-underline {
  text-decoration: none;
  &:hover {
    text-decoration: none;
  }
}
</style>
