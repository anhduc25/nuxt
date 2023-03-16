<template>
  <v-container class="  set-max-width">
    <v-progress-linear
      v-if="isLoading"
      color="primary"
      indeterminate
    />
    <v-card md="6" class="mx-auto">
      <v-card-title>
        Sign Up Form
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
          />
          <v-text-field
            v-model="password"
            label="Password"
            :type="isShow1 ? 'text' : 'password'"
            prepend-inner-icon="mdi-lock"
            :counter="25"
            :rules="passwordRule"
            :append-icon="isShow1 ? 'mdi-eye' : 'mdi-eye-off'"
            required
            @click:append="isShow1 = !isShow1"
          />
          <v-text-field
            v-model="rePassword"
            label="Re-Password"
            :type="isShow2 ? 'text' : 'password'"
            prepend-inner-icon="mdi-lock-check"
            :counter="25"
            :rules="rePasswordRule"
            :append-icon="isShow2? 'mdi-eye' : 'mdi-eye-off'"
            required
            @click:append="isShow2 = !isShow2"
          />
          <v-text-field
            v-model="phoneNumber"
            label="Phone Number"
            type="tel"
            :counter="30"
            prepend-inner-icon="mdi-phone-dial"
            :rules="phoneNumberRule"
            required
          />
          <v-text-field
            v-model="email"
            label="Email"
            type="email"
            :counter="30"
            prepend-inner-icon="mdi-email"
            required
            :rules="emailRule"
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
          @click="signUp"
        >
          Sign Up
        </v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-if="msg">
          <v-divider />

          <v-card-text class="text-center">
            <v-icon color="green lighten-3">
              mdi-account-check
            </v-icon>
            {{ msg }}
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      msg: '',
      isLoading: false,
      isShow1: false,
      isShow2: false,
      username: '',
      password: '',
      email: '',
      phoneNumber: '',
      rePassword: '',
      usernameRule: [
        v => !!v || 'User name is required',
        v => (v && v.length <= 15) || 'Must be less than 15 characters',
        v => /^[a-zA-Z0-9_]+$/.test(v) || 'Only contain a-z,A-z,0-9 and _'
      ],
      passwordRule: [
        v => !!v || 'Password is required',
        v => (v && v.length <= 15) || 'Must be less than 20 characters and greater than 8 characters',
        v => /(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}/.test(v) || 'contain min 8 character, 1 lowcase letter, 1 uppercase letter, 1 number and max 20 character'
      ],
      rePasswordRule: [
        v => !!v || 'Re-Password is required',
        v => (v && v.length <= 15) || 'Must be less than 20 characters and greater than 8 characters',
        v => /(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}/.test(v) || 'contain min 8 character, 1 lowcase letter, 1 uppercase letter, 1 number and max 20 character',
        v => v === this.password || 'Not correct'
      ],
      phoneNumberRule: [
        v => !!v || 'Phone number is required',
        v => /\(?([0-9]{3})\)?([ .-]?)([0-9]{3})\2([0-9]{4})/.test(v) || 'Invalid'
      ],
      emailRule: [
        v => !!v || 'Email is required',
        v => /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(v) || 'Invalid'
      ]
    }
  },
  methods: {
    signUp () {
      if (this.$refs.form.validate()) {
        this.isShow1 = !this.isShow1
        this.isShow2 = !this.isShow2
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
