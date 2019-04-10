<template>
  <v-layout row justify-end>
    <v-btn fab dark color="red" @click.stop="dialog = true">
      <v-icon dark>add</v-icon>
    </v-btn>

    <v-dialog v-model="dialog" max-width="400px">
      <v-card>
        <v-card-title class="headline">Book Holiday</v-card-title>
        <v-card-text>
          <v-container grid-list-md>
            <v-layout wrap>
              <!-- <form> -->
              <v-flex xs12>
                <p>Slot</p>

                <v-overflow-btn
                  v-model="dropdownSlot"
                  :items="dropdownSlots"
                  label="Overflow Btn"
                  target="#dropdown-example"
                  @change="onChange()"
                ></v-overflow-btn>
              </v-flex>
              <v-flex xs12>
                <date-picker
                  v-if="layout.start"
                  @dateset="onStartDateChange"
                ></date-picker>
                <!-- <v-text-field
                  v-if="layout.start"
                  v-model="start"
                  :error-messages="startErrors"
                  :counter="10"
                  label="Start"
                  required
                  @input="$v.start.$touch()"
                  @blur="$v.start.$touch()"
                ></v-text-field> -->
              </v-flex>
              <v-flex xs12>
                <date-picker
                  v-if="layout.end"
                  @dateset="onEndDateChange"
                ></date-picker>
                <!-- <v-text-field
                  v-if="layout.end"
                  v-model="end"
                  :error-messages="endErrors"
                  :counter="10"
                  label="End"
                  required
                  @input="$v.end.$touch()"
                  @blur="$v.end.$touch()"
                ></v-text-field> -->
              </v-flex>
              <v-flex xs12>
                <date-picker
                  v-if="layout.date"
                  @dateset="onOneDateChange"
                ></date-picker>
              </v-flex>
              <v-flex xs12>
                <v-text-field
                  v-model="description"
                  label="Description"
                ></v-text-field>
              </v-flex>
              <v-flex xs12>
                <v-radio-group v-if="layout.checkbox" v-model="slot" row>
                  <v-radio label="Morning" value="morning"></v-radio>
                  <v-radio label="Afternoon" value="afternoon"></v-radio>
                </v-radio-group>
              </v-flex>
              <v-card-actions>
                <div class="text-xs-right">
                  <v-btn @click="submit">Submit</v-btn>
                </div>
              </v-card-actions>
              <!-- </form> -->
            </v-layout>
          </v-container>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-layout>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required } from 'vuelidate/lib/validators'
import DatePicker from '~/components/date-picker.vue'

export default {
  name: 'HolidayModal',
  components: {
    DatePicker
  },
  mixins: [validationMixin],
  props: [],
  data() {
    return {
      dialog: false,
      start: '',
      end: '',
      date: '',
      slot: '',
      // date: new Date().toISOString().substr(0, 10),
      datePicker: false,
      description: '',
      layout: {
        start: false,
        end: false,
        date: true,
        checkbox: false
      },
      dropdownSlot: '',
      dropdownSlots: ['Half Day', 'One Day', 'Several']
    }
  },
  validations: {
    start: { required },
    end: { required },
    date: { required }
  },
  computed: {
    startErrors: function() {
      return ''
    },
    endErrors: function() {
      return ''
    },
    dateErrors: function() {
      return ''
    }
  },
  methods: {
    submit() {},
    onOneDateChange(value) {
      this.date = value
      // console.log(value) // someValue
    },
    onStartDateChange(value) {
      this.start = value
      // console.log(value) // someValue
    },
    onEndDateChange(value) {
      this.end = value
      // console.log(value) // someValue
    },
    onChange() {
      // console.log(event.target.value)
      if (this.dropdownSlot === 'Half Day') {
        this.layout = {
          start: false,
          end: false,
          checkbox: true,
          date: true
        }
      } else if (this.dropdownSlot === 'One Day') {
        this.layout = {
          start: false,
          end: false,
          checkbox: false,
          date: true
        }
      } else if (this.dropdownSlot === 'Several') {
        this.layout = {
          start: true,
          end: true,
          checkbox: false,
          date: false
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
