<template>
  <div id="reaction">
		<textarea name="comment" id="comment" rows="4" placeholder="Tweet your reply" v-model="text"></textarea>
		<button @click="commentTweet">Reply</button>
	</div>
</template>

<script>
export default {
  name: 'Reaction',
  props: [],
  data() {
    return {
			text: ''
    }
	},
	methods: {
		commentTweet () {	
			// create new comment object
			let newComment = {
				"id": this.$parent.tweetDict.comments.length,
				"authorName": "Visitor",
				"date": new Date(),
				"text": this.text,
				"likesNum": 0
			}
			
			// pass new comment object to tweet dict
			this.$parent.tweetDict.comments.push(newComment);
			this.text = "";
		}
	}
}
</script>

<style lang="scss" scoped>
#reaction {
	background-color: lightgrey;
	padding: 30px 40px;
	display: flex;
	flex-direction: column;
	border-top: 1px solid darken(lightgrey, 10%);;
	border-bottom: 1px solid darken(lightgrey, 10%);
}

textarea {
	padding: 10px;
	width: 75%;
	font-size: 16px;
	margin-bottom: 10px;
	align-self: flex-end;
}

button {
	padding: 5px 10px;
	font-size: 16px;
	align-self: flex-end;
}
</style>
