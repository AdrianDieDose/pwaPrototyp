<template>
  <div class="container mt-5 outer-container">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show" id="lable-color">
      <b-form-group id="input-group-1" label="Touchpoint:" label-for="input-1">
        <b-form-input
          id="input-1"
          v-model="form.touchpoint"
          required
          placeholder="Friseur, Pizzeria..."
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2 " label="Stadt:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.city"
          required
          placeholder="Bielefeld, Essen..."
        ></b-form-input>
      </b-form-group>

      <div class="container" id="btn">
        <div class="row">
          <div class="col">
            <b-button type="submit" class="btn-block" id="button-color"
              >Submit</b-button
            >
          </div>
          <div class="col">
            <b-button
              :disabled="!touchpointFilled || !stadtFilled"
              type="submit"
              class="btn-block"
              id="button-color"
              >Download Excel</b-button
            >
          </div>
        </div>
      </div>
    </b-form>
  </div>
</template>
<script>
export default {
  props: {
    x: String,
  },
  data() {
    return {
      form: {
        touchpoint: '',
        city: '',
      },
      show: true,
      stadtFilled: false,
      touchpointFilled: false,
    }
  },
  methods: {
    onSubmit(evt) {
      console.log(this.form.city)
      evt.preventDefault()
      alert(JSON.stringify(this.form))
    },
    onReset(evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.touchpoint = ''
      this.form.city = ''
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    },
  },
  watch: {
    'form.city'(value) {
      if (value) {
        this.stadtFilled = true
      } else {
        this.stadtFilled = false
      }
    },
    'form.touchpoint'(value) {
      if (value) {
        this.touchpointFilled = true
      } else {
        this.touchpointFilled = false
      }
    },
  },
}
</script>
<style scoped>
#btn {
  margin-top: 10%;
}
#lable-text {
  color: white;
}
#button-color {
  background-color: #ffa626;
  color: black;
  border-color: black;
}
#lable-color {
  color: white;
}
#outer-container {
  padding: 0;
  margin: 0 10% !important;
}
</style>
