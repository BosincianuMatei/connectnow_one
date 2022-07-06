<script>
import Home from './Home.vue'
import Contact from './Contact.vue'

const routes = {
	'/': Home,
	'/contact': Contact
}

export default {
	data() {
		return {
			currentPath: window.location.hash
		}
	},
	computed: {
		currentView() {
			return routes[this.currentPath.slice(1) || '/']
		}
	},
	mounted() {
		window.addEventListener('hashchange', () => {
			this.currentPath = window.location.hash
		})
	}
}
</script>

<template>
	<component :is="currentView" />
</template>

<style>

/*body element with Vertical linear gradient #081221 to #03080f*/

body {
	min-height:100vh;
	height:auto;
	background: -moz-linear-gradient(top, #081221,  #03080f);
	background: -webkit-linear-gradient(top, #081221, #03080f);
	background: linear-gradient(to bottom, #081221, #03080f);
}

/** Card panel background*/
.card-panel-background {
	background-color: #0e1a2b!important;
}

/** Text color*/
.text-color {
	color: #c1d1e8!important;
}

/*Headings / labels / buttons font-family*/
.HLB_font {
	font-family: 'Montserrat', sans-serif;
	color: #ffffff!important;
}

/**Input background color */
.input-background-color {
	background-color: #182c47!important;
}

/** Button color */
.button-color {
	background-color: #5692e8!important;
}
.button-text-color {
	color:#ffffff!important;
}

/**
RATING BADGE
*/
.notify-badge-small{
			display:none;
			position: absolute;
			right:10px;
			top:10px;
			background:#5692e8;
			text-align: center;
			border-radius: 30px 30px 30px 30px;
			color:white;
			width: 40px;
			height: 40px;
			padding: 5px 5px;
			font-size:20px;
}
.notify-badge-large{
			display: block;
			right:10px;
			top:10px;
			background:#5692e8;
			text-align: center;
			border-radius: 30px 30px 30px 30px;
			color:white;
			width: 40px;
			height: 40px;
			padding: 5px 5px;
			font-size:20px;
}

/** Basic elements */
input, .input-group, .btn, .form-select, .card  {
	border-radius: 0!important;
	border: 0px!important;
}

::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
	color: #c1d1e8!important;
	opacity: 1; /* Firefox */
}

:-ms-input-placeholder { /* Internet Explorer 10-11 */
	color: #c1d1e8!important;
}

::-ms-input-placeholder { /* Microsoft Edge */
	color: #c1d1e8!important;
}

a {
	text-decoration:none!important;
	color: #ffffff!important;
}

.form-select {
	background-image: url("https://upload.wikimedia.org/wikipedia/commons/9/9d/Caret_down_font_awesome_whitevariation.svg")!important;
}

textarea {
	border-radius:0px!important;
	border: 0px!important;
}

.clear_button {
	width: 10em;
  right: 0px;
  position: relative;
  float: right;
}

/** BREAKPOINTS */
/** // Small devices (landscape phones, 576px and up) */
@media (min-width: 320px){ 
	.clear_button {
		width: 100%;
	}

	.notify-badge-small{
			display:block;
			right:10px;
			top:10px;
			background:#5692e8;
			text-align: center;
			border-radius: 30px 30px 30px 30px;
			color:white;
			width: 40px;
			height: 40px;
			padding: 5px 5px;
			font-size:20px;
	}
	.notify-badge-large {
		display:none;
	}
 }
@media (min-width: 688px) { 
	.clear_button {
		width: 100%;
		top: 33px;
	}
}
/** // Medium devices (tablets, 768px and up) */
@media (min-width: 768px){ 
	.clear_button {
		width: 100%;
		top:0;
	}
	.notify-badge-small{
			display: block;
			right:10px;
			top:10px;
			background:#5692e8;
			text-align: center;
			border-radius: 30px 30px 30px 30px;
			color:white;
			width: 40px;
			height: 40px;
			padding: 5px 5px;
			font-size:20px;
	}

	.notify-badge-large {
		display:none;
	}
 }

/** // Large devices (desktops, 992px and up) */
@media (min-width: 992px) { 
	.clear_button {
		width: 100%;
	}
	.notify-badge-large{
			display: block;
			right:10px;
			top:10px;
			background:#5692e8;
			text-align: center;
			border-radius: 30px 30px 30px 30px;
			color:white;
			width: 40px;
			height: 40px;
			padding: 5px 5px;
			font-size:20px;
	}
	.notify-badge-small {
		display:none;
	}

 }

/** // X-Large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { 
	.clear_button {
		width: 10em;
	}
	.notify-badge-small{
			display:none;
	}
	.notify-badge-large{
			position: block;
			right:10px;
			top:10px;
			background:#5692e8;
			text-align: center;
			border-radius: 30px 30px 30px 30px;
			color:white;
			width: 40px;
			height: 40px;
			padding: 5px 5px;
			font-size:20px;
	}
 }

/** // XX-Large devices (larger desktops, 1400px and up) */
@media (min-width: 1400px) { 
	.notify-badge-small{
			display:none;
	}
 }
</style>
