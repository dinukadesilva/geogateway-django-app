<template>

    <div class="window" >
        <b-navbar class="navbar-custom" id="top" toggleable="lg" >
                <img id="logo" src="../assets/LogoDark.png" alt="GeoGateway Logo" v-on:click="move_logo_right">
         

           <b-button class="miscButton" size="sm">
            Feedback
          </b-button>

           <b-button class="miscButton" size="sm" >
            Help
          </b-button>
           <b-button size="sm" id="login" href="/auth/login">
            <b-icon-person></b-icon-person>Login
          </b-button>
        </b-navbar>
    </div>

</template>

<script>
    // import ToolBar from "./ToolBar";
    export default {
        name: "TopNav",
        components: {
            // ToolBar
        },
      methods: {
          loginRoute(){

          },
          move_logo_right: function () { 
              var step = 50;
              var y=document.getElementById('logo').offsetLeft;
              y= y + step;
              document.getElementById('logo').style.left= y + "px";
          }
      }
    }
</script>

<style scoped>
.navbar-custom {
  height: 40px;
  background: #FFFFFF;
}
.window{
    background: #FFFFFF;
}

#logo {
    //position: absolute;
    //left: 75%;

    
    left: 0%;
    right: 0%;
    top: 0%;
    bottom: 0%;

    float: top;
    height: 30px;
    width: 100px;
}

#login{
    color: #2F7CF6;
    background: #FFFFFF;
border: 1px solid #A2B8BF;
box-sizing: border-box;
border-radius: 5px;
display: flex;
align-items: flex-start;

font-family: Inter;
font-style: normal;
font-weight: 600;
font-size: 16px;
line-height: 19px;
display: flex;
align-items: center;

position: absolute;
left: 89.61%;
right: 2.32%;
top: 21.43%;
bottom: 21.43%;

}
.miscButton{
    background: none;

    font-family: Inter;
font-style: normal;
font-weight: 600;
font-size: 16px;
line-height: 19px;
display: flex;
align-items: center;

/* Primary text colour */

color: #283237;
}
</style>
