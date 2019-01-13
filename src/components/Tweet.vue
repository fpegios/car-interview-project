<template>
  <div id="tweet">
    <h1>{{ data.authorName }}</h1>
    <h2>@{{ data.authorUsername }}</h2>
    <p>{{ data.text }}</p>
    <hr>
    <div class="tweet-stats inline">
      <div class="tweet-stat comment">
        <img :src="require('./../assets/comment.png')" alt="Comment">
        {{ data.comments.length }}
      </div>
      <div class="tweet-stat like">
        <img @click="likeTweet(data.likesNum)" :src="require('./../assets/heart.png')" alt="Like">
        {{ data.likesNum }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tweet',
  props: ['data'],
  data() {
    return {
      liked: false
    }
  },
  methods: {
		likeTweet (likesNum) {	
      // if like btn is not liked, increase tweet likes by 1
			if (!this.liked) {
				this.$parent.tweetDict.likesNum = likesNum + 1;
				this.liked = true;
			} else {
        this.$parent.tweetDict.likesNum = likesNum - 1;
				this.liked = false;
      }
		}
  }
}
</script>

<style lang="scss" scoped>
#tweet {
  padding: 0 40px;
  margin-bottom: 20px;
}

h1, h2 {
  margin: 0;
}

h1 {
  font-size: 22px;
}

h2 {
  color: grey;
  font-size: 16px
}
</style>
