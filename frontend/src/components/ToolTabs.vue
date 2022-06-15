<template>
  <div id="sidebar">
    <b-row>
      <b-col>
        <b-collapse v-model="navbar" visible>
          <b-tabs id="tabs" vertical v-model="tabIndex" small pills card>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>Map Tools</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>UAVSAR</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>GNSS</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>Seismicity</strong></span></template>
            </b-tab>
            <!-- <b-tab no-body><template #title> <span style="font-size:14px"><strong>Nowcast</strong></span></template></b-tab> -->
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>Magnitude</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>Disloc</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>Studies</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>3D Imaging</strong></span></template>
            </b-tab>
            <b-tab no-body>
              <template #title><span style="font-size:14px"><strong>Help</strong></span></template>
            </b-tab>

          </b-tabs>
        </b-collapse>
      </b-col>

      <b-col syle=" width: fit-content;">
        <b-button-group vertical v-if="navbar || toolbar">
          <b-button v-if="navbar" class="icon-btn is-right" syle="pointer-events: all;" @click="closeNav">
            <i class="fa fa-times" aria-hidden="true"></i>
          </b-button>
          <b-button v-if="!navbar" @click="navbar=true" class="nav-toggle"><i class="fas fa-bars"></i></b-button>
          <b-button v-if="toolbar" @click="closeBar()" class="bar-toggle"><i class="fas fa-angle-left"></i></b-button>
          <b-button v-if="!toolbar" @click="openBar()" class="bar-toggle"><i class="fas fa-angle-right"></i></b-button>
        </b-button-group>
      </b-col>
    </b-row>

  </div>
</template>

<script>
import 'vue-router'
import {bus} from '../main'
import L from 'leaflet'
import {mapFields} from 'vuex-map-fields';

export default {
  name: "ToolTabs",
  components: {},

  data() {
    return {
      tabIndex: 0,
      navbar: true,
      toolbar: true,
      toggleButton: null,
    }
  },

  created() {
    this.directUrl(this.tabUrl);
  },
  mounted() {
    bus.$on('ToggleNav', () =>
        this.navbar = true);

  },
  watch: {
    tabIndex: function (val) {
      bus.$emit('ToPage', val);
      bus.$emit('OpenBar');
    },
    tabUrl: function (val) {
      this.directUrl(val);
    }
  },
  computed: {
    tabUrl: function () {
      return this.$route.fullPath;
    },
    ...mapFields(['map.globalMap', 'map.layers'])
  },
  methods: {

    addToggle() {
      let vm = this;
      if (!vm.toolbar && !vm.navbar) {
        if (vm.toggleButton == null) {
          vm.toggleButton = L.control({position: 'topleft'});
          vm.toggleButton.onAdd = function () {

            var btn = L.DomUtil.create('button', 'toggle');
            btn.id = "toggleButton";
            btn.setAttribute("style", "text-align: center;  padding: 10px; border-radius: 5px; background: #FFFFFF;");
            btn.innerHTML = '<i class="fa-lg fas fa-bars" style="color: #2F7CF6;"></i>';
            btn.addEventListener("click",
                function () {
                  vm.globalMap.removeControl(vm.toggleButton);

                  vm.toggleButton = null;
                  vm.navbar = true;
                },
                false);
            return btn;

          }
          this.toggleButton.addTo(this.globalMap);
        }
      }
    },
    removeToggle() {
      this.navbar = true;
      bus.$emit("ToggleNav");
    },
    closeNav() {
      this.navbar = false;
      this.addToggle();
    },


    closeBar() {
      bus.$emit('CloseBar');
      this.toolbar = false;
      this.addToggle();
    },
    openBar() {
      bus.$emit('OpenBar');
      this.toolbar = true;
    },
    directUrl(page) {
      var index = null;
      this.toolbar = true;
      switch (page) {
        case "/maptools":
          index = 0;
          break;
        case "/uavsar":
          index = 1;
          break;
        case "/gnss":
          index = 2;
          break;
        case "/seismicity":
          index = 3;
          break;
          //case "/nowcast":
          //    index = 4;
          //    break;
        case "/momentmagnitude":
          index = 4;
          break;
        case "/disloc":
          index = 5;
          break;
        case "/specialstudies":
          index = 6;
          break;
        case "/3dimaging":
          index = 7;
          break;
        case "/report":
          index = 9;
          break;
        case "/help":
          index = 8;
          break;
      }
      if (this.tabIndex != index) {
        this.tabIndex = index;
      }
    },
  }
}
</script>

<style>

#sidebar {
  overflow-y: scroll;
  float: left;
  background-color: #FFFFFF;
  -webkit-transition: none;
  transition: none;
}

.nav {
  background-color: #FFFFFF;
}

#tabs {
  min-height: 100vh;
  background-color: #FFFFFF;

}

.tab-text {
  width: auto;
  position: relative;
  align-content: center;
  height: 100%;
  overflow: auto;

}


h3 {
  font-size: 20px !important;
}

.nav-pills .nav-link.active {
  background-color: #343a40;

}

.nav-link.tab {
  color: #343a40;
}

label {
  color: #343a40;
}

p {
  color: #343a40;
}

.bar-toggle {
  pointer-events: auto;
  color: #2F7CF6;
  background: transparent;
  border: none;
  height: 80vh;
}

.nav-toggle {
  color: #2F7CF6;
  background: #FFFFFF;
}

.icon-btn {
  background: transparent;
  border: none;
  color: #2F7CF6
}

button:active {
  outline: none;
  border: none;
  box-shadow: none;
}

button:focus {
  outline: none;
  border: none;
  box-shadow: none !important;
}

</style>
