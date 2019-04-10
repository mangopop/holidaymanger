/* eslint-disable no-console */
<template>
  <v-menu
    ref="datePicker"
    v-model="datePicker"
    :close-on-content-click="false"
    :nudge-right="40"
    :return-value.sync="date"
    lazy
    transition="scale-transition"
    offset-y
    full-width
    min-width="290px"
  >
    <template v-slot:activator="{ on }">
      <v-text-field
        v-model="date"
        label="Date"
        prepend-icon="event"
        readonly
        v-on="on"
      ></v-text-field>
    </template>
    <v-date-picker v-model="date" no-title scrollable>
      <v-spacer></v-spacer>
      <v-btn flat color="primary" @click="datePicker = false">Cancel</v-btn>
      <v-btn
        flat
        color="primary"
        @click="
          $refs.datePicker.save(date)
          onDateChange(date)
        "
        >OK</v-btn
      >
    </v-date-picker>
  </v-menu>
</template>

<script>
export default {
  name: 'DatePicker',
  props: [],
  data() {
    return {
      date: new Date().toISOString().substr(0, 10),
      datePicker: false
    }
  },
  computed: {},
  mounted() {},
  methods: {
    onDateChange(event) {
      this.$emit('dateset', this.date)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
