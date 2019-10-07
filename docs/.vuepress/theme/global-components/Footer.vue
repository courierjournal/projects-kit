<template>
  <footer>
    <ul class="footer-links">
      <li v-for="(link,index) in footerLinks" :key="index" class="footer-link">
        <a :href="link.url">{{link.label}}</a>
      </li>
    </ul>
    <div class="copyright">© {{copyrightYear}} {{copyrightProperty}}. All rights reserved.</div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      copyrightYear: 2019,
      copyrightProperty: "www.courier-journal.com",
      footerLinks: [
        { label: "Help", url: "https://help.courier-journal.com/" },
        {
          label: "Terms of Service",
          url: "https://static.courier-journal.com/terms/"
        },
        {
          label: "Privacy Notice",
          url: "https://static.courier-journal.com/privacy/"
        },
        {
          label: "Got a tip?",
          url:
            "https://www.courier-journal.com/story/news/2018/08/10/louisville-breaking-news-how-send-tips-courier-journal/864954002/"
        }
      ]
    };
  }
};
</script>

<style scoped>
footer {
  font-family: "Unify Sans";
  background-color: rgba(248, 248, 248);
  text-align: center;
  padding: 1.5em;
}

.footer-links {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  padding: 0px 0 10px;
  justify-content: center;
}

.footer-link {
  align-self: flex-start;
  margin-bottom: 10px;
  padding-right: 7px;
  height: 18px;
}

.footer-link a {
  text-decoration: none;
  color: rgba(0, 0, 0, 0.73);
  font-size: 16px;
  cursor: pointer;
}

.footer-link a:hover {
  color: var(--primary-blue);
}

.footer-link a:after {
  content: "\00b7";
  margin-left: 7px;
}

.footer-link:last-child a:after {
  content: "";
}

.copyright {
  font-size: 14px;
  color: rgba(0, 0, 0, 0.73);
}
</style>