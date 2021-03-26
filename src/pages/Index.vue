<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="form.name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />

      <q-input
        filled
        v-model="form.hobby"
        label="Your hobby *"
        lazy-rules
          :rules="[ val => val && val.length > 0 || 'Please type your hobby']"
      />

      <q-input
        filled
        type="number"
        v-model="form.age"
        label="Your age *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
    <label>
      {{ biodata.name }} <br>
      {{ biodata.hobby }} <br>
      {{ biodata.age }} <br>
    </label>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        name: null,
        hobby: null,
        age: null
      },
      biodata: {
        name: null,
        hobby: null,
        age: null
      },
      accept: false
    }
  },

  methods: {
    onSubmit () {
      console.log(this.form)
      this.biodata.name = (this.form.name)
      this.biodata.hobby = (this.form.hobby)
      this.biodata.age = (this.form.age)
    },

    onReset () {
      this.form.name = null
      this.form.hobby = null
      this.form.age = null
      this.biodata.name = null
      this.biodata.hobby = null
      this.biodata.age = null
      this.accept = false
    }
  }
}
</script>
