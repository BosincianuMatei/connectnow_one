<template>
    <div class="container-fluid page_contact-container">
        <div class="d-flex flex-column justify-content-center align-items-center">
            <div class="col-md- 8 col-lg-4 col-lg-offset-5 col-md-offset-4">
                <div class="row">
                    <h4 class="HLB_font">
                        GET IN TOUCH
                    </h4>
                    <p class="text-color">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla quis convallis nulla. Maecenas euismod orci nisi, id commodo mauris varius a. Nam scelerisque diam lorem, eget tempus lorem placerat ac. Maecenas placerat porta varius. Integer eu aliquam diam, tempor congue elit. Praesent sed blandit sem, in posuere mauris. </p>
                </div>
                <div class="row">
                    <div class="card card-panel-background" style="padding:15px;">
                        <form>
                            <div class="row">
                                <h5 class="HLB_font">Contact Form</h5>
                            </div>
                            <br/>
                            <div class="row">
                                <div class="form-group col-md-6">
                                    <label for="name" class="HLB_font">Name *</label>
                                    <input type="text" class="form-control input-background-color text-color" id="name">
                                </div>
                                <div class="form-group col-md-6">
                                    <label for="email" class="HLB_font">Email Address *</label>
                                    <input type="email" class="form-control input-background-color text-color" id="email">
                                </div>
                            </div>
                            <br/>
                            <div class="row">
                                <div class="col-md-12">
                                    <label for="text" class="HLB_font">Message *</label>
                                    <textarea class="form-control input-background-color text-color" id="text" rows="3"></textarea>
                                </div>
                            </div>
                            <br/>
                            <button type="submit" class="btn button-color HLB_font clear_button">Send</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style>
.page_contact-container {
    top: 8em;
}

/** BREAKPOINTS */
/** // Small devices (landscape phones, 576px and up) */
@media (min-width: 320px){ 
    .page_contact-container {
        position:relative;
        margin-top: 0.5px;
        top: 5em;
    }
}

/** // Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { 

}

/** // Large devices (desktops, 992px and up) */
@media (min-width: 992px) { 

}
</style>