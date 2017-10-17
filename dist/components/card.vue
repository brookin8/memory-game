<template>
	<div class="card" 
		v-bind:class="cardNum"
		v-on:click ="reportClick(cardNum)"></div>
</template>

<script>

	export default {

		name : 'card', 
		props : [ 'cardNum'],
		methods : {
			reportClick : function(cardNum) {
			this.$emit('cardClicked', cardNum);

			}
		}
	}

</script>

<style>
	.card {
		margin : 5px;
		border : 2px solid #000;
		width : 125px;
		height : 125px;
		background-color : #DBC970;
		display : inline-block;
		box-shadow:inset 0 0 0 2000px rgba(255, 255, 148,1);
		background-size: cover;
	}

	

</style>