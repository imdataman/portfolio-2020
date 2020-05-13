<template>
  <div class="about">
    <h2 class="title" v-if="lang === 'zhTW'">
      地圖 &#128506; 前端 &#128187; 視覺化 &#128200;
    </h2>
    <h2 class="title" v-else>
      Maps &#128506; Coding &#128187; Dataviz &#128200;
    </h2>
    <h3 class="subtitle" v-if="lang === 'zhTW'">資料視覺化設計師 林佳賢</h3>
    <h3 class="subtitle" v-else>Andy Lin Chia Hsien</h3>
    <div class="main-grid">
      <div class="left-column">
        <p v-if="lang === 'zhTW'">
          我是一個興趣使然的coder，喜歡用簡潔易懂的方式，呈現艱澀難懂的資料，或是寫程式畫地圖，挖掘空間資訊中的故事。常用的工具有Vue、D3、Mapbox
          GL JS、R，歡迎這些工具的愛用者多多交流！
        </p>
        <p v-else>
          I'm a coder driven by the passion to discover meanings in datasets and
          communicate them in the most accessible way. Maps are my favorite type
          of data visualization, and I can spend a whole day clicking around an
          interactive map.
        </p>
        <p v-if="lang === 'zhTW'">
          除了工作之外，我還有經營一個臉書專頁<a
            href="https://www.facebook.com/imDataMan/"
            target="_blank"
            >Data Man 的資料視覺化筆記</a
          >，分享自己的資料視覺化作品、心得和相關教學，歡迎來看看！
        </p>
        <p v-else>
          If you need someone who is familiar with Vue, ES6, D3, Mapbox GL JS or
          R, feel free to contact me via any of the links below.
        </p>
        <div class="social-container">
          <a href="https://github.com/imdataman" target="_blank"
            ><img src="@/assets/image/github.png"
          /></a>
          <a href="https://twitter.com/imandylin2" target="_blank"
            ><img src="@/assets/image/twitter.png"
          /></a>
          <a href="https://www.facebook.com/imDataMan/" target="_blank"
            ><img src="@/assets/image/facebook.png"
          /></a>
          <a href="mailto: imandylin2@gmail.com" target="_blank"
            ><img src="@/assets/image/email.png"
          /></a>
        </div>
      </div>
      <div class="right-column">
        <div class="experience">
          <ul v-if="lang === 'zhTW'">
            <li><span>'19.10 - '20.02</span>海峽時報 資料視覺化設計師</li>
            <li><span>'17.02 - '19.09</span>天下雜誌 資料記者</li>
            <li><span>'16.08 - '17.01</span>端傳媒 資料記者</li>
            <li><span>'15.06 - '16.07</span>關鍵評論網 資料新聞編輯</li>
            <li><span>'13.08 - '15.05</span>經濟日報 國際財經編譯</li>
          </ul>
          <ul v-else>
            <li>
              <span>'19.10 - '20.02</span>The Straits Times, Dataviz Designer
            </li>
            <li>
              <span>'17.02 - '19.09</span>CommonWealth Magazine, Data Journalist
            </li>
            <li>
              <span>'16.08 - '17.01</span>Initium Media, Data Product Manager
            </li>
            <li><span>'15.06 - '16.07</span>The News Lens, Data Editor</li>
            <li>
              <span>'13.08 - '15.05</span>Economic Daily News, Economic Editor
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import works from "@/assets/works.json";

export default {
  name: "About",
  props: {
    lang: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.title {
  margin-top: 0.5rem;
  margin-bottom: 0;
  text-align: center;
  @extend %text-color-shadow;
}
.subtitle {
  text-align: center;
  margin-top: 0.5rem;
  margin-bottom: 1rem;
  opacity: $subtitle-opacity;
}
li {
  margin: 20px 0;
}

.main-grid {
  display: grid;
  grid-template-columns: 3fr 0.5fr 3fr;
  grid-template-areas: "left . right";
}

.left-column {
  grid-area: left;
  margin-bottom: 40px;
  a {
    color: black;
    &:hover {
      font-weight: 600;
      @extend %text-color-shadow;
    }
  }
}
.right-column {
  grid-area: right;
}

.social-container {
  img {
    height: 1.25rem;
    padding-right: 0.5rem;
    vertical-align: sub;
    &:hover {
      opacity: $subtitle-opacity;
    }
  }
}

span {
  float: right;
}

@media only screen and (max-width: 480px) {
  .main-grid {
    display: flex;
    flex-direction: column;
  }
  .left-column {
    margin-bottom: 20px;
  }
  span {
    display: block;
    float: none;
    margin-top: 1rem;
  }
}
</style>
