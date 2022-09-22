<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section title="Who am I?">
        I am a robotics engineer with an creative background.
        I started my journey as an art/music student in Bremen and discovered my passion
        for computer science and creative problem solving. Throughout my studies I gained
        experience in institutes working in the areas of virtual reality, robotics and computer vision.
        I am looking forward to new knowledge, new teams and new projects!
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template v-for="(skill, i) in skills">
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div class="mr-2 ml-2">
                <div class="align-center">
                  <v-icon small>
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="8"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({

    educations: [
      {
        from       : '2020',
        to         : '2022',
        title      : "Master's degree, Computer Science",
        location   : 'RWTH Aachen',
        description:
          'Thesis: An Approach to Instance Segmentation and Pose Estimation for Automated Dismantling of Lithium-Ion Batteries for High-Quality Recycling (more details in the experiences section)',
      },
      {
        from       : '2016',
        to         : '2020',
        title      : "Bachelor's degree, Computer Science",
        location   : 'University of Bremen',
        description:
          'Thesis: Comparison of Global and Local Path Planners on TurtleBots in C++/Python/ROS at the German Research Center for Artificial Intelligence',
      },
      {
        from       : '2017',
        to         : '2020',
        title      : "Master's degree, Art-Media-Aesthetic Education and Music",
        location   : 'University of Bremen',
        description:
          'Thesis: Augmented Reality Technologies in Art Education',
      },
      {
        from       : '2018',
        to         : '2019',
        title      : 'Exchange student semester, Computer Science',
        location   : '한양대학교 (Hanyang University)',
        description:
          'Focus on Courses in the Area of AI, Algorithms and Computer Networks ',
      },
      {
        from       : '2014',
        to         : '2015',
        title      : 'Exchange student semester, Media Arts',
        location   : '한양대학교 (Hanyang University)',
        description: 'Focus on Courses in the Area of New Media Arts',
      },
      {
        from       : '2013',
        to         : '2017',
        title      : "Bachelor's degree, Art-Media-Aesthetic Education and Music ",
        location   : 'University of Bremen',
        description: 'Thesis: New Media Art Installations',
      },
    ],
    skills: [
      {
        title: 'Python',
        icon : 'mdi-language-python',
        value: 90,
      },
      {
        title: 'C++',
        icon : 'mdi-language-cpp',
        value: 85,
      },
      {
        title: 'Java',
        icon : 'mdi-language-java',
        value: 75,
      },
      {
        title: 'ROS',
        icon : 'mdi-robot',
        value: 85,
      },
      {
        title: 'Ubuntu',
        icon : 'mdi-ubuntu',
        value: 90,
      },
      {
        title: 'HTML, JS, CSS',
        icon : 'mdi-language-html5',
        value: 50,
      },
      {
        title: 'Unreal Engine',
        icon : 'mdi-unreal',
        value: 65,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 90,
      },
      { divider: true },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
