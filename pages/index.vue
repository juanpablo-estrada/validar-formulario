<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6" class="mt-15">
      <v-card class="logo py-4 d-flex justify-center" color="#e2e2e2">
        <VuetifyLogo />
      </v-card>
      <v-card>
        <v-card-title class="text-center headline">
          VueJS - NuxtJS
        </v-card-title>
        <v-card-text>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="Name"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              required
            ></v-text-field>

            <v-select
              v-model="select"
              :items="items"
              :rules="[(v) => !!v || 'Item is required']"
              label="Item"
              required
            ></v-select>

            <v-btn
              :disabled="!valid"
              color="success"
              class="mr-4"
              block
              @click="validate"
            >
              Validate
            </v-btn>
          </v-form>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',

  data() {
    return {
      valid: true,
      name: '',
      nameRules: [
        (v) => !!v || 'Name is required',
        (v) => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: ['Item 1', 'Item 2'],
    }
  },
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        alert('Formulario valido')
      }
    },
  },
}
</script>
