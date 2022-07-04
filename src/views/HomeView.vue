<template>
  <header>
    <section class="header-content">
      <svg class="logo animate-pop-in" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 196.5 196.5"><path d="M37.1 68.4l-26.9-13.4c7.7-15.5 19.5-28.8 34-38.4L60.8 41.7C50.7 48.4 42.5 57.6 37.1 68.4zM0 98.7c0 14.6 3.1 28.7 9.3 41.8l27.1-12.8C32.2 118.7 30 108.9 30 98.7c0-2 0.1-4.1 0.3-6L0.4 90.1C0.1 92.9 0 95.8 0 98.7zM190.5 64.9c-6-16.3-16.2-30.8-29.6-41.9l-19.1 23.1c9.3 7.7 16.5 17.8 20.6 29.1L190.5 64.9zM166.5 98.7c0 12.1-3.2 24-9.3 34.4l25.9 15.1c8.8-15 13.4-32.1 13.4-49.5H166.5zM98.2 30.5c7.3 0 14.5 1.2 21.4 3.4l9.4-28.5c-9.9-3.3-20.3-4.9-30.8-4.9 -6.9 0-13.7 0.7-20.4 2.1l6.2 29.4C88.7 31 93.5 30.5 98.2 30.5zM82.6 165.2c-11.7-2.7-22.6-8.6-31.3-16.9l-20.6 21.8c12.7 12 28.3 20.4 45.2 24.4L82.6 165.2zM140.6 152.2c-9.5 7.5-20.8 12.4-32.7 14.1l4.2 29.7c17.2-2.4 33.5-9.4 47.2-20.3L140.6 152.2z"/></svg>
      <h1 class="header-title animate-pop-in">
       Contact Manager
      </h1>
      <h3 class="header-subtitle animate-pop-in">
        Access Your Contacts By One Click!
      </h3>
      <p class="header-button animate-pop-in">
        <a href="Contacts" class="button">
          Get started
        </a>
      </p>
    </section>
  </header>
  <footer>Created by Nour Al Hassan</footer>
</template>

<script>
export default {

  name: 'HomeView',
  data () {
    return {
      msg: 'Welcome to Your Contact App'
    }
  }
}
</script>

<style scoped>
.js-loading *, .js-loading *:before, .js-loading *:after {
  animation-play-state: paused !important;
}
body, html {
  font-family: 'Times New Roman' , sans-serif;
  background-color: #F9FCFF;
  height: 100%;
  letter-spacing: 3px;
  font-weight: 500;
  text-align: center;
  overflow-x: hidden;
}
body h1, body h2, body h3, html h1, html h2, html h3 {
  color: black;
  font-weight: 700;
}
body h3, html h3 {
  font-weight: 100;
}
.header-content {
  padding-top: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  z-index: 999;
}
header {
  background: url('https://img.freepik.com/free-photo/hand-using-gadgets-device-top-view-blank-screen-with-copyspace-minimalistic-style-technologies-modern-marketing-negative-space-ad-flyer-yellow-color-wall-stylish-trendy_155003-37987.jpg?t=st=1656893822~exp=1656894422~hmac=548cebb44bbc863a1e193932c71978f87077b7549db882924a3c9c75e2eb48de&w=1380');
  background-size: cover;
  height: 100%;
  max-height: 60rem;
}
header:after {
  animation: rotate-up 0.5s 0.5s cubic-bezier(0, 0.5, 0, 1) forwards;
  background: lightyellow;
  content: "";
  height: 15rem;
  left: -5%;
  position: absolute;
  right: -5%;
  top: 90%;
  transform-origin: 0 0;
  z-index: 0;
  animation-delay: 2s;
}
.animate-pop-in {
  animation: pop-in 0.6s cubic-bezier(0, 0.9, 0.3, 1.2) forwards;
  opacity: 0;
}
.logo {
  fill: black;
  width: 160px;
  animation-delay: 0.6s;
  z-index: 99;
  padding-bottom: 30px;
}
.header-title {
  animation-delay: 0.8s;
  z-index: 99;
}
.header-subtitle {
  animation-delay: 1s;
  z-index: 99;
}
.header-button {
  box-shadow: 0 7px 12px rgba(0, 0, 0, 0.28);
  animation-delay: 1.1s;
  z-index: 99;
  height: 50px;
  line-height: 50px;
  width: 200px;
  background: #0A1170;
  border-radius: 3px;
  color: #FFFFFF;
}
.header-button:hover {
  background-color: #c81811;
}
.header-button a {
  text-decoration: none;
  color: #f2f0f1 !important;
  font-weight: bold;
  text-transform: uppercase;
}
footer {
  color: #4c4c4c;
  position: absolute;
  width: 100%;
}
footer a {
  color: #4c4c4c;
  text-decoration: none;
}
@keyframes pop-in {
  0% {
    opacity: 0;
    transform: translateY(-4rem) scale(0.8);
  }
  100% {
    opacity: 0.9;
    transform: none;
  }
}
@keyframes rotate-up {
  100% {
    transform: rotateZ(-4deg);
  }
}

</style>
