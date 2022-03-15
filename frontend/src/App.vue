<template>
    <div id="app">
      <router-view name="mainPage"/>
    </div>
</template>

<script>

    import 'vue-router';
    import {bus} from './main';
    export default {
        name: 'app',
        
        mounted(){
            bus.$on('switchPage',  (feature)=>{
                try{
                   this.$router.push(feature);
                }
                catch (e) {
                    console.log(e.name);
                    if (e.name != 'NavigationDuplicated') {throw e}
                }
                
            });
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        width: 100%;
        min-height: 100vh;
    }
    .toolInfo {
      width: auto;
      height: auto;
      border: 2px solid #3388ff;
      box-sizing: border-box;
      border-radius: 8px;
      background-color: #bad7ff;
    }
    .overviewButtonGroup .active {
      color: #fff !important;
      background-color: #3388ff !important;
      border-color: #3388ff !important;

    }
    .tab-window {
    background: #F5F9FB;
    height:100%;
    overflow-x: hidden;
    overflow-y: hidden;
    padding-left: 20px;
    width: max-content;
    
    }
    .aboutIcon{
        color: #2F7CF6;
    }
    .inputLabel{
        left: 0%;
        font-family: Inter;
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 19px;
        display: flex;
        align-items: center;
        color: #95ABB1;
        margin-top: 10px;
    }

    .btn_blue{
        background: #2F7CF6;
        box-shadow: 0px 4px 5px rgba(217, 229, 235, 0.5);
        border-radius: 5px;
        font-family: Inter;
        font-style: normal;
        font-weight: 600;
        font-size: 16px;
        line-height: 19px;
        color: #FFFFFF;
    }


.btn_white{
  background: #FFFFFF;
  border: 1px solid #A2B8BF;
  box-sizing: border-box;
  border-radius: 5px;
  font-family: Inter;
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 19px;
  color: #2F7CF6;
}
.center{
    text-align: center;
}
.orange{
width: 46px;
height: 15px;
left: 30px;
top: 253px;
font-family: Inter;
font-style: normal;
font-weight: bold;
font-size: 12px;
line-height: 15px;
display: flex;
align-items: center;
text-transform: uppercase;
color: #EB9040;
}
.green{
  font-family: Inter;
font-style: normal;
font-weight: bold;
font-size: 12px;
line-height: 15px;
display: flex;
align-items: center;
text-transform: uppercase;
color: #60B56C;
}
.red{
font-family: Inter;
font-style: normal;
font-weight: bold;
font-size: 12px;
line-height: 15px;
display: flex;
align-items: center;
text-transform: uppercase;
color: #E9637D;

}

</style>
