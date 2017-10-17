<template>

<div class = "board">
	
	<card v-for="card in cards" v-on:cardClicked = "catchCard(card)" v-bind:class="{ 'active' : card.active }" v-bind:style="{ 'background-image': 'url(' + images[card.number] + ')' }" />


</div>
</template>

<script>
	import card from './card.vue';

	export default {

		name : 'board', 
		
		beforeMount : function() {
			 var currentIndex = this.images.length, temporaryValue, randomIndex;

  				while (0 !== currentIndex) {
    				randomIndex = Math.floor(Math.random() * currentIndex);
    				currentIndex -= 1;

    				temporaryValue = this.images[currentIndex];
    				this.images[currentIndex] = this.images[randomIndex];
    				this.images[randomIndex] = temporaryValue;
  				}

  			return this.images;


		},

		components : {
			card
		},


		data () {
		    return {

		    images : [ 
		    'https://i.pinimg.com/736x/96/29/b5/9629b50ad4a48f2d19e98daec6019296--funny-cards-valentine-cards.jpg',
		    'https://i.pinimg.com/736x/96/29/b5/9629b50ad4a48f2d19e98daec6019296--funny-cards-valentine-cards.jpg', 
		    'http://buzzsharer.com/wp-content/uploads/2015/04/You-Are-A-Crazy-Dog-Person.jpg', 
		    'http://buzzsharer.com/wp-content/uploads/2015/04/You-Are-A-Crazy-Dog-Person.jpg', 
		    'http://dabusblog.com/wp-content/uploads/2012/04/buddha-pug.jpg',
		    'http://dabusblog.com/wp-content/uploads/2012/04/buddha-pug.jpg',
		    'https://i.pinimg.com/736x/67/f4/a3/67f4a3f7b56f430f01e92a7795f36ac9--pet-halloween-costumes-animal-costumes.jpg',
		    'https://i.pinimg.com/736x/67/f4/a3/67f4a3f7b56f430f01e92a7795f36ac9--pet-halloween-costumes-animal-costumes.jpg',
		    'http://i.imgur.com/gTC7wnF.jpg',
		    'http://i.imgur.com/gTC7wnF.jpg',
		    'https://thewondrous.com/wp-content/uploads/2015/08/cute-funny-pug-pictures.jpg',
		    'https://thewondrous.com/wp-content/uploads/2015/08/cute-funny-pug-pictures.jpg',
		    'https://i.pinimg.com/736x/26/ff/5d/26ff5d59a8491038cd7a8778cb6c2867--pug-dogs-puppies.jpg',
		    'https://i.pinimg.com/736x/26/ff/5d/26ff5d59a8491038cd7a8778cb6c2867--pug-dogs-puppies.jpg',
		    'https://blog-cdn.dogbuddy.com/wp-content/uploads/2015/12/hilarious-dog-takes-internet-by-storm-9e873f7ce5.jpg',
		    'https://blog-cdn.dogbuddy.com/wp-content/uploads/2015/12/hilarious-dog-takes-internet-by-storm-9e873f7ce5.jpg',
		    'https://i.pinimg.com/originals/0c/cf/50/0ccf501ebd357e13c57af9bc92312fe2.jpg',
		    'https://i.pinimg.com/originals/0c/cf/50/0ccf501ebd357e13c57af9bc92312fe2.jpg',
		    'http://1.bp.blogspot.com/-mY6qoFR2V44/TgqC6OCT7oI/AAAAAAAAEcs/S0HqhA5Eq0c/s1600/Gadget_the_pug_expressive_eyes.jpg',
		    'http://1.bp.blogspot.com/-mY6qoFR2V44/TgqC6OCT7oI/AAAAAAAAEcs/S0HqhA5Eq0c/s1600/Gadget_the_pug_expressive_eyes.jpg'
		    ],
		    

			cards: [
			{
				number: 0, 
				active: false,
		
			}, 
			{
				number: 1, 
				active: false
		
			}, 
			{
				number: 2, 
				active: false
		
			}, 
			{
				number: 3, 
				active: false
	
			}, 
			{
				number: 4, 
				active: false
		
			}, 
				{
				number: 5, 
				active: false
		
			}, 
			{
				number: 6, 
				active: false
		
			}, 
			{
				number: 7, 
				active: false
	
			}, 
			{
				number: 8, 
				active: false
	
			}, 
			{
				number: 9, 
				active: false
	
			}, 
				{
				number: 10, 
				active: false
	
			}, 
			{
				number: 11, 
				active: false

			}, 
			{
				number: 12, 
				active: false

			}, 
			{
				number: 13, 
				active: false

			}, 
			{
				number: 14, 
				active: false
			}, 
			{
				number: 15, 
				active: false
			}, 
			{
				number: 16, 
				active: false
			}, 
			{
				number: 17, 
				active: false
			}, 
			{
				number: 18, 
				active: false
			}, 
			{
				number: 19, 
				active: false
			}, 
			],

		    cardPairImages : [],

		    cardPairNums : [] ,
		}
	},

		methods : {
			catchCard: function(card) {
			
			if(this.cardPairImages.length < 2) {
				card.active = true;

				console.log("number flips: " + this.flips);
				
				var image = this.images[card.number];
				var num = card.number;
				
				this.cardPairImages.push(image);

				this.cardPairNums.push(num);
				
				this.checkForMatch();

				this.checkForWin();
			
			} 
				
			},

			checkForWin : function() {
				var counter = 0;
				for(var i=0;i<this.cards.length;i++) {
					if(this.cards[i].active === true) {
						counter += 1;
					}
				}
				if(counter === 20) {
					alert('You win!');
				}
 			},

			checkForMatch : function() {
				
				var cards = this.cards;

				var card1Image = this.cardPairImages[0];
				var card2Image = this.cardPairImages[1];

				var card1Num = Number(this.cardPairNums[0]);
				var card2Num = Number(this.cardPairNums[1]);


				if(this.cardPairImages.length === 1) {

				}

				else if(this.cardPairImages.length === 2) {
					console.log('yes! 2 cards');
					if(card1Image === card2Image) {
						console.log('match');
						this.cardPairImages = [];
						this.cardPairNums = [];
						this.flips = 0;

					} else {


							setTimeout(function() { 
								
								cards.splice(card1Num,1, {
									'number' : card1Num,
									'active' : false
								});
								
								cards.splice(card2Num,1, {
									'number' : card2Num,
									'active' : false
								});

							}, 1000);
						
						console.log('flips reset: ' + this.flips);
						this.cardPairImages = [];
						this.cardPairNums = [];
						}

						
					}
				}
				
			} 

		}


</script>

<style>
	.board {
		margin-left: 10%;
		margin-bottom: 5%;
		width : 720px;
		background-color : transparent;
		padding-top: 2%;
		padding-bottom: 2%;
}
	
 .card.active {
	background-size: cover;
	box-shadow: none;
	}

	

</style>