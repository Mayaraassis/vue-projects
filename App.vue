<template>
  <div class="container">
    <div class="left">
      <div class="card-front">
        <div class="logo">
          <img src="./assets/card-logo.svg" alt="">
        </div>
        <div class="infos">
          <div class="numero">
            {{ number }}
          </div>
          <div class="nomeMes">
            <p class="nome">
              {{ name }}
            </p>
            <p>
              {{ mes }}/{{ ano }}
            </p>
          </div>
        </div>
        
      </div>
      <div class="card-back">
        <p class="cvc_txt">
          {{ cvc }}
        </p>
      </div>
    </div>
    <div class="rigth">
      <label for="name">
        Cardholder Name
      </label>
      <input type="text" name="name" id="" :placeholder="placeholderText" v-model="name" @focus="setPlaceholderText('')" @blur="setPlaceholderText('e.g. Jane Appleseed')">
      <label for="number">
        Card Number
      </label>
      <input type="text" name="number" id="" placeholder="e.g. 1234 5678 9123 0000" v-model="number">
      <v-row>
        <label for="date"> Exp. Date (MM/YY)</label>
        <label for="cvc">CVC</label>
      </v-row>
      <div class="data">
        <input type="text" placeholder="MM" name="date" v-model="mes">
        <input type="text" placeholder="YY" name="date" v-model="ano">
        <input type="text" placeholder="e.g. 123" v-model="cvc">

      </div>

      <button class="btn"> Confirm</button>
    </div>
    <div class="complet" v-if="completed">
      Thank you!
      We've added your card details
      <button>
        Continue
      </button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      completed: false,
      number: "0000 0000 0000 0000",
      name: 'Jane Appleseed',
      cvc: '000',
      mes:'00',
      ano:'00',
      isPlaceholderVisible: true

    }
  },
  methods: {
    setPlaceholderText(text) {
      this.placeholderText = text;
    }

  }
}

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500&display=swap');
* {
  font-family: 'Space Grotesk', sans-serif;
  margin: 0;
  padding: 0;
  font-size: 18px;
}

.container {
  display: flex;
  width: 90vw;
  height: 100vh;
  position: relative;
}
.cvc_txt{
  margin-right: 55px;
  color: white;
}
.card-front {
  position: absolute;
  color: white;
  width: 447px;
  height: 245px;
  background-image: url("./assets/bg-card-front.png");
  top: 140px;
  left: 150px;
}

.card-back {
  bottom: 265px;
  left: 200px;
  position: absolute;
  width: 447px;
  color: rgb(0, 0, 0);
  height: 245px;
  display: flex;
  justify-content: end;
  align-items: center;
  background-image: url("./assets/bg-card-back.png");
}

.data {
  display: flex;

}

.left {
  color: white;
  width: 450px;
  height: 100%;
  background-image: url("./assets/bg-main-desktop.png");
}

.rigth {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 0 auto;
  background-color: white;
}

input {
  height: 40px;
  border-radius:8px;
  margin-bottom: 8px;
  margin-right: 8px;
  border: 1px solid hsl(279, 6%, 55%);
  outline-color: hsl(249, 99%, 64%) to hsl(278, 94%, 30%);
}
.infos {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  align-content: end;
  margin-top: 90px;
}
.btn {
  width: 300px;
  height: 50px;
  border-radius: 8px;
  background-color: hsl(278, 68%, 11%);
  color: white;
  margin-top: 20px;
  margin-left: 162px;
}

#app {
  margin: 0 !important;
  padding: 0;
}

.nomeMes {
font-size: 18px;
display: flex;
width: 400px;
justify-content: space-around;
}

.numero{
font-size: 28px;
}
</style>