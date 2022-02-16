<template>
  <main>
    <h1>Vamos calcular sua média!</h1>
    <form @submit.prevent="handleSubmit" name="form">
      <div class="container-notas">
        <div class="areas">
          <label class="input-nota">
            Linguagens e Códigos:
            <input v-model="lc" type="number" required placeholder="999,9" />
          </label>

          <label class="input-nota">
            Ciências Humanas:
            <input v-model="ch" type="number" required placeholder="999,9" />
          </label>

          <label class="input-nota">
            Ciências da Natureza:
            <input v-model="cn" type="number" required placeholder="999,9" />
          </label>

          <label class="input-nota">
            Matemática:
            <input v-model="mt" type="number" required placeholder="999,9" />
          </label>

          <label class="input-nota">
            Redação:
            <input v-model="red" type="number" required placeholder="999,9" />
          </label>
        </div>

        <div class="pesos">
          <label class="peso">
            Peso:
            <input
              v-model="pesolc"
              type="number"
              pattern="[0-9]"
              min="1"
              max="10"
              required
            />
          </label>
          <label class="peso">
            Peso:
            <input
              v-model="pesoch"
              type="number"
              pattern="[0-9]"
              min="1"
              max="10"
              required
            />
          </label>

          <label class="peso">
            Peso:
            <input
              v-model="pesocn"
              type="number"
              pattern="[0-9]"
              min="1"
              max="10"
              required
            />
          </label>

          <label class="peso">
            Peso:
            <input
              v-model="pesomt"
              type="number"
              pattern="[0-9]"
              min="1"
              max="10"
              required
            />
          </label>

          <label class="peso">
            Peso:
            <input
              v-model="pesored"
              type="number"
              pattern="[0-9]"
              min="1"
              max="10"
              required
            />
          </label>
        </div>
      </div>

      <button type="submit">Calcular</button>
    </form>

    <p v-if="media">Sua média : {{ this.media }}</p>
  </main>
</template>

<script>
import "./styles/global.css";

export default {
  name: "App",
  data() {
    return {
      lc: "",
      pesolc: 1,
      ch: "",
      pesoch: 1,
      cn: "",
      pesocn: 1,
      mt: "",
      pesomt: 1,
      red: "",
      pesored: 1,
      media: "",
    };
  },
  methods: {
    handleSubmit() {
      let sumPeso =
        this.pesolc + this.pesoch + this.pesocn + this.pesomt + this.pesored;

      let sumG =
        this.pesolc * this.lc +
        this.pesoch * this.ch +
        this.pesocn * this.cn +
        this.pesomt * this.mt +
        this.pesored * this.red;

      this.media = (sumG / sumPeso).toFixed(1);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;700&family=Roboto:wght@400;500;700&display=swap");

body {
  margin: 0;
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}

main {
  font-family: "Roboto", sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 10vh;
  height: 100vh;
  background-color: #303030;
}

h1 {
  font-family: "Inter", sans-serif;
  color: #fff;
  margin-right: 5vw;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 15px;
}

.container-notas {
  display: flex;
  margin-right: 5vw;
  margin-top: 70px;
}

.areas {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.pesos {
  margin-left: 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.peso {
  color: #fff;
  margin: 15px 0;
}

.input-nota {
  color: #fff;
  margin: 15px 0;
}

input {
  border: 0;
  border-radius: 5px;
  padding: 8px 0;
  text-align: center;
}

button {
  border: 0;
  border-radius: 10px;
  margin-top: 15px;
  font-size: 20px;
  padding: 10px 15px;
  background-color: #25aae1;
  cursor: pointer;
}

p {
  margin-top: 70px;
  border-radius: 10px;
  width: 200px;
  background-color: #f3f3f3;
  text-align: center;
  padding: 15px;
}

@media (max-width: 531px) {
  main {
    height: 100%;
  }

  h1 {
    text-align: center;
  }

  .areas {
    margin-left: 25px;
  }

  .pesos {
    margin-left: 30px;
  }

  p {
    margin-bottom: 35px;
  }
}
</style>
