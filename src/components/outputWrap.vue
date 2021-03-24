<template>
  <div class="wrapper" :allUser="allUser">
    <div>
      <div class="img-bg" :class="allUser.gender"></div>
      <img :src="allUser.picture" />
      <ul>
        <li>
          <span :class="allUser.gender">Name</span>
          {{ allUser.name }}
        </li>
        <li>
          <span :class="allUser.gender">Gender</span>
          {{ allUser.gender }}
        </li>
        <li>
          <span :class="allUser.gender">Age</span>
          {{ allUser.age }}
        </li>
        <li>
          <span :class="allUser.gender">Phone</span>
          {{ allUser.phone }}
        </li>
        <li>
          <span :class="allUser.gender">Email</span>
          {{ allUser.email }}
        </li>
        <li>
          <span :class="allUser.gender">Country</span>
          {{ allUser.country }}
        </li>
        <li>
          <span :class="allUser.gender">State</span>
          {{ allUser.state }}
        </li>
        <li>
          <span :class="allUser.gender">City</span>
          {{ allUser.city }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  margin: 3rem auto;
  padding: 5rem 2rem 2rem;
  min-width: 300px;
  border-radius: 5px;
  position: relative;
  box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.15) !important;
  overflow: hidden;
}

img {
  margin: 0 auto 2rem;
  display: block;
  border-radius: 50%;
  border: solid 8px #fff;
  z-index: 5;
  position: relative;
  background-size: cover;
  background-repeat: no-repeat;
}

.img-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 30%;
}

li {
  display: flex;
  align-items: center;
  margin-bottom: 5px;
}

li span {
  padding: 5px 10px;
  margin-right: 10px;
  border-radius: 5px;
}

.male {
  background: #5b94cb;
  color: #fff;
}

.female {
  background: #ee9e9e;
  color: #fff;
}
</style>

<script>
export default {
  name: "outputWrap",
  props: {
    allUser: Object,
  },
};
</script>
