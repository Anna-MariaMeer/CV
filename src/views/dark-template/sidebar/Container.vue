<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>Anna-Maria <span class="light-blue--text text--lighten-3">Meer</span></h1>
        <span />
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{ item }">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.other_activities" />
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{ items }">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template v-for="(item, i) in items">
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'anna@meer-mg.de',
            },
            {
              name: 'Geburtsdatum',
              icon: 'mdi-cake-variant',
              text: 'May 02, 1993',
            },
            {
              name: 'Habitation',
              icon: 'mdi-map-marker',
              text: 'Mönchengladbach, Deutschland',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [
            {
              icon: 'mdi-violin',
              text: 'Viola, piano & orchestra',
            },
            {
              icon: 'mdi-pencil',
              text: 'Drawing',
            },
            {
              icon: 'mdi-biohazard',
              text: 'Challenges',
            },
            {
              icon: 'mdi-auto-fix',
              text: 'Hackathons',
            },
            {
              icon: 'mdi-walk',
              text: 'Running',
            },
            {
              icon: 'mdi-human-female-dance',
              text: 'Dancing',
            },
            {
              icon: 'mdi-swim',
              text: 'Swimming',
            },
            {
              icon: 'mdi-earth',
              text: 'Travel',
            },
          ],
        },
        other_activities: {
          title: 'OTHERS ACTIVITIES',
          items: [
            { text: ' - Role-model for young women at an expo of the "SMILE" project of the German Research Center for Artificial Intelligence' },
            { text: ' - Violist in multiple youth orchestras (Tonhalle Düsseldorf, state youth ensemble for new music,...)' },
            { text: ' - Volunteering as a swimming teacher for the German Life Saving Association' },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'Deutsch',
              value: 100,
            },
            {
              text : 'English',
              value: 90,
            },
            {
              text : 'Korean',
              value: 30,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar {
  background: #2e2e2e;
}
</style>
