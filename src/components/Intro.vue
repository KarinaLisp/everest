<template>
  <v-card width="500px">
    <v-card-title
      class="
        display-1
        d-flex
        justify-center
      "
      v-text="title"
    />

    <v-card-text
      class="
        subtitle-1
        text-center
        font-weight-light
      "
      v-html="description"
    />

    <p
      class="
        player-stats-headline
        body-1
        text-center
        font-weight-light
      "
      v-text="'Основные показатели, по которым начисляем баллы:'"
    />
    <player-stats
      class="
        font-weight-bold
        justify-space-around
        pa-0
        mb-2
      "
    />

    <lazy-image :src="image" />

    <v-card-actions
      class="
        d-flex
        flex-column
        pa-3
      "
    >
      <v-btn
        block
        color="pink"
        @click="startNewGame"
        v-text="'Поехали'"
      />
    </v-card-actions>
  </v-card>
</template>

<script>
  import { mapState, mapActions } from 'vuex'
  import LazyImage from './LazyImage.vue'
  import PlayerStats from './PlayerStats.vue'

  export default {
    name: 'Intro',
    components: {
      LazyImage,
      PlayerStats,
    },
    computed: {
      ...mapState({
        stage: state => state.game.intro,
      }),
      title: vm => vm.stage.title,
      description: vm => vm.stage.description,
      image: vm => vm.stage.image,
    },
    methods: {
      ...mapActions([
        'startNewGame',
      ]),
    },
  }
</script>
