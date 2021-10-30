<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="10" md="7" class="mx-auto my-5 pa-5 form-box">
        <h1>Sign up</h1>
        <v-form>
          <v-text-field 
            label="Email" 
            type="email"
            prepend-icon="mdi-email"
            placeholder="Example@email.com"
          ></v-text-field>

          <v-autocomplete label="Which browser do you use?" :items="browsers" prepend-icon="mdi-form-select"></v-autocomplete>

          <v-file-input
            show-size
            counter
            label="Attach profile picture"
            :rules="rules"
            accept="image/png, image/jpeg, image/bmp"
            prepend-icon="mdi-camera"
          ></v-file-input>

          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            transition="scale-transition"
            offset-y
            min-width="auto"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-text-field
                v-model="date"
                label="Birthday date"
                prepend-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker
              v-model="date"
              :active-picker.sync="activePicker"
              :max="(new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)"
              min="1950-01-01"
              @change="save"
            ></v-date-picker>
          </v-menu>

          <v-checkbox
            v-model="checkbox"
            label="Agree to terms & conditions"
          ></v-checkbox>

          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        date: '',
        browsers: ['Chrome', 'Firefox', 'Safari', 'Edge', 'Brave']
      }
    },
  }
</script>

<style scoped>
.form-box {
  box-shadow: 0px 3px 5px -1px rgb(0 0 0 / 20%), 0px 5px 8px 0px rgb(0 0 0 / 14%), 0px 1px 14px 0px rgb(0 0 0 / 12%) !important;
}
</style>