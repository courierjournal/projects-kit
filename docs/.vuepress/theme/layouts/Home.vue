<template>
  <div class="theme-container">
    <div class="home-hero">
      <div class="title-container">
        <div class="top-corner">
          <div class="horizontal-bar"></div>
          <div class="vertical-bar"></div>
        </div>
        <h1>{{$page.title}}</h1>
        <div class="bottom-corner">
          <div class="horizontal-bar"></div>
        </div>
      </div>
    </div>
    <Content class="theme-content" />
    <Footer />
  </div>
</template>

<style>
.theme-container {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}
.theme-content {
  flex: 1;
  padding: 1em 0;
}

.home-hero {
  padding: 2em;
  height: 300px;
  background-color: #ddd;
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url(/img/header.jpg);
  background-position: center;
  background-size: cover;
  margin-bottom:70px;
}

h1 {
  color: #fff;
  margin:0;
}

h1:after {
  content: none;
}

.title-container {
  /*background-color: rgba(0, 0, 0, 0.3);*/
  padding: 1.5em 2.5em;
  position: relative;
}

.top-corner {
  position: absolute;
  top: 0;
  left: 0;
}

.bottom-corner {
  position: absolute;
  bottom: 10px;
  right: 50px;
}

.horizontal-bar {
  height: 10px;
  width: 50px;
  left: 0;
  top: 0;
  background-color: var(--primary-blue);
  position: absolute;
}

.vertical-bar {
  height: 50px;
  width: 10px;
  background-color: var(--color-news, #009bff);
  position: absolute;
  left: 0px;
  top: 0px;
}

h2{
  font-size:1.5rem;
}

p{
  font-size: 1.1rem;
}
</style>