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
		border : 2px solid #fffcf0;
		width : 125px;
		height : 125px;
		background-color : #fbd14b;
		display : inline-block;
		box-shadow:inset 0 0 0 2000px rgba(251, 209, 75, 1);
		background-size: cover;
	}

	

</style>