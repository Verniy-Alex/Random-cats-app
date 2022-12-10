<script >
import axios from 'axios'

export default {
  data() {
    return {
      info: null
    }
  },
  methods: {
    getRandomImg() {

      try {
        axios.get('http://aws.random.cat//meow')
          .then(resp => (this.info = resp.data))
      }
      catch (error) {
        alert(error);
      }

    }
  }
}
</script>
<template>
  <div class="wrapper">
    <div class="app__container">
      <h1>Получение рандомных картинок по API</h1>
      <p><a href="http://random.cat/view/268"> Api site</a></p>
      <div class="random-container-img-box">
        <img v-if="this.info != null" :src="this.info.file" alt="cat">
      </div>
      <button @click="getRandomImg()">Click</button>
    </div>
  </div>


</template>

<style scoped>
.app__container button {
  margin-top: 15px;
  padding: 8px 10px;
  font-size: 14px;
}

.app__container {
  text-align: center;
  display: flex;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

.app__container h1 {
  margin-bottom: 10px;
}

.app__container p {
  margin-bottom: 10px;
}

.random-container-img-box {
  max-width: 600px;
  height: 100%;
}

.random-container-img-box img {
  width: 100%;
}
</style>
