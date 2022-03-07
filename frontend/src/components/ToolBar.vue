<template>
<div id="sidebar-1">
    <!--<b-button v-if="!toolbar" @click="removeToggle()" class="toggle"><i class="fas fa-bars"></i></b-button>-->
    <b-collapse id="toolbar" v-model="toolbar" visible>
    
    <div class = "row">
    <div class="col-sm-2" v-if="!nav">
    <b-button v-if="!nav" @click="removeToggle()" class="toggle"><i class="fas fa-bars"></i></b-button>
    </div>
        <div class="col">
            <b-card-text id="toolbarContent"><router-view></router-view></b-card-text>
        </div>
        <div class= "col-sm-2" syle=" width: fit-content;">
        <span class="icon is-right" syle="pointer-events: all;" @click=closeBar()>
            <i class="fa fa-times" aria-hidden="true"></i>
        </span>
        </div>
    </div>
    </b-collapse>
</div>
</template>

<script>
  import {bus} from '../main'
  import L from 'leaflet'
  import { mapFields } from 'vuex-map-fields';
  export default {
    name: "ToolBar",
     data (){
            return {
                toolbar: true,
                toggleButton: null,
                nav: true,
            }
        },
    mounted() {
      bus.$on('ToPage', (page) =>
        this.toPage(page));
        bus.$on('ToggleBar', () =>{
        if(!this.toolbar){
            
            //let vm = this;
            //vm.globalMap.removeControl(vm.toggleButton);
            this.toolbar = true;
            //vm.toggleButton = null;
        }
        });

        bus.$on('OpenBar', () =>{
            if(!this.toolbar){
                //let vm = this;
                //vm.globalMap.removeControl(vm.toggleButton);
                this.toolbar = true;
                //vm.toggleButton = null;
        }
        });
        bus.$on('navClosed', () =>{
            this.nav = false;
            this.addToggle();
        });
            
    },
  computed: {
          ...mapFields(['uavsar.overview', 'map.globalMap', 'map.layers', 'uavsar.overviewLegend'])
        },
    methods: {
        closeBar(){
            this.toolbar = false;
            this.addToggle();
        },
        addToggle(){
            let vm = this;
            if (!vm.toolbar && !vm.nav){
            console.log(this.toolbar);
            if (vm.toggleButton==null){
                
                vm.toggleButton = L.control({position: 'topleft'});
                
                vm.toggleButton.onAdd = function () {
                    var btn =  L.DomUtil.create('b-button', 'toggle');
                    btn.id = "toggleButton";
                    btn.innerHTML = '<i class="fas fa-bars"></i>';
                    btn.addEventListener ("click", 
                    function () {
                        vm.globalMap.removeControl(vm.toggleButton);
                        bus.$emit("ToggleNav");
                        vm.toggleButton = null;
                        vm.nav=true;
                    }, 
                    false);
                    return btn;
        }
            this.toggleButton.addTo(this.globalMap);
            }
            }
        },
        removeToggle(){
            this.nav = true;
            bus.$emit("ToggleNav");
        },
        toPage(page){
                var route ='';
                switch (page) {
                    case 0:
                        route = '/maptools';
                        break;
                    case 1:
                        route = '/uavsar';
                        if(!this.overview) {
                          this.overview = true;
                          this.uavsarOverview();
                        }
                        break;
                    case 2:
                        route = '/gnss';
                        break;
                    case 3:
                        route = '/seismicity';
                        break;
                    case 4:
                        route ='/nowcast';
                        break;
                    case 5:
                        route =  '/momentmagnitude';
                        break;
                    case 6:
                        route = '/disloc';
                        break;
                    case 7:
                        route= '/specialstudies';
                        break;
                    case 8:
                        route= '/3dimaging';
                        break;
                    case 9:
                        route = '/report';
                        break;
                    case 10:
                        route = '/help';
                        break;
                }
                if (this.$route.path !== route) {
                    this.$router.push(route)}
            },
            uavsarOverview(){
            this.layers['uavsarWMS'] = L.tileLayer.wms('https://archive.geo-gateway.org/geoserver/InSAR/wms?', {
                  layers: 'InSAR:thumbnailmosaic',
                  transparent: true,
                  format: 'image/png',
                  zIndex: 2
                }
            );
            this.overviewLegend = L.control({position: 'bottomleft'});
            this.overviewLegend.onAdd = function () {
              var div = L.DomUtil.create('div', 'overviewLegend');
              div.innerHTML = '<img src=' + 'https://raw.githubusercontent.com/GeoGateway/GeoGatewayStaticResources/master/kmz/uavsarlegend.png' + '>';
              return div;
            };
            this.overviewLegend.addTo(this.globalMap);

            this.globalMap.addLayer(this.layers['uavsarWMS'])
            this.layers['uavsarWMS'].setOpacity(.7);
          },
    },
  }
</script>

<style scoped>

    #sidebar-1 {
        height: 100%;
        //width: 27%;
        width: fit-content;
        overflow-y: scroll;
        float: left;
        background: none;
        -webkit-transition: none;
        transition: none;
    }

    #toolbar{
    }

    .toggle{
        pointer-events: auto;
        color: #2F7CF6;
        background: #FFFFFF;
    }
    #close{
        width: fit-content;
    }
    #toolbarContent{
                margin-top:3%;
    }


</style>