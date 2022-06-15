<template>

  <div class="window">
    <b-navbar class="navbar-custom" id="top" toggleable="lg">
      <img id="logo" src="../assets/LogoDark.png" alt="GeoGateway Logo" v-on:click="move_logo_right">


      <b-button class="miscButton" size="sm" @click="feedbackPopup=true">
        Feedback
      </b-button>

      <b-button class="miscButton" size="sm" @click="helpPopup=true">
        Help
      </b-button>
      <b-button size="sm" id="login" href="/auth/login">
        <b-icon-person></b-icon-person>
        Login
      </b-button>
    </b-navbar>

    <!-- feedback  popup -->
    <b-modal hide-backdrop
             v-model="feedbackPopup"
             title="Feed Back">
      <report/>
      <div slot="modal-footer" class="w-100">
      </div>

    </b-modal>

    <!-- help  popup -->
    <b-modal hide-backdrop
             v-model="helpPopup"
             title="Help">
      <help/>
      <div slot="modal-footer" class="w-100">
      </div>
    </b-modal>


  </div>

</template>

<script>
// import ToolBar from "./ToolBar";
import report from "./report"
import help from "./help"

export default {
  name: "TopNav",
  components: {
    // ToolBar
    report,
    help,
  },
  data() {
    return {
      feedbackPopup: false,
      helpPopup: false,
    };
  },
  methods: {
    loginRoute() {

    },
    move_logo_right: function () {
      var step = 50;
      var y = document.getElementById('logo').offsetLeft;
      y = y + step;
      document.getElementById('logo').style.left = y + "px";
    }
  }
}
</script>

<style scoped>
.navbar-custom {
  height: 40px;
  background: #FFFFFF;
  justify-content: right;
}

.window {
  background: #FFFFFF;
}

#logo {
  position: absolute;
  left: 0%;
  right: 0%;
  top: 0%;
  bottom: 0%;

  float: left;
  height: 30px;
  width: 100px;
}

#login {
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

}

.miscButton {
  background: none;
  border: none;
  font-family: Inter;
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 19px;
  display: flex;
  align-items: center;
  margin-left: 20px;
  margin-right: 20px;
  float: right;
  /* Primary text colour */

  color: #283237;
}
</style>
