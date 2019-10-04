<template>
  <div id="app">
    <div class="wrapper">
      <restricted-access :restricted="true" :config="config">
        <div slot="custom-message">
          hello world
        </div>
        <div class="test-item">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Temporibus
          suscipit laudantium numquam iure quia non quos aspernatur eos
          recusandae quaerat nulla vel, repellendus necessitatibus doloremque
          animi adipisci exercitationem, facere minima. Lorem ipsum dolor sit,
          amet consectetur adipisicing elit. Dolores cupiditate, voluptatibus
          fugiat vitae, repudiandae eos temporibus neque eaque itaque accusamus
          quidem? Corrupti praesentium quae, eos ea amet delectus tenetur
          quisquam. Lorem ipsum dolor sit amet consectetur adipisicing elit.
          Consectetur rerum quos, ullam optio perferendis quae omnis nihil
          maxime mollitia corrupti atque tenetur unde veniam dolores. Autem vero
          eveniet error enim.
        </div>
      </restricted-access>
    </div>
  </div>
</template>

<script>
import RestrictedAccess from './RestrictedAccess.vue'
export default {
  name: 'app',
  components: {
    RestrictedAccess
  },
  data() {
    return {
      config: {
        strict: false,
        opacity: 0.5,
        blur: 3,
        showStatusText: true,
        statusText: 'Signup',
        statusTextColor: '#000',
        showLock: true,
        customStatusBox: true,
        customStatusPositionCenter: true
      }
    }
  }
}
</script>
<style lang="scss" scoped>
.wrapper {
  display: flex;
  justify-content: center;
  margin-top: 50px;
}
.test-item {
  width: 600px;
  padding: 10px;
}
</style>
