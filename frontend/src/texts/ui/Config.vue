<template>
  <div class="visual-dl-page-config-com">
    <v-text-field
      label="Group name RegExp"
      hint="input a tag group name"
      v-model="config.groupNameReg"
      dark
    />

    <label class="visual-dl-page-checkbox-group-label">Runs</label>

    <v-checkbox
      v-for="item in runsItems"
      :key="item.name"
      :label="item.name"
      :value="item.value"
      v-model="config.runs"
      dark
      class="visual-dl-page-runs-checkbox"
    />

    <v-btn
      :color="config.running ? 'primary' : 'error'"
      v-model="config.running"
      @click="toggleAllRuns"
      class="visual-dl-page-run-toggle"
      dark
      block
    >
      {{ config.running ? 'Running' : 'Stopped' }}
    </v-btn>
  </div>
</template>
<script>

export default {
  props: {
    runsItems: {
      type: Array,
      required: true,
    },
    config: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
    };
  },
  methods: {
    toggleAllRuns() {
      this.config.running = !this.config.running;
    },
  },
};

</script>
<style lang="stylus">
+prefix-classes('visual-dl-page-')
    .config-com
        padding 20px
        .slider-block
            display flex
            align-items center
        .smoothing-slider
            display inline
        .slider-span
            width 40px
        .run-toggle
            margin-top 20px
        .config-selector
            margin-top 12px
            margin-bottom 20px
        .checkbox-group-label
            display flex
            margin-top 20px
            margin-bottom 10px

</style>


