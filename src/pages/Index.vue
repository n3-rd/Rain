<template>
  <q-page>
    <div class="home-banner">
      <div class="date q-pl-md q-pt-md">
        <div class="app-week-day text-h4 text-weight-bolder">
          {{ appWeekDay }}
        </div>
        <div class="app-date text-h5 text-weight-bold">
          {{ appDay }} {{ appMonth }} {{ appYear }}
        </div>
        <div class="app-time text-h6">
          {{ appHour }} : {{ appMinute }} {{ appAm }}
        </div>
      </div>

      <!-- <div class="share-button q-pa-md q-ml-md cursor-pointer">
        <q-icon name="share" />
      </div> -->
    </div>

    <Sounds />
  </q-page>
</template>

<style lang="scss">
.home-banner {
  height: 30vh;
  background-image: url(~assets/img2.jpg);
  background-size: cover;
background-repeat: no-repeat;
background-blend-mode: darken;
background-position: left;
  backdrop-filter: brightness(60%);
  border-radius: 0 0 20px 20px;
  .share-button {
    background-color: rgba(255, 255, 255, 0.377);
    width: 3.2rem;
    text-align: center;
    border-radius: 50%;
    height: 3.2rem;
    position: absolute;
    top: 23%;
  }
  .date{
    opacity: .8;
  }
}
</style>

<script>
import { defineComponent } from "vue";
import { date } from "quasar";
import Sounds from "components/Sounds";

export default defineComponent({
  name: "PageIndex",
  components: {
    Sounds,
  },
  data() {
    return {
      appWeekDay: "",
      appDay: "",
      appMonth: "",
      appYear: "",
      appHour: "",
      appMinute: "",
      appAm: "",
      timeStamp: Date.now(),
      dateFormats: {
        days: [
          "Sunday",
          "Monday",
          "Tuesday",
          "Wednesday",
          "Thursday",
          "Friday",
          "Saturday",
        ],
        daysShort: ["Sun", "Mon", "Tue", "Wed", "Thur", "Fri", "Sat"],
        months: [
          "January",
          "Feburary",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        monthsShort: [
          "Jan",
          "Feb",
          "Mar",
          "Apr",
          "May",
          "Jun",
          "Jul",
          "Aug",
          "Sept",
          "Oct",
          "Nov",
          "Dec",
        ],
      },
      todayDay: date.formatDate(this.timeStamp, "DD", this.dateFormats),
      todayMonth: date.formatDate(this.timeStamp, "MMM", this.dateFormats),
    };
  },
  created() {
    const timeStamp = Date.now();
    const updateDate = () => {
      this.appWeekDay = date.formatDate(
        this.timeStamp,
        "dddd",
        this.dateFormats
      );
      this.appDay = date.formatDate(this.timeStamp, "DD", this.dateFormats);
      this.appMonth = date.formatDate(this.timeStamp, "MMM", this.dateFormats);
      this.appYear = date.formatDate(this.timeStamp, "YYYY", this.dateFormats);
      this.appHour = date.formatDate(this.timeStamp, "h", this.dateFormats);
      this.appMinute = date.formatDate(this.timeStamp, "mm", this.dateFormats);
      this.appAm = date.formatDate(this.timeStamp, "A", this.dateFormats);
    };

    setInterval(() => {
      this.timeStamp = Date.now();
      updateDate();
    }, 1000);
  },
});
</script>
