<template>
  <v-container class="  set-max-width">
    <v-progress-linear
      v-if="isLoading"
      color="primary"
      indeterminate
    />
    <v-card md="6" class="mx-auto">
      <v-card-title>
        Sign In Form
      </v-card-title>
      <v-card-text>
        <v-form ref="form" lazy-validation @submit.prevent>
          <v-text-field
            v-model="username"
            label="Username"
            prepend-inner-icon="mdi-account"
            :rules="usernameRule"
            :counter="20"
            required
            autocomplete="username"
          />
          <v-text-field
            v-model="password"
            label="Password"
            :type="isShow ? 'text' : 'password'"
            prepend-inner-icon="mdi-lock"
            :counter="25"
            :rules="passwordRule"
            :append-icon="isShow ? 'mdi-eye' : 'mdi-eye-off'"
            autocomplete="current-password"
            required
            @click:append="isShow = !isShow"
          />
        </v-form>
      </v-card-text>
      <v-card-actions>
        <div>
          <span>If you don't have account, </span>
          <nuxt-link to="/sign_up">
            sign up
          </nuxt-link>
        </div>
        <v-spacer />

        <v-btn
          color="info"
          @click="signIn"
        >
          Sign In
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
</template>

<script>
export default {
  layout: 'home',
  data () {
    return {
      // show: false,
      isShow: false,
      isLoading: false,
      username: '',
      password: '',
      usernameRule: [
        v => !!v || 'User name is required',
        v => (v && v.length <= 15) || 'Must be less than 15 characters',
        v => /^[a-zA-Z0-9_]+$/.test(v) || 'Only contain a-z,A-z,0-9 and _'
      ],
      passwordRule: [
        v => !!v || 'Password is required',
        v => (v && v.length <= 15) || 'Must be less than 20 characters and greater than 8 characters',
        v => /(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}/.test(v) || 'contain min 8 character, 1 lowcase letter, 1 uppercase letter, 1 number and max 20 character'
      ]
    }
  },
  methods: {
    signIn () {
      if (this.$refs.form.validate()) {
        this.isShow = !this.isShow
        this.isLoading = !this.isLoading
      }
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
