<template>
  <header>
    <div class="logo-container">
      <img
        id="site-logo"
        :src="propertyLogo"
      />
    </div>
    <div class="nav-container">
      <ul id="nav-items">
        <li v-for="(link,index) in headerLinks" :key="index">
          <a :href="link.url" class="nav-item">{{link.label}}</a>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      propertyLogo:
        "https://www.gannett-cdn.com/gannett-web/properties/courier-journal/logos-and-branding/logo-default.svg",
      headerLinks: [
        { label: "Home", url: "https://help.courier-journal.com/" },
        {
          label: "News",
          url: "https://static.courier-journal.com/terms/"
        },
        {
          label: "Sports",
          url: "https://static.courier-journal.com/privacy/"
        },
        {
          label: "Entertainment",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        },
        {
          label: "Opinion",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        },
        {
          label: "Lifestyle",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        },
        {
          label: "Photos",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        },
        {
          label: "Obituaries",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        },
        {
          label: "Weather",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        }
      ]
    };
  }
};
</script>

<style scoped>
header {
  font-family: "Unify Sans";
  background-color: #fff;
  height: 55px;
  overflow: hidden;
  width: 100%;
  border-bottom: 1px solid #ddd;
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0 100px;
}

.logo-container {
  height: 32px;
  margin-left: var(--spacer-twelve, 12px);
  opacity: 1;
  -webkit-transition: all var(--speed-fast, 0.25s);
  -moz-transition: all var(--speed-fast, 0.25s);
  transition: all var(--speed-fast, 0.25s);
  padding-right: 48px;
}

#site-logo {
  display: block;
  height: 100%;
}

#nav-items {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  align-items:center;
  height: 100%;
}

.nav-item {
  color: rgba(0, 0, 0, 0.73);
  font-weight: 600;
  font-size: 14px;
  text-decoration: none;
  padding: 0 12px;
  height:100%;
}

.nav-item:hover {
  font-weight: 900;
}
</style>