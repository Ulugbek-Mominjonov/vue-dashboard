<template>
  <v-container class="login-container">
    <v-row class="login-row">
      <v-col cols="12" sm="9" md="7" class="mx-auto">
        <v-card
          class="pb-3"
          color="cyan lighten-5"
          elevation="5">
          <v-card-title>Login</v-card-title>
          <v-card-text>
            <v-form>
              <v-text-field
                label="Username"
                prepend-icon="mdi-account-circle"></v-text-field>
              <v-text-field
                label="Password"
                :type="showPassword ? 'text' : 'password'"
                prepend-icon="mdi-lock"
                :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                @click:append="showPassword = !showPassword"></v-text-field>
            </v-form>
          </v-card-text>
          <v-divider></v-divider>
          <v-card-actions>
            <v-btn color="info">
              Login
              <v-icon class="ml-1">mdi-login</v-icon>
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn color="success" to="/signup">
              Regiter
              <v-icon class="ml-1">mdi-account-plus</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        showPassword: false,
      }
    }
  }
</script>

<style scoped>
.login-container, .login-row {
  height: 100%;
}
.login-row {
  align-items: center;
}
</style>