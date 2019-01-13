<template>
  <div id="comments">
		<div class="comment" v-for="comment in data" :key="comment.id">
			<div class="inline">
				<h3>{{ comment.authorName }} <span>&bull; {{ formatDate(comment.date) }}</span></h3>
			</div>
			<p>{{ comment.text }}</p>
			<div class="tweet-stat like">
				<img @click="likeTweet(comment.id, comment.likesNum)" :src="require('./../assets/heart.png')" alt="Like">
				{{ comment.likesNum }}
			</div>
		</div>
  </div>
</template>

<script>
export default {
  name: 'Comments',
  props: ['data'],
  data() {
    return {
			name: "name",
			likes: 10,
			text: "Lorem Ipsum is simply dummy text of the printing",
			commentLikes: 20,
			liked: []
    }
	},
	methods: {
    formatDate: function (date) {
			const now = new Date(date);
			const monthNames = ["January", "February", "March", "April", "May", "June",
				"July", "August", "September", "October", "November", "December"
			];
      
      return monthNames[now.getMonth()].substring(0, 3) + " " + now.getDate();
    },
		likeTweet (commentId, commentLikes) {	
			// if like btn is not liked, increase tweet likes by 1
			if (!this.liked[commentId]) {
				this.$parent.tweetDict.comments[commentId].likesNum = commentLikes + 1;
				this.liked[commentId] = true;
			} else {
				this.$parent.tweetDict.comments[commentId].likesNum = commentLikes - 1;
				this.liked[commentId] = false;
			}
		}
	}
}
</script>

<style lang="scss" scoped>
.comment {
	padding: 15px 40px;
	&:not(:last-child) {
		border-bottom: 1px solid lightgrey;
	}
}

.inline {
	display: inline-flex;
}

h3 {
	margin: 0;
	span {
		color: grey;
	}
}
</style>
