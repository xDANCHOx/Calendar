<template>
  <div class="home">
    <vue-cal
      ref="vuecal"
      active-view="week"
      locale="ru"
      click-to-navigate
      editable-events
      :events="computedEvents"
      class="vuecal--full-height-delete"
      :cell-click-hold="false"
      @cell-dblclick="
        $refs.vuecal.createEvent($event, 120, {
          title: 'Новое событие',
          class: 'sample'
        })
      "
    >
    </vue-cal>
  </div>
</template>
<script>
import "vue-cal/dist/vuecal.css";
import "vue-cal/dist/drag-and-drop.js";
import "vue-cal/dist/i18n/ru.js";
import events from "../../database.json";
import VueCal from "vue-cal";
export default {
  name: "Home",
  components: {
    VueCal
  },
  computed: {
    computedEvents() {
      return events.filter(item => {
        return (item.class = "sample");
      });
    }
  }
};
</script>
<style>
.vuecal__event.sample {
  background-color: #eeefc8;
  border: 1px solid rgb(235, 82, 82);
}
.vuecal--month-view .vuecal__cell {
  height: 80px;
}
.vuecal--month-view .vuecal__cell-content {
  justify-content: flex-start;
  height: 100%;
  align-items: flex-end;
}
.vuecal--month-view .vuecal__cell-date {
  padding: 4px;
}
.vuecal__flex .weekday-label {
  flex-direction: column;
}
.vuecal__weekdays-headings,
.vuecal__all-day {
  padding-right: 0 !important;
  padding-top: 20px;
  padding-bottom: 20px;
}
.vuecal__heading {
  height: auto;
}
.vuecal__flex .weekday-label span:last-child {
  font-size: 30px;
}
</style>
