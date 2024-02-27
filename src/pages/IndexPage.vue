<template>
  <div class="q-pa-md" style="max-width: 400px">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        v-model="name"
        label="Empresa"
        hint="Nome da empresa"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input
        filled
        v-model="login"
        label="Login"
        hint="Login de usuário"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type something']"
      />

      <q-input
        filled
        type="number"
        v-model="password"
        label="Sua senha"
        lazy-rules
        :rules="[
          (val) => (val !== null && val !== '') || 'Please type your age',
          // (val) => (val > 0 && val < 100) || 'Please type a real age',
        ]"
      />

      <div>
        <q-btn label="Submit" type="submit" color="primary" />
        <q-btn
          label="Reset"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        />
      </div>
    </q-form>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar } from "quasar";
import { acceptHMRUpdate } from "pinia";

export default defineComponent({
  name: "IndexPage",
  setup() {
    const $q = useQuasar();

    const name = ref(null);
    const login = ref(null);
    const password = ref(null);

    return {
      name,
      login,
      password,

      onSubmit () {
        console.log(name.value)
        // console.log('@submit - do something here', evt)
        // evt.target.submit()
      },

      onReset () {
        name.value = null
        login.value = null
        password.value = null
      }
    };
  },
});
</script>
