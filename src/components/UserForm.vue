<template>
  <div>
    <h1>Formulaire d'inscription</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="name">Nom :</label>
        <input type="text" id="name" v-model="name" />
        <span v-if="errors.name">{{ errors.name }}</span>
      </div>

      <div>
        <label for="email">Email :</label>
        <input type="email" id="email" v-model="email" />
        <span v-if="errors.email">{{ errors.email }}</span>
      </div>

      <div>
        <label for="phone">Numéro de téléphone :</label>
        <input type="text" id="phone" v-model="phone" />
        <span v-if="errors.phone">{{ errors.phone }}</span>
      </div>

      <button type="submit">Soumettre</button>
    </form>

    <div v-if="submitted">
      <h2>Merci pour votre inscription, {{ name }}!</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      errors: {},
      submitted: false
    };
  },
  methods: {
    validateForm() {
      this.errors = {};

      if (!this.name) {
        this.errors.name = "Le nom est requis.";
      }

      if (!this.email) {
        this.errors.email = "L'email est requis.";
      } else if (!this.validEmail(this.email)) {
        this.errors.email = "L'email n'est pas valide.";
      }

      if (!this.phone) {
        this.errors.phone = "Le numéro de téléphone est requis.";
      } else if (!this.validPhone(this.phone)) {
        this.errors.phone = "Le numéro de téléphone n'est pas valide.";
      }

      return Object.keys(this.errors).length === 0;
    },
    validEmail(email) {
      const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(String(email).toLowerCase());
    },
    validPhone(phone) {
      const re = /^[0-9]{10}$/;
      return re.test(phone);
    },
    submitForm() {
      if (this.validateForm()) {
        this.submitted = true;
      }
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
form div {
  display: flex;
  flex-direction: column;
  margin-bottom: 1em;
}

form div input {
  width: 300px;
  padding: 10px;
  border: 1px solid #80A470;
  border-radius: 10px;
  outline: none;
}
form button {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  padding: 12px;
  border: none;
  border-radius: 10px;
  margin-bottom: 30px;
  margin-top: 20px;
  color: #ffffff;
  background-color:#FF8C00;
  width: 95%;
}

span {
  color: red;
  font-size: 0.8em;
}
</style>
