<template>
  <div class="intro__media">
    <video
      class="intro__media-video"
      src="../assets/background-live.webm"
      autoplay
      muted
      loop
    ></video>
  </div>
</template>

<script>
export default { name: 'LiveBackground' }
</script>

<style>
.intro__media {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgb(218, 218, 218) url(../assets/covid.png) no-repeat center
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
</style>
