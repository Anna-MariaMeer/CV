<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text class="text-xs-center">
      <h4>My CV ends here, but not my journey!</h4>
      <content-section>
        <v-timeline>
          <v-timeline-item
            v-for="n in futurePage * 2"
            :key="n"
            icon=""
            large
          >
            <template
              v-slot:icon
            >
              <div class="fill-width">
                <vue-content-loading
                  :width="80"
                  :height="95"
                >
                  <circle
                    cx="40"
                    cy="52"
                    r="42"
                  />
                </vue-content-loading>
              </div>
            </template>

            <vcl-code />
          </v-timeline-item>
        </v-timeline>
      </content-section>
      <div
        v-if="toggleMessage"
        class="ma-4"
      >
        <span
          class="pre"
        >{{ message.text }}</span>
        <div
          v-if="!loading"
          v-scroll="scrolled"
        />
      </div>
      <v-progress-circular
        v-if="loading"
        indeterminate
        color="primary"
      />
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
import VueContentLoading, { VclCode } from 'vue-content-loading'

export default {
  name      : 'EndlessTimeline',
  components: {
    ContentSection, VueContentLoading, VclCode,
  },
  data: () => ({
    futurePage   : 0,
    message      : '',
    toggleMessage: true,
    loading      : false,
    messages     : [],
  }),
}
</script>

<style scoped>
.fill-width {
  width: 100%;
}
.pre {
  white-space: pre;
}
</style>
