<template>
    <div class="container-fluid page_content-container">
        <div class="row">
            <!---SEARCH CONTENT--->
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-2 col-xl-2 offset-lg-1">
                    <div class="card card-panel-background" style="padding:15px">
                        <div class="row">
                            <h3 class="HLB_font">Filter Results</h3>
                        </div>
                        <!---SEARCH FORM-->
                        <div class="row">
                            <form v-on:submit="submitForm">
                                <!--Name search (input)-->
                                <div class="row">
                                <div class="mb-3 col-xs-4">
                                    <label for="name_search" class="form-label  HLB_font">Name (contains)</label>
                                    <input type="input" class="form-control input-background-color text-color" v-model="searchQueryName" @input="onInput()" id="name_search" placeholder="Text string">
                                </div>
                                </div>
                                <div class="row">
                                <!--Minimum Score -->
                                    <div class="col-xs-12 col-sm-4 col-md-12 col-lg-12">
                                        <label for="minimum_score_search" class="form-label HLB_font">Minimum Score</label>
                                        <input type="number" class="form-control input-background-color text-color" 
                                            v-model="searchQueryMinScore"
                                            @input="onInput()"
                                            maxlength = "10" id="minimum_score_search" placeholder="1 - 10">
                                    </div>

                                    <!--Order By-->
                                    <div class="col-xs-12 col-sm-4 col-md-12 col-lg-12">
                                    <label for="order_by" class="form-label HLB_font">Order By</label>
                                    <div class="input-group mb-3">
                                        <button class="btn btn-outline-secondary button-color" type="button" id="button-sort" v-on:click="changeSortOrder">
                                            <i class="text-color bi" v-bind:class="[arrowClass]"></i>
                                        </button>
                                        <select class="form-select input-background-color text-color" id="order_by" aria-label="select" v-model="searchQueryOrderBy" @change="handleChange">
                                            <option value="0">Release Date</option>
                                            <option value="1">Score</option>
                                            <option value="2" selected>Name</option>
                                        </select>
                                    </div>
                                    </div>

                                    <!--Clear Button-->
                                    <div class="col-xs-12 col-sm-4 col-md-12 col-lg-12">
                                        
                                            <button class="btn button-color HLB_font clear_button">Clear</button>
                                        
                                    </div>
                                
                                </div>
                            </form>
                        </div>
                    <!---SEARCH FORM-->
                    </div>
                </div>
            <!---SEARCH CONTENT--->

            <!--DISPLAY CONTENT-->
           
                <!--GAME INFO CONTAINER-->
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-8 col-xl-8 container-data">
                    <div class="d-flex flex-column justify-content-center align-items-center">
                        <img class=".loader" v-if="loading" src="@/assets/loader.gif" style="widht:60px; height: 60px;"/>
                    </div>
                    <div v-for="(game,index) in games" :key="index" class="card card-panel-background" id="card" style="max-width:100%; max-height: 15rem; margin-bottom:0.5em;">
                        <div class="row g-0">
                            <div class="col-xs-12 col-sm-12 col-md-2 col-lg-1">
                                <span class="notify-badge-small HLB_font"> {{ game.rating }}</span>
                                <div class="card-img-custom"></div>
                            </div>
                            <div class="col-xs-12 col-sm-12 col-md-8 col-lg-8">
                                <div class="card-body">
                                    <h4 class="card-title HLB_font"> {{ game.name }}
                                        <br/>
                                        <small>Release Date: {{ game.first_release_date }}</small>
                                    </h4>
                                    <p class="card-text text-color ellipsis">{{ game.summary }}</p>
                                </div>
                            </div>
                            <div class="col-sm-2 col-md-2 col-lg-2 col-xl-2 d-flex justify-content-center align-items-center">
                                <span class="notify-badge-large HLB_font">{{ game.rating }}</span>
                            </div>
                        </div>
                    </div>
                    <!--GAME INFO CONTAINER-->
                </div>
            <!--DISPLAY CONTENT-->
        </div>
    </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page_content-container {
    top: 8em;
}
.card-img-custom {
    display:block;
    background-color: #000000;
    width: 100%;
    height: 100%;
    
}
small {
    font-size: .65em;
}
.ellipsis {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
}

/** BREAKPOINTS */
/** // Small devices (landscape phones, 576px and up) */
@media (min-width: 320px){ 
    .page_content-container {
        position:relative;
        margin-top: 0.5px;
        top: 5em;
    }

    .card-img-custom {
        display:block;
        background-color: #000000;
        width: 100%;
        height: 7.5em;
    }

    .ellipsis {
        display: -webkit-box;
        -webkit-line-clamp: 1;
        -webkit-box-orient: vertical;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .container-data {
    position: relative;
    top:1em;
  }
}

/** // Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { 

    .container-data {
        position: relative;
        top:1em;
    }
}

/** // Large devices (desktops, 992px and up) */
@media (min-width: 992px) { 
    .container-data {
        position: relative;
        top:0em;
    }
}

</style>

<script>

import moment from 'moment'
export default {
  data () {
    return {
        // searchQueryName = gets value from name input
        searchQueryName: null,
        // searchQueryMinScore = gets value from min score input
        searchQueryMinScore: null,
        // searchQueryOrderBy = gets value from order by input
        searchQueryOrderBy: null,
        // games will be used for displaying games in DOM
        games: null,
        // filteredGames will be used to filter games by inputs
        filteredGames: null,
        // originalGames will store response from async GET
        originalGames: null,
        // sortedGames will be used to sort games
        sortedGames: null,
        loading: true,
        arrowClass: "bi-arrow-up",
        // currentIcon is used to store info about user option in sorting asc/desc
        currentIcon: 0,
        valueSelected: 
    }
  },
  async created () {
    this.loading = true;
    const response = await fetch("https://public.connectnow.org.uk/applicant-test/")
    
    const result = await response.json()
    // format score and date
    Object.keys(result).forEach(function(k){
        // format score
        result[k]['rating'] = Math.round(result[k]['rating'] / 10);
        // format date
        result[k]['timestamp'] = result[k]['first_release_date'];
        result[k]['first_release_date'] = moment(result[k]['first_release_date']).format('DD/MM/YYYY');
    });
    
    this.loading = false;
    
    this.games = result
    this.originalGames = result
  },
  methods: {
    onInput: function (){
    var filteredGames = this.originalGames;

    console.log(this.searchQueryName);
    console.log(this.searchQueryMinScore);
    
    
    if(this.searchQueryName || this.searchQueryMinScore || this.searchQueryOrderBy){
        // search name
        if(this.searchQueryName){
            filteredGames =  filteredGames.filter((item)=>{
                return this.searchQueryName.toLowerCase().split(' ').every(v => item.name.toLowerCase().includes(v))
            })
            console.log(filteredGames);
        } else if (!this.searchQueryName) {
            filteredGames = this.originalGames;
        }
        // search min score 
        if(this.searchQueryMinScore){
            filteredGames =  filteredGames.filter((item)=>{
                return item.rating >= this.searchQueryMinScore
            })
            console.log(filteredGames);
        }
       
        this.games = filteredGames;
    } else {
        return this.games;
    }
    
    },
    handleChange(e) {

        /**
         * On select change will sort the results that are displayed in DOM
         * valueSelected shows if sorting is asc/desc
         */
        var sortedGames = this.games;
        if(e.target.options.selectedIndex > -1) {
            var valueSelected = e.target.options[e.target.options.selectedIndex].value;
            if(valueSelected == 0) {
                if(!this.currentIcon) 
                    sortedGames =  sortedGames.slice().sort(function(a, b){
                        return (a.timestamp > b.timestamp) ? 1 : -1;
                    });
                else 
                    sortedGames =  sortedGames.slice().sort(function(a, b){
                        return (a.timestamp < b.timestamp) ? 1 : -1;
                    });
            } else if(valueSelected == 1) {
                if(!this.currentIcon) 
                    sortedGames =  sortedGames.slice().sort(function(a, b){
                        return (a.rating > b.rating) ? 1 : -1;
                    });
                else
                    sortedGames =  sortedGames.slice().sort(function(a, b){
                        return (a.rating < b.rating) ? 1 : -1;
                    });
            } else if(valueSelected == 2) {
                if(!this.currentIcon)
                    sortedGames =  sortedGames.slice().sort(function(a, b){
                        return (a.name > b.name) ? -1 : 1;
                    });
                else 
                    sortedGames =  sortedGames.slice().sort(function(a, b){
                        return (a.name < b.name) ? -1 : 1;
                    });
            }

            //console.log(this.games);
            this.games = sortedGames;
        }
    },

    submitForm(e){
        /**
         * Will reset form and display original values without another async GET
         */
        this.searchQueryName = "";
        this.searchQueryMinScore = "";
        this.searchQueryOrderBy = "";
        // To prevent the form from submitting
        e.preventDefault();

        this.games = this.originalGames;

    },

    changeSortOrder(){
        /**
         * Changes arrow on Order By
         * 
         */
        if(!this.currentIcon) {
            this.currentIcon = 1;
            this.arrowClass = "bi-arrow-down";
        } else {
            this.currentIcon = 0;
            this.arrowClass = "bi-arrow-up";
        }
        
    }
  },
  
}


</script>