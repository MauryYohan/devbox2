<template>
  <div class="container">
    <!--  LETTERS-->

    <ul class="my-title-main">
      <li>
        <input type="checkbox" />
        <div class="letter">D</div>
      </li>
      <li>
        <input type="checkbox" />
        <div class="letter">E</div>
      </li>
      <li>
        <input type="checkbox" />
        <div class="letter">V</div>
      </li>
      <li>
        <input type="checkbox" />
        <div class="letter">B</div>
      </li>
      <li>
        <input type="checkbox" />
        <div class="letter">O</div>
      </li>
      <li>
        <input type="checkbox" />
        <div class="letter">X</div>
      </li>
      <!--    <li>-->
      <!--      <input type="checkbox" />-->
      <!--      <div class="letter">M</div>-->
      <!--    </li>-->
    </ul>
  </div>
</template>

<script>
export default {
  name: "TitlePages"
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@900&display=swap');

body {
  padding: 0;
  margin: 0;
  height: 100vh;
  background: red;
  font-family: 'Poppins', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
}

ul {
  position: relative;
}

li {
  list-style: none;
}

label {
  position: relative;
}

input[type="checkbox"] {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 80px;
  width: 80px;
  z-index: 100;
}

.letter {
  position: relative;
  height: 80px;
  width: 80px;
  background: #18191f;
  color: #555;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 46px;
  cursor: pointer;
  margin: 0 4px;
  border-radius: 20px;
  box-shadow: -1px -1px 4px rgba(255, 255, 255, 0.05),
  4px 4px 6px rgba(0, 0, 0, 0.2),
  inset -1px -1px 4px rgba(255, 255, 255, 0.05),
  inset 1px 1px 1px rgba(0, 0, 0, 0.1);
}

/* div:before {
  content: "";
  position: absolute;
  top: 2px;
  left: 2px;
  width: 75px;
  height: 38px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  background: rgba(255, 255, 255, 0.05);
} */

input[type="checkbox"]:checked ~ div {
  box-shadow: inset 0 0 2px rgba(255, 255, 255, 0.05),
  inset 4px 4px 6px rgba(0, 0, 0, 0.2);
  color: yellow;
  text-shadow: 0 0 15px yellow, 0 0 25px yellow;
  animation: glow 1.5s linear infinite;

}



@keyframes glow {
  0% {
    filter: hue-rotate(0deg);
  }
  100% {
    filter: hue-rotate(360deg);
  }
}


.check-form-plus{
  opacity: 1 !important;
  height: 16px !important;
  width: 14px !important;
}

.my-title-main{
  display:flex;
  justify-content: center;
  padding-bottom:20px;
  font-family: 'Poppins', sans-serif;
}

</style>