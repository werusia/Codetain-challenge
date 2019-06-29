<template>
<div id="status">
  <h1>Total Power: {{totalPower()}} kW</h1>
  <div class="columns">
    <div class="column">
      <img v-bind:class="[getBackground(isActiveFalcon), getBorder(this.falcon)]" @click="[switchActive('falcon'), giveMorePower(falcon)]" src="../assets/falcon.png" alt="falcon">
      <p><strong>{{ falcon }}</strong> kW</p>
    </div>
    <div class="column">
      Click to give <br> more power!
    </div>
    <div class="column">
      <img v-bind:class="[getBackground(isActiveLight), getBorder(this.lightsaber)]" @click="[switchActive('lightsaber'), giveMorePower(lightsaber)]" src="../assets/light.png" alt="lightsaber">
      <p><strong>{{ lightsaber }}</strong> kW</p>
    </div>
  </div>
</div>
</template>
<script>
export default {
  name: 'Status',

  data: function() {
    return {
      isActiveFalcon: false,
      isActiveLight: false,
      falcon: 0,
      lightsaber: 0,
      apiUrl: 'https://challenge.codetain.com/api/v1/charging_status'
    }
  },
  methods: {
    getBackground(active) {
      return {
        'yellow': active
      }
    },
    switchActive(type) {
      switch (type) {
        case 'falcon':
          this.isActiveFalcon = !this.isActiveFalcon;
          if (this.isActiveFalcon) {
            this.isActiveLight = false;
          }
          break;
        case 'lightsaber':
          this.isActiveLight = !this.isActiveLight;
          if (this.isActiveLight) {
            this.isActiveFalcon = false;
          }
          break;
      }
  },
  getBorder(number) {
    return {
      'gray': number < 1,
      'green': number > 0
    }
  },
  totalPower() {
    return parseInt(this.falcon) + parseInt(this.lightsaber);
  },
  getData() {
    const axios = require('axios');
    axios
      .get(this.apiUrl)
      .then(response => (
        this.falcon = response.data.charging_status.falcon,
        this.lightsaber = response.data.charging_status.lightsaber))
  },
  giveMorePower(type) {
    if (type = 'falcon' && this.isActiveFalcon) {
      this.apiUrl = 'https://challenge.codetain.com/api/v1/charging_status?priority=falcon'
      this.$router.push({
        path: 'status',
        query: {
          priority: 'falcon'
        }
      });
    } else if (type = 'lightsaber' && this.isActiveLight) {
      this.apiUrl = 'https://challenge.codetain.com/api/v1/charging_status?priority=lightsaber'
      this.$router.push({
        path: 'status',
        query: {
          priority: 'lightsaber'
        }
      });
    } else {
      this.apiUrl = 'https://challenge.codetain.com/api/v1/charging_status'
      this.$router.replace({
        query: null
      });
    }
    this.getData()
  }
},
created() {
  this.getData()
  setInterval(() => {
    this.getData()
  }, 10000)
}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../mediaqueries.sass";
#status {
    margin-top: 40px;
    h1 {
        color: $status-red;
    }
}
.columns {
    @include mobile {
        flex-direction: column;
        margin: 20px 0;
    }
    display: flex;
    justify-content: space-around;
    margin: 100px;
    .column {
        img {
            @include mobile {
                width: 100px;
            }
            width: 200px;
            padding: 40px;
            border-radius: 50%;
        }
        p {
            margin-top: 20px;
            font-size: 24px;
        }
        strong {
            font-size: 36px;
        }
        &:nth-child(2){
          @include mobile {
            display: none;
          }
          font-size: 40px;
          align-self: center;
          font-family: 'Bungee Shade', cursive;
          line-height: 40px;
          margin: 20px;
        }
    }
}
.gray {
    border: 10px solid $status-gray;
}
.yellow {
    background-color: $bcg-yellow;
}
.green {
    border: 10px solid $status-green;
}
</style>
