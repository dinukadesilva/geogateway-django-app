<template>
<div id="sidebar">
    
        <b-collapse v-model="navbar" visible>
        <div class="row">
        <div class="col">
        <b-tabs id="tabs" vertical v-model="tabIndex" small pills card>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Map Tools</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>UAVSAR</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>GNSS</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Seismicity</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Nowcast</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Magnitude</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Disloc</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Studies</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>3D Imaging</strong></span></template></b-tab>
            <!--
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Feedback</strong></span></template></b-tab>
            <b-tab no-body><template #title> <span style="font-size:14px"><strong>Help</strong></span></template></b-tab>
            -->
        </b-tabs>
        </div>
        <div class= "col-sm" syle=" width: fit-content;">
        <span class="icon is-right" syle="pointer-events: all;" @click="addToggle()">
            <i class="fa fa-times" aria-hidden="true"></i>
        </span>
        </div>
        
           </div>
        </b-collapse>
        

</div>
</template>

<script>
    import 'vue-router'
    import {bus} from '../main'
    //import L from 'leaflet'
    //import { mapFields } from 'vuex-map-fields';
    export default {
        name: "ToolTabs",
        components: {
        },
        
        data (){
            return {
                tabIndex: 0,
                navbar: true,
            }
        },
        
        created() {
            this.directUrl(this.tabUrl);
        },
        mounted(){
            bus.$on('ToggleNav', () =>
            this.navbar = true);
            
        },
        watch: {
            tabIndex: function(val){
                //this.toPage(val);
                bus.$emit('ToPage', val);
                bus.$emit('OpenBar');
            },
            tabUrl: function(val){
                this.directUrl(val);
            }
        },
        computed: {
            tabUrl: function(){
                return this.$route.fullPath;
            },
          //...mapFields(['uavsar.overview', 'map.globalMap', 'map.layers', 'uavsar.overviewLegend'])
        },
        methods: {

            addToggle(){
                this.navbar= false;
                bus.$emit("navClosed");
            },
            directUrl(page) {
                var index = null;
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
                    case "/nowcast":
                        index = 4;
                        break;
                    case "/momentmagnitude":
                        index = 5;
                        break;
                    case "/disloc":
                        index = 6;
                        break;
                    case "/specialstudies":
                        index = 7;
                        break;
                    case "/3dimaging":
                        index = 8;
                        break;
                    case "/report":
                        index = 9;
                        break;
                    case "/help":
                        index = 10;
                        break;
                }
                if (this.tabIndex!=index){
                    this.tabIndex = index;
                }
            },
        }
    }
</script>

<style >

#sidebar {
        overflow-y: scroll;
        float: left;
        background-color: #FFFFFF;
        -webkit-transition: none;
        transition: none;
    }
.nav{
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
        height: 100% ;
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
        color: #343a40 ;
    }
    p {
        color: #343a40;
    }
</style>
