<template>
  <div class="about">
    <div>
      <label for="email">Email </label>
      <input
        id="email"
        v-model="email"
        type="email"
      >
    </div>
    <div>
      <label for="password">Password </label>
      <input
        id="password"
        v-model="password"
        type="password"
      >
    </div>
    <button
      type="button"
      @click="signInUser(email, password)"
    >
      Sign in
    </button>
  </div>
</template>

<script>
import { signInWithEmailAndPassword } from 'firebase/auth';
import { auth } from '@/firebase.config';

export default {
  name: 'Login',

  data() {
    return {
      email: '',
      password: '',
    };
  },

  methods: {
    async signInUser(email, password) {
      try {
        await signInWithEmailAndPassword(auth, email, password);
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>
