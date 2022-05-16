<template>
  <div class="container">
      <div class="card">
          <div class="title">
              <div>Send Test</div>
              <div class="onCancel" @click="onCancelClick">
                  <font-awesome-icon icon="fa-solid fa-xmark" />
              </div>
          </div>
          <div class="avtar"></div>
          <div class="dot">{{this.cardData.short_name}}</div>
          <div class="profileLabel">{{this.cardData.name}}</div>
          <div class="addrLabel">{{this.cardData.address_1}},</div>
          <div class="addrLabel2">{{this.cardData.city}}, {{this.cardData.state_province}} {{this.cardData.postal_code}}, {{this.cardData.country}}</div>
          <div>
              <table style="width:100%" v-for="item in cardData.details" v-bind:key="item.ID" >
                  <tr>
                        <th>Guest ID</th>
                        <td class="value">{{item.ID}}</td>
                  </tr>
                  <tr>
                        <th>Email</th>
                        <td class="value">{{item.email}}</td>
                  </tr>
                  <tr>
                        <th>Phone</th>
                        <td class="value">{{item.phone}}</td>
                  </tr>
                  <tr>
                        <th>Fax</th>
                        <td class="value">{{item.fax}}</td>
                  </tr>
                  <tr>
                        <th>Status</th>
                        <td class="status">{{item.status}}</td>
                  </tr>
              </table>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  data () {
    return {
      cardData: []
    }
  },
  mounted () {
    fetch('http://localhost:3004/data', {
      headers: { 'Content-type': 'application/json' }
    })
      .then(response => response.json())
      .then((data) => { this.cardData = data[0] })
  },
  methods: {
    onCancelClick () {
      this.$router.replace('/')
    }
  }
}
</script>
<style scoped>
 .container{
    display:flex;
    justify-content: center;
    align-items: center;
}
.card {
  box-shadow: 0 4px 8px 4px rgba(0, 0, 0, 0.2);
  height:540px;
  width:400px;
  margin: auto;
  text-align: center;
  border-radius: 10px;
}
.title{
    height:20px;
    margin:10px;
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    font-family: sans-serif;
    font-weight: bold;
    color:black;
}
.avtar{
    width:100%;
    height:120px;
    background-color: #6eaff8;
}
.dot {
  height: 80px;
  width: 80px;
  line-height: 80px;
  background-color: #0e1eaf;
  border-radius: 50%;
  display: inline-block;
  margin-top:-50px;
  box-shadow: 0 0 0 5px #ffffff;
  color: #ffff;
  text-align: center;
  font-size: 26px;
  font-family: sans-serif;
}
.profileLabel{
    text-align: center;
    margin:12px 0px 8px 0px;
    color:black;
    font-weight: bold;
    font-family: sans-serif;
    font-size: 20px;
}
.addrLabel{
    text-align: center;
    margin: 0px 0px 8px 0px;
    font-family: sans-serif;
    font-weight: bold;
    font-size: 14px;
    color: #6E84A3
}
.addrLabel2{
    text-align: center;
    margin: 0px 0px 25px 0px;
    font-family: sans-serif;
    font-weight: bold;
    font-size: 14px;
    color: #6E84A3
}
.value{
    font-size: 14px;
    font-weight: bold;
    font-family: sans-serif;
    color: #6E84A3
}
.onCancel{
    cursor: pointer;
    color: #6E84A3;
}
.status{
    border: 1px solid gray;
    border-radius: 5px;
    border-color: #1867c0;
    background-color: #e2eaf2;
    color: green;
    font-size: 12px;
    padding: 2px;
}
tr{
    border-top: 2px solid #6E84A3;
    margin: 0px 24px 0px 24px;
    padding-top: 12px;
    padding-bottom: 12px;
    font-size: 14px;
    font-family: sans-serif;
    color: #12263f;
    font-weight: bold;
    display: flex;
    justify-content: space-between;
    width: 350px;
}
</style>
