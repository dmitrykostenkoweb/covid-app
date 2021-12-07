<template>
  <div class="wrapper">
    <div class="intro">
      <div class="intro__media">
        <video
          class="intro__media-video"
          src="../static/WHO_ A global response to a global pandemic.mp4"
          autoplay
          muted
          loop
        ></video>
      </div>
      <div class="intro__content">
        <h1>COVID INFO</h1>
        <app-bar />
      </div>
    </div>
  </div>
</template>

<script>
import AppBar from '../components/AppBar.vue'
export default {
  components: { AppBar },
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat+Alternates:wght@400;600;800&display=swap');
* {
  padding: 0;
  margin: 0;
  border: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat Alternates', sans-serif;
  color: white;
}
h1 {
  margin: 20px auto;
}

.intro {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100vh;
  width: 100vw;
}
.intro__media {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  background: rgb(218, 218, 218) url(../static/covid.png) no-repeat center
    center;
  background-size: cover;
}
.intro__media::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  z-index: 5;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
}
.intro__media-video {
  position: absolute;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
  object-fit: cover;
  transform: translate(-50%, -50%);
}
.intro__content {
  z-index: 10;
}
</style>
