<template>
  <div id="home-text">
    <div v-for="tab in tabs" class="section">
    <img src="../assets/star.svg" alt="">
      <div class="title">{{tab.title}}</div>
      <div class="text">{{tab.text}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeText',
  data: function () {
       return {
         tabs: [
        {
          title: 'Millennium Falcon',
          text: 'Its aged appearance belied numerous advanced modifications to boost the ships speed, weapons, and shield.',
          animation: 'fade-right'
        },
        {
          title: 'Lightsaber',
          text: 'Lightsabers consist of a plasma blade, powered by a kyber crystal, that was emitted from a usually metal hilt and could be shut off at will',
          animation: 'fade-up'
        },
        {
          title: 'CP3O',
          text: 'He was fluent in over seven million forms of communication, and developed a fussy and worry-prone personality.',
          animation: 'fade-down'
        }
      ]
       }
     }
}
</script>


<style scoped lang="scss">
@import "../mediaqueries.sass";
#home-text{
  @include mobile{
    flex-direction: column;
    margin: 0;
}
  display: flex;
  margin: 100px;
  align-items: center;
  img{
    width: 10%;
  }
  .section{
    justify-content: space-evenly;
    margin: 50px;
    flex-grow: 1;
    flex-basis: 0;
    .title{
      font-weight: bold;
      font-size: 30px;
      margin: 20px 0;
    }
    .text{
      @include section-shadow;
      padding: 30px;
      line-height: 25px;
      background-color: $bcg-blue;
    }
  }
}
</style>
