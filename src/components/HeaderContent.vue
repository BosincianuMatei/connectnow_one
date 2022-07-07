<template>
    <div class="container-fluid header-container">
        <div class="col-lg-10 offset-lg-1">
            <div class="row row-cols-auto">
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-5 col-xl-3">
                    <h1 class="HLB_font"><a href="#/">VIDEO</a> <span  class="shadow_text_video">VIDEO</span></h1>
                </div>
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-5 col-xl-3">
                    <h1 class="HLB_font"><a href="#/contact">CONTACT</a></h1>
                </div>
            </div>
        </div>
    </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .header-container {
        position: relative;
        height: 5em;
        top:5em;
    }
    .shadow_text_video {
        color: #182c47;
        position: absolute;
        font-family: 'Montserrat', sans-serif;
        font-size: 45pt;
        filter: blur(2px);
        top:-35px;
        left: 125px;
        z-index:-1;
    }

    .shadow_text_contact {
        color: #182c47;
        position: absolute;
        font-family: 'Montserrat', sans-serif;
        font-size: 45pt;
        filter: blur(2px);
        top:-35px;
        left: 460px;
        z-index:-1;
    }

/** BREAKPOINTS */
/** // Small devices (landscape phones, 576px and up) */
@media (min-width: 320px) { 
    .shadow_text_video {
        color: #182c47;
        position: absolute;
        font-family: 'Montserrat', sans-serif;
        font-size: 45pt;
        filter: blur(2px);
        top:-35px;
        left: 15px;
        z-index:-1;
    }
}

/** // Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { 
.header-container {
    height: 10em;
}
}

/** // Large devices (desktops, 992px and up) */
@media (min-width: 992px) { 
  
 }

/** // X-Large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { 
  
 }

/** // XX-Large devices (larger desktops, 1400px and up) */
@media (min-width: 1400px) { 
  
 }
</style>