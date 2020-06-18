<template>
  <div>
    <div class="header-container">
      <div class="header-left">
        <p>ロゴ</p>
      </div>
      <div class="header-right">
        <div class="header-right-contents">
          <p>about</p>
        </div>
        <div class="header-right-contents">
          <p>Works</p>
        </div>
        <div class="header-right-contents">
          <p>Access</p>
        </div>
        <div class="header-right-contents">
          <p>Contact</p>
        </div>
      </div>
    </div>
    <div class="header-right-h">
      <input id="toggle" type="checkbox" />
      <label class="hamburger" for="toggle">
        <div class="top"></div>
        <div class="meat"></div>
        <div class="bottom"></div>
      </label>
      <div class="nav">
        <div class="nav-wrapper">
          <nav>
            <a href="#">Home</a>
            <a href="#">About</a>
            <a href="#">Works</a>
            <a href="#">Access</a>
            <a href="#">Contact</a>
          </nav>
        </div>
      </div>
    </div>
  </div>
</template>
    
<style scoped>
.header-container {
  width: 100%;
  height: 75px;
  background-color: #404040;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
@media screen and (max-width: 500px) {
  .header-container {
    display: none;
  }
}
.header-container p {
  color: #e7e7e7;
}
.header-left {
  margin-left: 20px;
}
.header-right {
  display: flex;
}
.header-right-contents {
  margin-right: 30px;
}

@media screen and (min-width: 501px) {
  .header-right-h {
    display: none;
  }
}

.hamburger {
  position: absolute;
  width: 50px;
  height: 45px;
  top: 10px;
  right: 20px;
  z-index: 5;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.hamburger div {
  position: relative;
  width: 40px;
  height: 5px;
  border-radius: 3px;
  background-color: #17171b;
  margin-top: 7px;
  -webkit-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
}

#toggle {
  display: none;
}

#toggle:checked + .hamburger .top {
  -webkit-transform: rotate(-45deg);
  transform: rotate(-45deg);
  margin-top: 22.5px;
}
#toggle:checked + .hamburger .meat {
  -webkit-transform: rotate(45deg);
  transform: rotate(45deg);
  margin-top: -5px;
}
#toggle:checked + .hamburger .bottom {
  -webkit-transform: scale(0);
  transform: scale(0);
}
#toggle:checked + .hamburger + .nav {
  top: 0;
}

.nav {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #f7f7f7;
  top: -100%;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
  -webkit-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
}
.nav .nav-wrapper {
  position: relative;
  overflow-y: auto;
  height: 100%;
}

nav {
  height: 100vh;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}
nav a {
  margin-top: 1.25em;
  color: #17171b;
  opacity: 0;
  text-decoration: none;
  font-size: 1.5em;
  letter-spacing: 3px;
  -webkit-transition: all 0.1s ease;
  transition: all 0.1s ease;
}
nav a:first-child {
  margin-top: 0;
}

#toggle:checked + .hamburger + .nav .nav-wrapper nav a {
  opacity: 0.9;
  -webkit-transform: scale(1);
  transform: scale(1);
}
#toggle:checked + .hamburger + .nav .nav-wrapper nav a:hover {
  opacity: 1;
  color: white;
  -webkit-transform: scale(1.2);
  transform: scale(1.2);
}
</style>