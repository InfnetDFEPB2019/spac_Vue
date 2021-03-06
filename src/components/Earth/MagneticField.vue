<template>
    <div>
        <div id="divContentHolderMagneticField">
            <Header/>
            <section id="sectionMagneticField">
                <div>
                    <b-row class="contentTitle">
                        <b-img class="imageSection" src="https://raw.githubusercontent.com/christianvajgel/spa_c_assets/master/images/space_weather.png"
                               height="75" width="75" alt="magnetic field icon section"></b-img>
                        <p class="titleSection">MAGNETIC FIELD</p>
                    </b-row>
                </div>

                <div>
                    <table class="borderTable tableMagneticField">
                        <tr>
                            <td>
                                <b-img v-b-popover.hover.top.v-dark="{ content: magneticDeclination }"
                                       src="https://raw.githubusercontent.com/christianvajgel/spa_c_assets/master/images/compass.png"
                                       height="50" width="50" alt="magnetic declination icon"></b-img>
                            </td>
                            <td>
                                <b-img v-b-popover.hover.top.v-dark="{ content: magneticInclination }"
                                       src="https://raw.githubusercontent.com/christianvajgel/spa_c_assets/master/images/inclination.png"
                                       height="50" width="50" alt="magnetic inclination icon"></b-img>
                            </td>
                            <td>
                                <b-img v-b-popover.hover.top.v-dark="{ content: magneticTotal_intensity }"
                                       src="https://raw.githubusercontent.com/christianvajgel/spa_c_assets/master/images/intensity.png"
                                       height="50" width="50" alt="magnetic field total intensity icon"></b-img>
                            </td>
                        </tr>
                        <tr>
                            <td>
                                <p>Declination <sup>({{ allMagneticFieldData.declination.units }})</sup></p>
                                <p class="pCenterAlignment">{{ (allMagneticFieldData.declination.value).toFixed(3) }}</p>
                            </td>
                            <td>
                                <p>Inclination <sup>({{ allMagneticFieldData.inclination.units }})</sup></p>
                                <p class="pCenterAlignment">{{ (allMagneticFieldData.inclination.value).toFixed(3) }}</p>
                            </td>
                            <td>
                                <p>Total Intensity <sup>({{ allMagneticFieldData.total_intensity.units }})</sup></p>
                                <p class="pCenterAlignment">{{ (allMagneticFieldData.total_intensity.value).toFixed(3) }}</p>
                            </td>
                        </tr>
                    </table>
                </div>
                
            </section>
            <Footer/>
        </div>
    </div>
</template>

<script>
    import Glossary from "@/components/Glossary";
    import Header from "@/components/Header";
    import Footer from "@/components/Footer";
    import { mapGetters, mapActions } from "vuex";
    export default {
        name: "MagneticField",
        components: {Footer, Header},
        methods: {
            ...mapActions(["getMagneticFieldData"]),
        },
        computed:
            mapGetters(["allMagneticFieldData"]),
        created() {
            this.getMagneticFieldData();
        },
        data(){
            return {
                magneticDeclination:Glossary.methods.data().magneticDeclination,
                magneticInclination:Glossary.methods.data().magneticInclination,
                magneticTotal_intensity:Glossary.methods.data().magneticTotal_intensity
            }
        }
    }
</script>

<style scoped>

    .pCenterAlignment {
        margin: 5px auto !important;
    }

    .imageSection {
        margin-left: 50px;
    }

    .titleSection {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: left !important;
        font-size: 30px;
        margin-left: 25px;
        margin-top: 10px !important;
        align-self: self-end;
    }

    .contentTitle {
        margin-top: 5px !important;
        margin-left: 25px !important;
    }

    .row {
        margin: 0;
    }

    .form-row  {
        margin: 0;
    }

    #divContentHolderMagneticField {
        position: relative;
    }
    
    .bg-b-table-default {
        background-color: #181818 !important;
    }

    #sectionMagneticField {
        margin-bottom: 25px !important;
    }

    .tableMagneticField {
        margin: 0 auto !important;
        margin-top: 40px !important;
    }

</style>