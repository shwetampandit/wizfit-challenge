<template>
  <div class="image-component">
    <div class="image-container">
      <img src="../assets/banner.png" alt="" class="banner">
      <div class="header flex-rw">
        <div>
          What is WizFit Challenge?
        </div> 
        <div class="btn-container">
          <button class="watch-btn" @click="openYoutube">Watch Video</button>
        </div>
      </div>
      <div class="body-container flex-cl">
        <img src="../assets/player.png" alt="" class="player">
        <div class="form-container flex-cl">
          <ChallengeDiv />
          <SchoolList />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SchoolList from '../components/SchoolList.vue'
import ChallengeDiv from '../components/ChallengeDiv'
export default {
  name: 'HelloWorld',
  components: {
    SchoolList,
    ChallengeDiv
  },
  methods: {
    openYoutube () {
      window.open('https://youtu.be/KNRrXzf_IRY?feature=shared', '_blank')
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../styles.scss'; // Adjust the path as necessary

// @media (max-width: 1200px) {
//   font-size: 3rem; // Adjust for medium screens
// }

// @media (max-width: 768px) {
//   font-size: 2.5rem; // Adjust for smaller screens
// }
// @media (max-width: 480px) {
//   font-size: 2rem; // Adjust for mobile
// }

  .image-container {
    .banner {
      width: 100%;
  }
}

.watch-btn {
  background-color: $primary-color;
  color: #FFF;
  font-size: 1srem;
  font-weight: 600;
  border: $primary-color;
  border-radius: 5px;
  padding: 7px 20px;
  &:hover {
    cursor: pointer;
  }
}
.btn-container {
  display: flexs;
}
.body-container {
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
  .player {
    height: 13rem;
  }
}
.form-container {
  width: fit-content;
  padding: 10px 40px;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
}
</style>
