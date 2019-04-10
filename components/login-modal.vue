<template>
  <v-card>
    <v-card-title class="headline">Login</v-card-title>
    <v-card-text>
      <v-container grid-list-md>
        <v-layout wrap>
          <form>
            <v-text-field
              v-model="name"
              :error-messages="nameErrors"
              :counter="10"
              label="Name"
              required
              @input="$v.name.$touch()"
              @blur="$v.name.$touch()"
            ></v-text-field>
            <v-text-field
              v-model="email"
              :error-messages="emailErrors"
              label="E-mail"
              required
              @input="$v.email.$touch()"
              @blur="$v.email.$touch()"
            ></v-text-field>

            <v-card-actions>
              <v-spacer></v-spacer>

              <v-btn @click="submit">Login</v-btn>
            </v-card-actions>
          </form>
        </v-layout>
      </v-container>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: 'Login',
  props: [],
  data() {
    return {}
  },
  computed: {},
  mounted() {},
  methods: {}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
