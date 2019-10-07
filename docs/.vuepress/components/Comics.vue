<template>
  <div class="comic-container">
    <div class="nav-container">
      <div>
        Show comics for:
        <select @change="setCurrentDate">
          <option
            v-for="(item, index) in lastSevenDays"
            :key="index"
            :value="item.raw"
          >{{item.label}}</option>
        </select>
      </div>
      <div>
        Search for comic:
        <input type="text" />
      </div>
      <div>Customize:</div>
    </div>
    <div v-for="(item, index) in comicList" :key="index">
      <h2>{{item.title}}</h2>
      <img :src="getImage(item)" :alt="item.title" />
    </div>
  </div>
</template>

<script>
import comicList from "./data/comics-list.json";

export default {
  name: "Comics",
  data() {
    return {
      reqDate: {
        pretty: "",
        raw: new Date().getTime(),
        minRequestable: ""
      },
      comicList,
      userPrefs: []
    };
  },
  computed: {
    lastSevenDays() {
      var result = [];
      var days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ];
      var months = [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jun",
        "Jul",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec"
      ];
      for (var i = 0; i < 8; i++) {
        var d = new Date();
        d.setDate(d.getDate() - i);
        var label = `${days[d.getDay()]}, ${
          months[d.getMonth()]
        } ${d.getDate()}`;
        result.push({ label: label, raw: d.getTime() });
      }
      //console.log(result);
      return result;
    },
    filteredComicList() {}
  },
  methods: {
    getImage(item) {
      //https://docs.google.com/spreadsheets/d/1oUHP1GLSjPO2lr4tLVag0XkbfwbvtRfRvC1dtBYpRgk/edit?usp=sharing
      let newDate = new Date(this.reqDate.raw);
      let thisComic = item;
      let format = "gif";
      let requestedDate = {
        year: newDate.getFullYear(),
        month: ("0" + (newDate.getMonth() + 1)).slice(-2),
        day: ("0" + newDate.getDate()).slice(-2)
      };
      if (thisComic.sundayOnly === true) {
        newDate = new Date(newDate.setDate(newDate.getDate() - newDate.getDay()));
        requestedDate = {
          year: newDate.getFullYear(),
          month: ("0" + (newDate.getMonth() + 1)).slice(-2),
          day: ("0" + newDate.getDate()).slice(-2)
        };
        format = "jpg";
      }
      if (thisComic.partner === "king") {
        let encodedPayload = btoa(
          `/home/vhost/kfs/safr2.kingfeatures.com/cache/${thisComic.slug}/${requestedDate.year}/${requestedDate.month}/${thisComic.slugShort}.${requestedDate.year}${requestedDate.month}${requestedDate.day}_${thisComic.size}.gif`
        );
        return `https://safr.kingfeatures.com/content.php?file=${encodedPayload}`;
      }
      if (thisComic.partner === "am") {
        return `http://synd.imgsrv.uclick.com/comics/${thisComic.slug}/${
          requestedDate.year
        }/${thisComic.slugShort}${requestedDate.year.toString().substr(-2)}${requestedDate.month}${
          requestedDate.day
        }.${format}`;
      }
    },
    setCurrentDate(e) {
      this.reqDate.raw = Number(e.target.value);
    },
    readCookie() {},
    writeCookie() {}
  }
};
</script>