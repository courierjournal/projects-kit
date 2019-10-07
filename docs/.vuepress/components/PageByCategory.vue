<template>
  <div class="category-container">
    <a
      class="item-container"
      :href="item.path"
      v-for="(item, index) in filterCategory"
      :key="index"
      :style="{backgroundImage: `url(${item.frontmatter.thumbnail})`}"
    >
      <div class="item-text-container">
        <div class="item-title">{{item.title}}</div>
        <div class="item-description">{{item.frontmatter.description}}</div>
      </div>
    </a>
    <a v-show="moreVisible" class="item-container" @click="showMore">
      <div class="item-more-plus-symbol">+</div>
      <div class="item-more-text">More</div>
    </a>
  </div>
</template>

<script>
export default {
  name: "PageByCategory",
  props: ["front"],
  data() {
    return {
      itemsToShow: 3,
      moreVisible: false
    };
  },
  computed: {
    filterCategory() {
      let items = this.$site.pages.filter(
        n =>
          n.frontmatter.front.toLowerCase() === this.front.toLowerCase()
      );

      if (items.length > this.itemsToShow) {
        this.moreVisible = true;
      } else {
        this.moreVisible = false;
      }
      return items.slice(0, this.itemsToShow);
    }
  },
  methods: {
    showMore() {
      this.itemsToShow += this.itemsToShow;
    }
  }
};
</script>

<style scoped>
.category-container {
  display: flex;
  flex-wrap: wrap;
  margin-bottom:70px;
}
.item-container {
  display: inline-flex;
  flex-direction: column;
  width: 200px;
  height: 200px;
  background-color: #ccc;
  margin: 1em;
  padding: 1em;
  text-decoration: none;
  color: #333;
  align-items: center;
  justify-content: center;
  text-align: center;
  cursor: pointer;
  background-size: cover;
  background-position: center;
  transition: all 0.3s;
}

.item-container:hover {
  transform: scale(1.1, 1.1);
}

.item-text-container {
  color: #fff;
  padding: 1em;
  background-color: rgba(0, 0, 0, 0.7);
}

.item-title {
  font-weight: bold;
}
.item-description {
  font-size: 14px;
  overflow: hidden;
  text-overflow: ellipsis;
}

.item-more-plus-symbol {
  font-size: 5rem;
}
</style>