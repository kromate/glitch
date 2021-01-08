<template>
  <div class="bg">
    <h1 v-if="data.name">{{ data.name }}</h1>
    <h1 v-else>Loading...</h1>
    <img
      class="Bimg"
      src="https://cdn.glitch.com/fbe1547c-e1e4-460d-b1e3-b5c47836d798%2Fmodel.png?v=1610110433399"
      alt=""
      srcset=""
    />
    <div class="Bmenu">
      <p>Home</p>
      <p>About</p>
      <img
        class="Cimg"
        src="https://cdn.glitch.com/fbe1547c-e1e4-460d-b1e3-b5c47836d798%2Fcircle.png?v=1610112381735"
        alt=""
        srcset=""
      />
      <p>Gallery</p>
      <p>Contact</p>
    </div>

    <div class="social" v-if="data.social_media">
      <a :href="social.link" v-for="(social, index) in socials" :key="index" target="_blank">
        <img class="icon" :src="social.img" alt="" srcset="" />
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: "{}",
    };
  },
  computed: {
    socials() {
      return [
        {
          img:
            "https://cdn.glitch.com/fbe1547c-e1e4-460d-b1e3-b5c47836d798%2Finsta.svg?v=1610116161893",
          link: `https://instagram.com/${this.data.social_media.instagram}`,
        },
        {
          img:
            "https://cdn.glitch.com/fbe1547c-e1e4-460d-b1e3-b5c47836d798%2Ftwitter.svg?v=1610116161893",
          link: `https://twitter.com/${this.data.social_media.twitter}`,
        },
        {
          img:
            "https://cdn.glitch.com/fbe1547c-e1e4-460d-b1e3-b5c47836d798%2Fsnap.svg?v=1610116161893",
          link: `https://snapchat.com/${this.data.social_media.snapchat}`,
        },
        {
          img:
            "https://cdn.glitch.com/fbe1547c-e1e4-460d-b1e3-b5c47836d798%2Fmail.svg?v=1610116162012",
          link: `${this.data.social_media.instagram}`,
        },
      ];
    },
  },
  methods: {
    fetchData() {
      fetch("https://hirng-x2021.glitch.me/api")
        .then((response) => response.json())
        .then((data) => {
          this.data = data;
          console.log(data);
        });
    },
  },
  created() {
    this.fetchData();
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");
* {
  padding: 0;
  margin: 0;
  font-family: "Roboto", sans-serif;
  font-weight: 300;
  color: white;
}

h1 {
  margin-bottom: 2rem;
  margin-left: 2.7rem;
  font-size: 2rem;
}

.icon {
  width: 75%;
  margin: 10px;
}
.social {
  position: fixed;
  top: 35%;
  right: 3%;
  width: 30px;
}
.Bimg {
  width: 45%;
  height: auto;
      box-shadow: 0px 0px 7px 0px #2d2929;
}
.Cimg {
  width: 10%;
  height: auto;
}
.Bmenu {
  margin-top: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 50%;
  margin-left: 1rem;
}

.bg {
  background-image: linear-gradient(to right, #bd0f4d 50%, #cb2964 50%);
  min-width: 100vw;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;

  flex-direction: column;
}
</style>
