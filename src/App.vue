<template>
  <div>
    <div class="container">
      <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
      <div id="nav">
        <div class="logo">
          <img alt="Vue logo" src="@/assets/logo.png" />
        </div>
        <div class="centro">
          <input type="text" name="cerca" id="cerca" placeholder="Cerca" />
        </div>
        <div class="destra">
          <i class="far fa-heart"></i>
          <i class="fas fa-home"></i>
          <img alt="Vue logo" src="@/assets/profile.jpg" />
        </div>
      </div>
    </div>
    <hr />
    <router-view />
  </div>
</template>



<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.container {
  max-width: 1170px;
  margin: auto;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 0.5rem 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .logo {
    img {
      height: 30px;
    }
  }

  .centro {
    input {
      height: 25px;
      width: 250px;
      border-radius: 0.25rem;
      border: 1px solid rgba(0, 0, 0, 0.342);
      text-align: center;
    }
  }

  .destra {
    display: flex;
    align-items: center;
    i {
      font-size: 20px;
      margin-right: 15px;
    }
    img {
      height: 40px;
      width: 40px;
      border-radius: 50%;
    }
  }
}
</style>
