<template>
  <div id="app">
    <div class="container">
      <p>
        <span>Advice #{{ id }}</span>
      </p>
      <p>"{{ advice }}"</p>
      <div>
        <svg width="444" height="16" xmlns="http://www.w3.org/2000/svg">
          <g fill="none" fill-rule="evenodd">
            <path fill="#4F5D74" d="M0 8h196v1H0zM248 8h196v1H248z" />
            <g transform="translate(212)" fill="#CEE3E9">
              <rect width="6" height="16" rx="3" />
              <rect x="14" width="6" height="16" rx="3" />
            </g>
          </g>
        </svg>
      </div>
      <div class="btnC">
        <svg
          @click="generateAdv"
          class="btn"
          width="24"
          height="24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z"
            fill="#202733"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      id: "",
      advice: "",
    };
  },
  methods: {
    generateAdv() {
      axios
        .get("https://api.adviceslip.com/advice")
        .then((response) => {
          this.id = response.data.slip.id;
          this.advice = response.data.slip.advice;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn {
  margin-top: 10px;
  cursor: pointer;
}
.btnC {
  width: 45px;
  height: 45px;
  background-color: hsl(150, 100%, 66%);
  border-radius: 22px;
}
.container {
  background-color: hsl(217, 19%, 24%);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  align-items: center;
  align-content: center;
  margin: 0 auto;
  padding: 20px;
  color: white;
  text-align: center;
}
span {
  color: hsl(150, 100%, 66%);
}
</style>
