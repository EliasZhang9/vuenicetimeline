<script lang="ts">
import Vue from "vue";
import { PropType } from "vue";

interface timelineComponentsTypes {
  timelineWrapper?: Element | null;
  eventsWrapper?: Element | null;
  fillingLine?: Element | null;
  timelineEvents?: NodeList | null;
}

export default Vue.extend({
  name: "vueInteractiveTimeline", // vue component name
  props: {
    timelinePoint: {
      type: Array as PropType<string[]>,
      required: true,
      validator: function (value) {
        let checkIfString = value.every((i) => typeof i === "string");
        if (!checkIfString) {
          console.error("All variables in the array need to be string");
        }
        return checkIfString;
      },
    },
  },
  data(): {
    counter: number;
    initCounter: number;
    message: {
      action: string | null;
      amount: number | null;
    };
  } {
    return {
      counter: 5,
      initCounter: 5,
      message: {
        action: null,
        amount: null,
      },
    };
  },
  created: function () {
    console.info(123456, this.timelinePoint);
    //this.$slots[0];
    // this!.$slots["eventsContent"]![0]!.data!.class = {};
  },
  mounted() {
    let eventContent = this.$refs["eventContent"] as Element;
    let testElement = eventContent.querySelector("li");
    testElement?.classList.add("hello");
    console.info(1234, testElement);
    console.info(this.$slots);
    this.$slots.default?.forEach(function (vnode) {
      let style = {
        backgroundColor: "#77DD77",
        display: "inline-block",
        padding: "5px",
        fontFamily: "Arial",
      };
      vnode.data = vnode.data || {};
      vnode.data.style = style;
      vnode.data.staticClass = "hello";
      console.info(vnode);
    });
    if (this.$slots.eventsContent && this.$slots.eventsContent.length > 0) {
      let a = this.$slots.eventsContent[0];
      if (a.data) {
        a.data["staticClass"] = "hello";
      }

      console.info("wse", a);
    }
    this.initTimeline();
  },

  computed: {},
  methods: {
    decrement(arg: Event | number): void {
      const amount = typeof arg !== "number" ? 1 : arg;
      this.counter -= amount;
      this.message.action = "decremented by";
      this.message.amount = amount;
    },

    initTimeline(): void {
      let timelineComponents: timelineComponentsTypes = {};
      timelineComponents["timelineWrapper"] =
        this.$el.querySelector(".events-wrapper");
      if (timelineComponents["timelineWrapper"]) {
        timelineComponents["eventsWrapper"] =
          timelineComponents["timelineWrapper"].querySelector(".events");
      }
      if (timelineComponents["eventsWrapper"]) {
        timelineComponents["fillingLine"] =
          timelineComponents["eventsWrapper"].querySelector(".filling-line");
      }

      if (timelineComponents["eventsWrapper"]) {
        timelineComponents["timelineEvents"] =
          timelineComponents["eventsWrapper"].querySelectorAll("a");
      }
      if (timelineComponents["timelineEvents"])
        this.parseDate(timelineComponents["timelineEvents"]);

      if (timelineComponents["eventsWrapper"]) {
        console.info(timelineComponents);
      }

      /*if (typeof this !== "undefined") {
        console.info(this.$refs["cd-horizontal-timeline"].querySelector('.events-wrapper'))
      }*/
    },
    parseDate(events: NodeList) {
      //let dateArrays = [];
      events.forEach((event: Node) => {
        console.info(123, event);
        /* let dateComp = $(this)
            .data('date')
            .split('/'),
          newDate = new Date(dateComp[2], dateComp[1] - 1, dateComp[0])*/
        //dateArrays.push(newDate)
      });
      return 1;
    },
  },
});
</script>

<template>
  <section class="cd-horizontal-timeline" ref="cd-horizontal-timeline">
    <div class="timeline">
      <div class="events-wrapper">
        <div class="events">
          <ol>
            <li
              v-for="(point, index) in timelinePoint"
              v-bind:key="point + index"
            >
              <a v-if="index === 0" class="selected">{{ point }}</a>
              <a v-else>{{ point }}</a>
            </li>
          </ol>
          <span class="filling-line" aria-hidden="true" />
        </div>
        <!-- .events -->
      </div>
      <!-- .events-wrapper -->

      <ul class="cd-timeline-navigation">
        <li><a href="#0" class="prev inactive">Prev</a></li>
        <li><a href="#0" class="next">Next</a></li>
      </ul>
      <!-- .cd-timeline-navigation -->
    </div>
    <!-- .timeline -->

    <div class="events-content" ref="eventContent">
      <ol>
        <slot></slot>
      </ol>
    </div>
    <!-- .events-content -->
  </section>
</template>

<style scoped>
.cd-horizontal-timeline {
  font-weight: 400;
  position: relative;
}
.cd-horizontal-timeline .timeline {
  position: relative;
  height: 100px;
  margin: 0 auto;
  max-width: 800px;
  width: 90%;
}
.cd-horizontal-timeline .events-wrapper {
  position: relative;
  height: 100%;
  margin: 0 40px;
  overflow: hidden;
}
.cd-horizontal-timeline .events {
  /* this is the grey line/timeline */
  position: absolute;
  z-index: 1;
  left: 0;
  top: 50%;
  height: 2px;
  /* width will be set using JavaScript */
  background: #dfdfdf;
}

.cd-horizontal-timeline .filling-line {
  /* this is used to create the green line filling the timeline */
  position: absolute;
  z-index: 1;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  background-color: red;
  transform: scaleX(0);
  transform-origin: left center;
}

.cd-horizontal-timeline .events a {
  position: absolute;
  top: 0;
  font-size: 0.8rem;
  z-index: 2;
  text-align: center;
  padding-bottom: 15px;
}

.cd-horizontal-timeline .events a::after {
  /* this is used to create the event spot */
  content: "";
  position: absolute;
  left: 50%;
  bottom: -5px;
  height: 12px;
  width: 12px;
  border-radius: 50%;
  border: 2px solid #dfdfdf;
  background-color: #f8f8f8;
}

.cd-horizontal-timeline .events a.selected {
  pointer-events: none;
}
.cd-horizontal-timeline .events a.selected::after {
  background-color: red;
  border-color: red;
}

.cd-horizontal-timeline .events a.older-event::after {
  border-color: blue;
}
</style>
