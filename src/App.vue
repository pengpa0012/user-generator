<template>
  <div class="container">
    <div class="heading">
      <span>Made by Godfrey Necesario</span>
      <h1>User Generator</h1>
    </div>
    <submitBtn
      text="Generate User"
      bgColor="#fff"
      textColor="#000"
      border="1px solid rgba(0,0,0,.125)"
      class="submitBtn"
      @click="displayUser"
    />
    <outputWrap :imgSrc="imgSrc" :allUser="allUser" />
  </div>
</template>

<script>
import submitBtn from "@/components/submitBtn.vue";
import outputWrap from "@/components/outputWrap.vue";
import { ref } from "vue";

export default {
  setup() {
    const allUser = ref({});

    // To display user on load
    fetch("https://randomuser.me/api/")
      .then((res) => res.json())
      .then((data) => {
        allUser.value = {
          name: data.results[0].name.first + " " + data.results[0].name.last,
          age: data.results[0].dob.age,
          gender: data.results[0].gender,
          phone: data.results[0].phone,
          picture: data.results[0].picture.large,
          email: data.results[0].email,
          city: data.results[0].location.city,
          state: data.results[0].location.state,
          country: data.results[0].location.country,
        };
      });

    // To change user on btn click
    async function displayUser() {
      const res = await fetch("https://randomuser.me/api/");

      const data = await res.json();

      allUser.value = {
        name: data.results[0].name.first + " " + data.results[0].name.last,
        age: data.results[0].dob.age,
        gender: data.results[0].gender,
        phone: data.results[0].phone,
        picture: data.results[0].picture.large,
        email: data.results[0].email,
        city: data.results[0].location.city,
        state: data.results[0].location.state,
        country: data.results[0].location.country,
      };
    }

    let imgSrc = ref("");

    fetch("https://source.unsplash.com/random").then((data) => {
      imgSrc = data.url;
      console.log(imgSrc);
    });

    return {
      imgSrc,
      allUser,
      displayUser,
    };
  },

  components: {
    submitBtn,
    outputWrap,
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1366px;
  margin: auto;
  font-family: "Courier New", Courier, monospace;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0 10px;
}

.flex {
  display: flex;
}

.heading {
  text-align: center;
  padding: 3rem 30px;
}

.heading span {
  font-size: 1.2rem;
}

.heading h1 {
  font-size: 3.5rem;
  font-weight: 300;
}

li {
  list-style: none;
}

button {
  padding: 10px 20px;
  outline: none;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1.2rem;
}

.submitBtn:hover {
  background: #f7f7f7 !important;
}

@media (max-width: 635px) {
  .heading {
    padding: 2rem 30px;
  }

  .heading span {
    font-size: 1rem;
  }

  .heading h1 {
    font-size: 2.25rem;
  }

  button {
    margin: 1rem auto !important;
  }
}

@media (max-width: 400px) {
  .heading span {
    font-size: 0.8rem;
  }

  .heading h1 {
    font-size: 2rem;
  }

  .wrapper {
    margin: 2rem auto !important;
    padding: 5rem 1rem 1rem !important;
    width: 100% !important;
  }
}
</style>
