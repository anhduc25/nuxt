<template>
  <v-container class="  set-max-width">
    <v-card md="6" class="mx-auto">
      <v-card-title>
        Sign Up Form
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field label="Username" />
          <v-text-field label="Password" type="password" />
          <v-text-field
            v-if="show"
            label="Phone Number"
          />
        </v-form>
      </v-card-text>
      <v-card-actions>
        <div>
          <span>If you don't have account, </span>
          <nuxt-link to="/">
            sign in
          </nuxt-link>
        </div>
        <v-spacer />

        <v-btn
          color="info"
          @click="show = !show"
        >
          Log In
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider />

          <v-card-text>
            {{ $route.path }}
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
export default {
  layout: 'home',
  data () {
    return {
      show: false,
      username: '',
      password: ''
    }
  },
  methods: {
    login () {
      // handle login logic here
    }
  }
}
</script>
<style lang="scss">
.set-max-width{
  max-width: 30%;
  margin-top: 5%;
}
</style>
