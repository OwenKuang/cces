<template>

  <div class="background">
    <div class="image-container">
      <!-- Image -->
      <img src="./assets/logo.png" class="logo-image">
      <img src="./assets/text.png" class="text-image">
    </div>
    <nav>
      <!-- Navigation bar -->
      <ul>
        <li v-for="(link, index) in links" :key="index">
          <a :href="link.url" :class="{ active: link.active }" @click="setActiveLink(index)">{{ getLinkLabel(link) }}</a>
        </li>
      </ul>
    </nav>
    <div class = "main">
      <h1>About Us:</h1>
      <p>
        We are a society composed of Chinese-Canadian professionals that are employed or interested in energy solutions of the present and future.
      </p>
    </div>
    <div>
      <!-- Become a member footer -->
      <button class="become-member" @click="showMembershipForm">{{ getBecomeMemberText() }}</button>
      <!-- Language toggle button -->
      <button class="language-toggle" @click="toggleLanguage">{{ getLanguageButtonText() }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      links: [
        { url: '/home', label: { english: 'Home', chinese: '主页' }, active: false },
        { url: '/about', label: { english: 'About', chinese: '关于' }, active: false },
        { url: '/services', label: { english: 'Services', chinese: '服务' }, active: false },
        { url: '/contact', label: { english: 'Contact', chinese: '联系我们' }, active: false },
      ],
      language: 'english',
    };
  },
  methods: {
    setActiveLink(index) {
      this.links.forEach((link, i) => {
        link.active = i === index;
      });
    },
    showMembershipForm() {
      // Code to show the membership form
    },
    toggleLanguage() {
      this.language = this.language === 'english' ? 'chinese' : 'english';
    },
    getLinkLabel(link) {
      return link.label[this.language];
    },
    getBecomeMemberText() {
      return this.language === 'english' ? 'Become a Member' : '成为会员';
    },
    getLanguageButtonText() {
      return this.language === 'english' ? '中文' : 'English';
    },
  },
};
</script>

<style>
.main {
  text-align: center;
  margin-top: 20px;
  font-weight: bolder;
  font-size: 20px;
}
body {
  margin: 0;
  padding: 0;
  background-image: url("./assets/background.jpg");
  background-size: cover;
  background-position: center;
}

nav {
  background-color: black; 
  padding: 5px;
  font-family: Arial, sans-serif;
} 

.background {
  position: relative;
  z-index: 0;
}




ul {
  list-style-type: none;
  margin: 1%;
  padding: 0;
  display: flex;
  justify-content: center;
}

li {
  display: inline;
  margin: 0 10%;
}

a {
  text-decoration: none;
  color: #fff;
  padding: 15px 30px;
  font-size: 18px;
  transition: background-color 0.3s ease, border-radius 0.3s ease;
  border-radius: 50px;
  white-space: nowrap;
}

a:hover {
  background-color: #555;
}

a.active {
  background-color: #f1f1f1;
  color: #333;
  border-radius: 50px;
}

.become-member {
  background-color: #555;
  color: #fff;
  padding: 15px 30px;
  border: none;
  border-radius: 4px;
  font-size: 20px;
  cursor: pointer;
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 999;
  transition: background-color 0.3s ease;
}

.become-member:hover {
  background-color: #333;
}

.language-toggle {
  background-color: #555;
  color: #fff;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  position: fixed;
  bottom: 20px;
  left: 20px;
  z-index: 999;
  transition: background-color 0.3s ease;
}

.language-toggle:hover {
  background-color: #333;
}
.logo-image {
  padding-left: 50px;
  height: 1%;
}
.text-image {
  padding-top: 20px;
  padding-left: 40px;
  width: 40%;
  padding-bottom: 20px;
}
</style>
