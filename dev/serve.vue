<script lang="ts">
import Vue from "vue";
import vueInteractiveTimeline from "@/vue-interactive-timeline.vue";

export default Vue.extend({
  name: "ServeDev",
  components: {
    vueInteractiveTimeline,
  },
});
</script>

<template>
  <div id="app">
    <vue-interactive-timeline
      :timeline-point="[
        'Sep 2018',
        'May 2019',
        'Aug 2020',
        'Oct 2021',
        'April 2020',
      ]"
    >
      <template>
        <li class="selected" ref="eventNumber">
          <h2 class="title">
            University of Duisburg-Essen<br /><img
              class="logo-image"
              alt="University of Duisburg-Essen"
              width="20%"
              height="20%"
            />
          </h2>
          <p>
            Hello, Since 2015 I have studied in Germany. I have a major in
            electrical and electronic engineering. During my university time, I
            spent time o Since 2015 I have studied in Germany. I have a major in
            electrical and electronic engineering. During my university time, I
            spent time o Since 2015 I have studied in Germany. I have a major in
            electrical and electronic engineering. During my university time, I
            spent time o Since 2015 I have studied in Germany. I have a major in
            electrical and electronic engineering. During my university time, I
            spent time o Since 2015 I have studied in Germany. I have a major in
            electrical and electronic engineering. During my university time, I
            spent time o Since 2015 I have studied in Germany. I have a major in
            electrical and electronic engineering. During my university time, I
            spent time o
          </p>
        </li>

        <li>
          <h2 class="title">
            Event title here<br /><img
              class="logo-image"
              alt="Kiwi standing on oval"
              width="20%"
              height="20%"
            />
          </h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illum
            praesentium officia, fugit recusandae ipsa, quia velit nulla
            adipisci? Con
          </p>
        </li>

        <li>
          <h2 class="title">
            Event title here<br /><img
              class="logo-image"
              alt="Kiwi standing on oval"
              width="20%"
              height="20%"
            />
          </h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illum
            praesentium officia, fugit recusandae ipsa, quia velit nulla
            adipisci? Con
          </p>
        </li>

        <li>
          <h2 class="title">
            Event title here<br /><img
              class="logo-image"
              alt="Kiwi standing on oval"
              width="20%"
              height="20%"
            />
          </h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illum
            praesentium officia, fugit recusandae ipsa, quia velit nulla
            adipisci? Con
          </p>
        </li>

        <li>
          <h2 class="title">
            Event title here<br /><img
              class="logo-image"
              alt="Kiwi standing on oval"
              width="20%"
              height="20%"
            />
          </h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illum
            praesentium officia, fugit recusandae ipsa, quia velit nulla
            adipisci? Con
          </p>
        </li>
      </template>
    </vue-interactive-timeline>
  </div>
</template>
