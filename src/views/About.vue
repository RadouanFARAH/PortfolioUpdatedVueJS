<template>
  <div>
    <div class="home-content">
      <div class="img-container zoomIn animated">
        <img src="../assets/white.png" alt="" />
      </div>
      <h1><span>Hi</span>, <span style='font-size:30px;'>&#128522;</span> <br> I'm Radouan FARAH</h1>
      <h4>
        I'm a Full Stack JavaScript Web Developer, based in Rabat, Morocco. I'm
        very ambitious when it comes to Development and Programming.
      </h4>
      <div class="socialMedia animated fadeInUp">
        <a href="https://github.com/redouanefarah" target="_blank"
          ><i class="fab fa-github"></i
        ></a>
        <a
          href="https://www.linkedin.com/in/redouanefarah"
          target="_blank"
          ><i class="fab fa-linkedin"></i
        ></a>
      </div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
@import url("https://use.fontawesome.com/releases/v5.0.13/css/all.css");
.home-content {
  height: 90vh;
  display: flex;
  flex-direction: column;
  margin:auto 0;
  text-align: center;
  justify-content: center;
  align-content: center;
}
.img-container {
  height: 200;
  width: 200;
  align-self: center;
  margin: 0 auto;
  display: block;
  overflow: hidden;
  border-radius: 50%;
  text-align: center;
  animation-delay: 0.4s;
}
h4 {
  min-width: 100px;
  max-width: 300px;
  align-self: center;
  font-weight: normal;
  animation-name: moveInright;
  animation-duration: 2s;
  font-size: 14px;
  color: whitesmoke;
}
h1 {
  min-width: 100px;
  align-self: center;
  display: inline-block;
  animation-name: moveInleft;
  animation-duration: 2s;
  font-weight: normal;
  font-family: comfortaa;
  font-size: 30px;
  color: whitesmoke;
}
span {
  color: #ff4d5a;
}
@keyframes homeSkew {
  from {
    transform: translateY(50px) skewY(20deg);
  }
  50% {
    transform: translateY(0) skewY(20deg);
  }
  to {
    transform: skewY(0);
  }
}
@keyframes moveInleft {
  0% {
    opacity: 0;
    transform: translateX(-20px);
  }
  80% {
  }
  100% {
    opacity: 1;
    transform: translate(0);
  }
}
@keyframes moveInright {
  0% {
    opacity: 0;
    transform: translateX(20px);
  }
  80% {
  }
  100% {
    opacity: 1;
    transform: translate(0);
  }
}

.socialMedia {
  font-size: 16px;
  margin-top: 20px;
  a {
    color: white;
    padding: 8px;
  }
  a:hover {
    color: #ff4d5a;
  }
}

</style>
