<template>
  <div class="projects-container">
    <div class="projects-content">
      <div class="header">
        <div class="fadeInDown animated">
          <button
            :class="{ 'active-btn': projects == 1 }"
            @click="projects = 1"
          >
            <i class="fas fa-desktop" style="font-size: 18px;"></i>
            <p style="font-size: 10px; font-family:comfortaa;">WEB</p>
          </button>
          <button
            :class="{ 'active-btn': projects == 2 }"
            @click="projects = 2"
          >
            <i class="fas fa-mobile" style="font-size: 18px;"></i>
            <p style="font-size: 10px;font-family:comfortaa;">MOBILE</p>
          </button>
        </div>
      </div>
      <!-- WEB -->

      <div class="container" v-if="projects == 1">
        <div class="row">
          <dir class="col-sm-12 col-md-6 col-lg-4 col-xl-4 zoomIn animated">
            <div class="card-cover ">
              <a
                href="https://redouanetictactoegame.herokuapp.com/"
                target="_blank"
                class="animated fadeInUp"
              >
                <img class="A" src="../assets/game.png" alt="" />
                <img class="B" src="../assets/game-hover.png" alt="" />
              </a>
            </div>
          </dir>
          <dir class="col-sm-12 col-md-6 col-lg-4 col-xl-4 zoomIn animated">
            <div class="card-cover ">
              <a
                href="https://redouanewebsite.herokuapp.com/"
                target="_blank"
                class="animated fadeInUp"
              >
                <img class="A" src="../assets/website.png" alt="" />
                <img class="B" src="../assets/website-hover.png" alt="" />
              </a>
            </div>
          </dir>
          <dir class="col-sm-12 col-md-6 col-lg-4 col-xl-4 zoomIn animated">
            <div class="card-cover ">
              <a
                href="https://github-trending-repositories.herokuapp.com/"
                target="_blank"
                class="animated fadeInUp"
              >
                <img class="A" src="../assets/github.png" alt="" />
                <img class="B" src="../assets/github-hover.png" alt="" />
              </a>
            </div>
          </dir>
        </div>
      </div>
      <!-- MOBILE -->
      <div class="container " v-if="projects == 2">
        <div class="row">
          <!------------------------------------------------------------------------------------------------- -->
          <dir class="col-sm-12 col-md-6 col-lg-4 col-xl-4 zoomIn animated">
            <div class="mobile-cover ">
              <a href="" target="_blank" class="animated fadeInUp">
                <img src="../assets/Iphone.png" alt="" />
              </a>
            </div>
          </dir>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "projects",
  data() {
    return {
      projects: 1,
    };
  },
};
</script>

<style lang="scss" scoped>
.projects-container {
  a {
    color: #fff;
    text-decoration: none;
  }
}

.projects-content {
  box-sizing: border-box;
  margin: auto;
}

.header {
  text-align: center;
  margin-left: 50%;
  transform: translate(-50%);
  margin-bottom: 30px;

  button {
    background-color: transparent;

    text-align: center;
    border: none;
    cursor: pointer;
    outline: none;
    font-size: 20px;

    margin-left: 0px;
    color: #474747;
  }

  .active-btn {
    background-color: transparent;

    text-align: center;
    border: none;
    cursor: pointer;
    outline: none;

    margin-left: 0px;
    color: #ff4d5a;
  }
}
.container {
  padding-right: 0px;
  padding-left: 0px;
  width: fit-content;
}
.card-cover {
  width: 320px;
  height: 200px;
  text-align: center;
  justify-self: center;
  margin: 0 auto;
  img {
    height: auto;
  }
  .B {
    display: none;
  }
}

.card-cover:hover {
  .A {
    display: none;
  }
  .B {
    display: block;
  }
}

.mobile-cover {
  align-self: center;
  text-align: center;
  margin: 0 auto;
  img {
    height: 270px;
  }
}

.active-btn {
  background: royalblue;
  transition: all 0.2s;
}

@media (max-width: 1069px) {
  .projects-content {
    padding-top: 90px;
  }
}

@media (max-width: 460px) {
  .projects-content {
    padding-right: 0;
    padding-left: 0;

    .header {
      padding: 0 20px;
      box-sizing: border-box;
    }
  }
}
</style>
