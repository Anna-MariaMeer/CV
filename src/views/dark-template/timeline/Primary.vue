<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        title="My Experiences"
      >
        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    items: [
      {
        year : '2019',
        title: 'Teaching Assistant University of Bremen',
        html : `
          <p>
          Teaching assistant in the seminar "Exploring Virtual Reality technologies for documentary films", VR workshop 
          at international bremer symposium on films 
          </p>
        `,
        icon: 'mdi-filmstrip',
      },
      {
        year : '2019',
        title: 'Internship Bioinformatics Lab Hanyang University',
        html : `
          <p>
           Development of a frontend prototype and algorithms for DNA alignment
          </p>
        `,
        icon: 'mdi-gesture-tap',
      },
      {
        year : '2019',
        title: 'Project work at University of Bremen',
        html : `<p>Implementation of a Collision Detection Plugin for grasping in Unreal Engine (C++). Collecting data for the later usage on robots <a href=https://cgvr.cs.uni-bremen.de/teaching/studentprojects/virtualcooking/>(Click here for details)</a></p>`,
        icon : 'mdi-hand-coin',
      },
      {
        year : '2020',
        title: 'Bachelor Thesis at German Research Center for Artificial Intelligence',
        html : `<p>Implementation of a testframework for local and global path planner in C++/Python, ROS </p>`,
        icon : 'mdi-map-marker-distance',
      },
      {
        year : '2021',
        title: 'World Champion Title RoboCup Logistic League with Carologistics',
        html : `<p>My part was the application of a neural network for identifying working stations and the improvement of the robot localization with ROS <a href=https://www.informatik.rwth-aachen.de/cms/informatik/Fachgruppe/Aktuell/Meldungen/~pkyef/Aachener-Carologistics-gewinnt-ersten-hy/?lidx=1>(Click here for details)</a></p>`,
        icon : 'mdi-robot-happy',
      },
      {
        year : '2020 - 2022',
        title: 'Research Assistant at Cybernetics Lab RWTH Aachen (19h per week)',
        html : `<p>Research assistance and master thesis student in the project Demosens, which deals with the automated dismantling and recycling of electrical car batteries using robotic arms. Implementation of a pipeline for battery component identification (Instance Segmentation) and pose estimation (Pointcloud Registration) <a href="https://www.pem.rwth-aachen.de/cms/PEM/Forschung/Projekte/~pkazx/DemoSens/?lidx=1">(Click Link for Details)</a></p>

        <p>Development of the software for the mobile robotic plattform Oscar with ROS and assisting robotics workshops in the project Oecherlab <a href="https://ifu.rwth-aachen.de/en/robotics-workshop-for-adults/#pll_switcher">(Click Link for Details)
        </a></p>
        <p>Semantic Segmentation of sidewalks in the project Urbant <a href=https://urbant.de/de/>(Click here for details)</a> </p>`,
        icon: 'mdi-robot-industrial',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      return items
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
