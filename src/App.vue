<template>
  <div id="app">
    <Tweet :data="tweetDict"/>
    <Reaction :data="tweetDict"/>
    <Comments :data="tweetDict.comments"/>
  </div>
</template>

<script>
import Tweet from './components/Tweet.vue'
import Reaction from './components/Reaction.vue'
import Comments from './components/Comments.vue'

let dict = [];
dict.push({
  "authorName": "John Poter",
  "authorUsername": "john.poter",
  "text" : "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages.",
  "likesNum": 11,
  "comments": [
    {
      "id": 0,
      "authorName": "Askolony",
      "date": "2019-10-25",
      "text": "Lorem Ipsum is simply dummy text of the printing.",
      "likesNum": 18
    },
    {
      "id": 1,
      "authorName": "Wayne Allan",
      "date": "2019-10-25",
      "text": "this one is too real!",
      "likesNum": 5
    },
    {
      "id": 2,
      "authorName": "XiaoPeng",
      "date": "2019-10-27",
      "text": "When you work on trashy legacy codebase, you need ZenUML.com.",
      "likesNum": 2
    }
  ]
});

export default {
  name: 'app',
  components: {
    Tweet,
    Reaction,
    Comments
  },
  data () {
    return {
      tweetDict: dict[0]
    }
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }

  #app {
    width: 800px;
    box-shadow: 0 2px 9px rgba(0,0,0,.25);
    border-radius: 4px;
    margin: 0 auto;
    padding: 20px 0;
  }

  .tweet-stats {
	display: inline-flex;
}

.tweet-stat {
  display: flex;
  align-items: center;
	margin-bottom: 10px;
	
	&:not(:last-child) {
		margin-right: 30px;
	}

	&.like {
		img {
      cursor: pointer;

      &:hover {
        transform: scale(1.2);
      }
    }
	}
		
	img {
		width: 22px;
		margin-right: 10px;
		transition: all .3s ease-out;
	}

	span {
		font-size: 20px;
	}
}
</style>
