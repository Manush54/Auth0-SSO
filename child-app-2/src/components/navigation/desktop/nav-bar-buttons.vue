<template>
  <div class="nav-bar__buttons">
    {{ $auth0.isAuthenticated }}
    <template v-if="!$auth0.isAuthenticated">
      <SignupButton />
      <LoginButton />
    </template>
    <template v-if="$auth0.isAuthenticated">
      <LogoutButton />
    </template>
  </div>
</template>

<script>
import LoginButton from "@/components/buttons/login-button.vue";
import LogoutButton from "@/components/buttons/logout-button.vue";
import SignupButton from "@/components/buttons/signup-button.vue";

export default {
  components: { LoginButton, LogoutButton, SignupButton },
};
</script>
