<template>
  <div class="home">
    <Carousel></Carousel>
    <Story
      v-for="story in stories" 
      :key="story.id"
      :story="story"
    ></Story>
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
import Story from "@/components/Story.vue";

export default {
  name: "HomeView",
  components: {
    Carousel,
    Story,
  },
  data() {
    return {
      stories: stories
    }
  }
};

const stories = [
  {
    id: 1,
    title: "理念",
    info: "小店想強調的是貝果本身的風味，小麥的香氣與口感，內餡為點綴。<br>我們的理念一直都是製作較天然、低負擔的麵包，因此採用製粉技術較好的法國、日本進口粉，麵團無油、減糖、減鹽，內餡也追求較天然、無添加的原料，相信小麥粉們也是認同我們的理念，而購買我們的貝果。",
    img: "/story_1.jpg"
  },
  {
    id: 2,
    title: "故事",
    info: `在烘焙業打滾8、9年，從學徒做起，慢慢地愛上麵包。<br>
      對我來說，麵包做得用不用心，看得出來，也吃得出來。<br><br>
      市面上高油、高糖的麵包為大宗，但近來發現越來越多民眾喜愛天然、低負擔、營養食材，喜歡小麥原味、享受咀嚼後的清香，且樂於與他人分享。
      這也激勵了我，欲實現一直以來的心願...<br><br><i><strong>「做出能給人帶來幸福、溫暖、滿足、趣味的天然優質麵包」</strong></i><br><br>
      我們堅定地相信著，健康、美味的麵包能帶來無價的微笑。`,
    img: "/story_2.jpg"
  }
]

</script>

<style lang="scss" scoped>
$bgc: rgba(255, 238, 223, 1);

.home {
  background-color: $bgc;
  border: transparent solid;
}

</style>