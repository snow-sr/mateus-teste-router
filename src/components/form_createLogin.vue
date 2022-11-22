<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      username: "",
      password: "",
    };
  },
  methods: {
    createUser(e) {
      axios
        .post("http://localhost:8000/watchers/", {
          email: this.email,
          username: this.username,
          password: this.password,
        })
        .then((res) => {
          console.log(res);
          this.$router.push("/login");
        })
        .catch((error) => {
          alert(error);
        });
    },
  },
};
</script>

<template>
  <div>
    <div>
      <div class="mb-6">
        <label for="name" class="block mb-2 font-medium">Nome de usuário</label>
        <input
          type="text"
          id="name"
          v-model="username"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
          placeholder=""
          required="true"
        />
      </div>
      <div class="mb-6">
        <label for="email" class="block mb-2 font-medium">Email</label>
        <input
          type="email"
          id="email"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
          v-model="email"
          placeholder="exemplo@email.com"
          required="true"
        />
      </div>
      <div class="mb-6">
        <label for="password" class="block mb-2 font-medium">Senha</label>
        <input
          type="password"
          id="password"
          v-model="password"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
          placeholder="*********"
          required="true"
        />
      </div>
      <div class="mb-6">
        <label for="confirm_pass" class="block mb-2 font-medium"
          >Confirme sua Senha</label
        >
        <input
          type="password"
          id="confirm_pass"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
          placeholder="*********"
          required="true"
        />
      </div>
      <div class="flex items-start mb-6">
        <div class="flex items-center h-5">
          <input
            id="remember"
            type="checkbox"
            value=""
            class="w-4 h-4 bg-gray-50 rounded border border-gray-300 focus:ring-3 focus:ring-blue-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-600 dark:ring-offset-gray-800"
            required
          />
        </div>
        <label for="remember" class="ml-2 text-sm font-medium text-gray-900"
          >Tenho mais de 18 anos</label
        >
      </div>
      <button
        class="text-white hover:bg-gray-900 bg-primary transition-all font-medium rounded-lg text-sm w-full px-5 py-2.5 text-center"
        @click="createUser"
      >
        Entrar
      </button>
    </div>
  </div>
</template>

<style scoped></style>
