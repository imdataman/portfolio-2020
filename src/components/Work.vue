<template>
  <div class="work">
    <div class="work-wrapper">
      <div
        class="type-container"
        v-for="works in allWorks"
        :key="works.category[lang]"
      >
        <p class="category">{{ works.category[lang] }}</p>
        <hr />
        <div class="work-container" v-for="w in works.entry" :key="w.shared.id">
          <div class="work-title">
            <h2>{{ w[lang].title }}</h2>
            <p class="subtitle">{{ w[lang].subtitle }}</p>
          </div>
          <div class="work-image">
            <a :href="w.shared.url" target="_blank">
              <img
                :src="`image/${w.shared.id}.png`"
                :alt="`${w[lang].title}`"
              />
            </a>
          </div>
          <div class="work-description">
            <p>{{ w[lang].description }}</p>
          </div>
          <div class="work-tools">
            <ul>
              <li
                v-for="(t, i) in w[lang].tools"
                :key="`${w.shared.id}-${i}-tool`"
              >
                {{ t }}
              </li>
            </ul>
          </div>
          <div class="work-social" v-if="w.shared.github">
            <a :href="w.shared.github" target="_blank">
              <img
                src="@/assets/image/github.png"
                :alt="`${w[lang].title} GitHub`"
              />
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import works from "@/assets/works.json";

export default {
  name: "Work",
  props: {
    lang: String
  },
  data() {
    return {
      allWorks: works
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
hr {
  margin-top: 0;
  margin-bottom: 2rem;
  border-top: #ccc;
}

.category {
  opacity: $subtitle-opacity;
  margin-bottom: 0.25rem;
  font-weight: 500;
}

.type-container {
  margin-bottom: 80px;
}

.work-container {
  margin-bottom: 40px;
  display: grid;
  align-items: center;
  grid-template-columns: 7fr 0.5fr 6fr;
  grid-template-rows: 1fr 1fr 1.5fr 0.5fr;
  grid-template-areas:
    "img . title"
    "img . description"
    "img . tool"
    "img . social";
}

.work-image {
  grid-area: img;
  img {
    width: 100%;
    filter: gray; /* IE6-9 */
    -webkit-filter: grayscale(0.6); /* Google Chrome, Safari 6+ & Opera 15+ */
    filter: grayscale(0.6);
    &:hover {
      -webkit-filter: grayscale(0);
      filter: none;
    }
  }
}

.work-title {
  grid-area: title;
  h2 {
    margin-top: 0;
    margin-bottom: 0;
    @extend %text-color-shadow;
  }
  .subtitle {
    opacity: $subtitle-opacity;
    margin-top: 0.5rem;
    font-weight: 500;
  }
}

.work-description {
  grid-area: description;
  p {
    margin: 0;
  }
}

.work-tools {
  grid-area: tool;
  ul {
    margin-top: 0;
  }
}

.work-social {
  grid-area: social;
  img {
    height: 1.25rem;
    &:hover {
      opacity: $subtitle-opacity;
    }
  }
}

@media only screen and (max-width: 480px) {
  .work-container {
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
  .work-image {
    margin-bottom: 10px;
  }
  .work-description {
    grid-area: description;
    p {
      margin: 10px;
    }
  }
}
</style>
