<template>
  <div class="hero">
    <img src="../assets/jedi.png" alt="">
    <div class="center-content">
    <h1>{{ msg }}</h1>
    <h3>May the Force be with you</h3>
    <a href="#home-text" class="button">More info</a>
  </div>
  </div>
</template>

<script>
export default {
  name: 'Hero',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../mediaqueries.sass";
.hero {
  background-color: $hero;
  background-size: cover;
  background-position: center;
  width: 100wh;
  height: 90vh;
  display: flex;
  img{
    display: none;
    margin: 20px;
    margin-bottom: 10px;
    @include widescreen{
    display: flex;
  }
  }
  .center-content {
    width: 400px;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto;
    h1 {
      font-family: 'Bungee Shade', cursive;
      text-transform: uppercase;
      font-size: 4em;
      margin-bottom: 10px;
      text-align: center;
      color: white;
      line-height: 1;
    }
    h3 {
      margin-bottom: 40px;
      margin-top: 40px;
      font-size: 1.5em;
      font-weight: normal;
      color: white;
      line-height: 1;
    }
    .button {
      text-transform: uppercase;
      color: white;
      padding: 20px;
      border: 1px solid white;
      text-decoration: none;
      &:hover {
        background-color: rgba(255, 255, 255, 0.1);
        border-color: rgba(255, 255, 255, 0.7);
        color: $bcg-primary;
    }
    }
  }
}
</style>
