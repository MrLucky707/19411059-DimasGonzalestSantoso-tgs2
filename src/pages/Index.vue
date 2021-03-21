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
        label="Nama Lengkap"
        hint="Masukan Nama Lengkap Anda"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Kolom Nama Tidak Boleh Kosong']"
      />

      <q-input
        filled
        type="number"
        v-model="form.age"
        label="Umur"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Umur Tidak Boleh Kosong',
          val => val > 0 && val < 200 || 'Tolong Tulis Umur Asli Anda'
        ]"
      />

      <q-input
        filled
        v-model="form.hobby"
        label="Hobi"
        hint="Tulis Hobi Anda"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Tolong diisi']"
      />

      <q-input
        filled
        v-model="form.job"
        label="Pekerjaan"
        hint="Tulis Pekerjaan Anda"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Harap Diisi']"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
      <div>
        {{ datas.name }}<br>
        {{ datas.age }}<br>
        {{ datas.hobby }}<br>
        {{ datas.job }}<br>
      </div>
    </q-form>

  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        name: null,
        age: null,
        hobby: null,
        job: null
      },
      datas: {
        name: null,
        age: null,
        hobby: null,
        job: null
      },
      accept: false
    }
  },

  methods: {
    onSubmit () {
      this.datas = this.form
      console.log(this.datas)
    },

    onReset () {
      this.form.name = null
      this.form.age = null
      this.form.hobby = null
      this.form.job = null
      this.accept = false
    }
  }
}
</script>
