<script setup>
import { ref, computed, onMounted } from "vue";
import Sidebar from "./Sidebar.vue";
import arrowdown from "../assets/img/arrow-down.svg";
import Grafic from "./Grafic.vue";
import Session from "./Session.vue";
import iconsview from "../assets/img/Views.svg";
import iconsuser from "../assets/img/Users.svg";
import iconsadd from "../assets/img/Signups.svg";
import iconsstar from "../assets/img/Features.svg";
import arrowUp from "../assets/img/ArrowGreen.svg";
import arrowDown from "../assets/img/ArrowRed.svg";
import iconstotal from "../assets/img/Sales.svg";
import iconscalendar from "../assets/img/Calendar.svg";
import iconschevron from "../assets/img/Chevron.svg";
import iconstime from "../assets/img/time.svg";
import figma from "@/assets/img/Figma.svg";

import VueDatePicker from "@vuepic/vue-datepicker";
import "@vuepic/vue-datepicker/dist/main.css";

const itemsInfo = [
  {
    icons: iconsview,
    pretitle: "Pageviews",
    title: "50.8K",
    subtitle: "28.4%",
    status: "up",
  },
  {
    icons: iconsuser,
    pretitle: "Monthly users",
    title: "23.6K",
    subtitle: "12.6%",
    status: "down",
  },
  {
    icons: iconsadd,
    pretitle: "New sign ups",
    title: "756",
    subtitle: "3.1%",
    status: "up",
  },
  {
    icons: iconsstar,
    pretitle: "Subscriptions",
    title: "2.3K",
    subtitle: "11.3%",
    status: "up",
  },
];
const revenue = ref(true);
const dateSearch = ref("Jan 2024 - Dec 2024");
// const dateRange = ref([new Date("2024-01-01"), new Date("2024-12-01")]);
// const date = new Date();
// onMounted(() => {
//   setTimeout(() => {
//     const calendar = document.querySelector(".dp__main");
//     if (calendar) {
//       calendar.classList.remove("dp__theme_light");
//     }
//   }, 0);
// });
</script>

<template>
  <div class="dashboard">
    <Sidebar />
    <div class="container container__mediu">
      <div class="dashboard__content">
        <img :src="figma" alt="" class="figma" />
        <div class="dashboard__head">
          <div class="dashboard__head_text">
            <div class="dashboard__title">Welcome back, John</div>
            <div class="dashboard__descr">
              Measure your advertising ROI and report website traffic.
            </div>
          </div>
          <div class="dashboard__head_btn">
            <button class="btn btn__blue">
              Export data <img :src="arrowdown" alt="" />
            </button>
            <button class="btn btn__pink">Create report</button>
          </div>
        </div>
        <div class="dashboard__info col-sm-12">
          <div class="row dashboard__info_row">
            <div
              class="col-sm-4 dashboard__info_block block"
              v-for="(item, index) in itemsInfo"
              :key="index"
            >
              <div class="block__head">
                <div class="block__pretitle">
                  <img :src="item.icons" alt="" />
                  {{ item.pretitle }}
                </div>
                <button class="block__more"></button>
              </div>
              <div class="block__info">
                <div class="block__title">
                  {{ item.title }}
                </div>
                <div
                  :class="[
                    'block__descr',
                    item.status === 'up'
                      ? 'block__descr_green'
                      : 'block__descr_red',
                  ]"
                >
                  {{ item.subtitle }}
                  <img :src="arrowUp" alt="" v-if="item.status === 'up'" />
                  <img :src="arrowDown" alt="" v-if="item.status === 'down'" />
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="dashboard__total total">
          <div class="total__block diagram">
            <div class="diagram__wrap">
              <div class="total__block_head">
                <div class="total__block_pretitle">Total revenue</div>
                <div class="total__block_title">
                  <div class="cash">$240.8K</div>
                  <div class="percent percent_green" v-if="revenue">
                    24.6% <img :src="arrowUp" alt="" />
                  </div>
                </div>
              </div>
              <div class="total__block_more">
                <div class="revenue">Revenue</div>
                <div class="expenses">Expenses</div>

                <div class="calendar">
                  <img :src="iconscalendar" alt="" />
                  {{ dateSearch }}
                  <img :src="iconschevron" alt="" />
                </div>
              </div>
            </div>
            <Grafic />
          </div>
          <div class="total__block more">
            <div class="total__block_head">
              <div class="total__block_pretitle">
                <img :src="iconstotal" alt="" />
                Total profit
              </div>
              <div class="total__block_title">
                <div class="cash">$144.6K</div>
                <div class="percent percent_green" v-if="revenue">
                  28.5% <img :src="arrowUp" alt="" />
                </div>
              </div>
            </div>
            <div class="more__diagram">
              <div class="more__diagram_start">
                <div class="more__diagram_row">
                  <div class="more__diagram_item item">
                    <div class="item__span">
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                      <span></span>
                    </div>
                  </div>
                  <div class="item__time">
                    <div class="item__descr">12AM</div>
                    <div class="item__descr">12AM</div>
                    <div class="item__descr">12AM</div>
                    <div class="item__descr">12AM</div>
                  </div>
                </div>
              </div>
              <div class="more__diagram_end">
                <div class="more__diagram_text">Last 12 months</div>
                <button class="more__diagram_btn">View report</button>
              </div>
            </div>
            <div class="more__session">
              <div class="total__block_head">
                <div class="total__block_pretitle">
                  <img :src="iconstime" alt="" />
                  Total sessions
                </div>

                <div class="total__block_title">
                  <div class="cash">400</div>
                  <div class="percent percent_green" v-if="revenue">
                    16.8% <img :src="arrowUp" alt="" />
                  </div>
                </div>
              </div>
              <Session />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.dashboard .container {
  padding: 0;
}
.figma {
  position: absolute;
  right: -25px;
  top: -25px;
}
.dashboard {
  display: flex;

  border-top-left-radius: 24px;
  border-bottom-left-radius: 4px;
  &__content {
    position: relative;
    background: var(--background-color);
    padding: 35px 46px;
    padding-bottom: 0;
    display: flex;
    flex-flow: column;
  }
  &__head {
    display: flex;
    justify-content: space-between;
    &_text {
      display: flex;
      flex-flow: column;
      color: var(--color-white);
    }
    &_btn {
      display: flex;
      gap: 12px;
      .btn {
        min-width: 99px;
        width: 100%;
        height: 30px;
        color: var(--color-white);
        border-radius: 4px;
        &__blue {
          background: #0a1330;
        }
        &__pink {
          background: #cb3cff;
        }
      }
    }
  }
  &__info {
    margin-top: 32px;
    &_row {
      display: flex;
      margin-right: -16px;
      margin-left: -16px;
    }

    &_block {
      border: 1px solid #343b4f;
      background: #0b1739;
      border-radius: 8px;
    }
  }
  &__title {
    font-size: 24px;
    font-weight: 600;
    line-height: 32px;
  }
  &__descr {
    color: #aeb9e1;
    font-weight: 400;
    font-size: 12px;
    line-height: 14px;
    margin-top: 4px;
  }
  .block {
    padding: 21px 20px 17px 20px;
    margin: 0 8px;
    &__head {
      display: flex;
      justify-content: space-between;
    }
    &__more {
      background: url("../assets/img/Dots.svg");
      width: 16px;
      height: 16px;
      display: block;
    }
    &__pretitle {
      color: #aeb9e1;
      font-size: 12px;
      line-height: 14px;
      font-weight: 400;
      display: flex;
      align-items: center;
      img {
        margin-right: 4px;
      }
    }
    &__title {
      font-size: 24px;
      line-height: 32px;
      font-weight: 600;
      color: var(--color-white);
    }
    &__info {
      margin-top: 15px;
      display: flex;
      align-items: center;
    }
    &__descr {
      font-size: 10px;
      line-height: 14px;
      font-weight: 400;
      padding: 2px 4px;
      margin-left: 6px;
      border-radius: 2px;
      height: 20px;
      &_green {
        background-color: rgba(5, 193, 104, 0.2);
        border: 1px solid rgba(5, 193, 104, 0.2);
        color: #14ca74;
      }
      &_red {
        background-color: rgba(255, 90, 101, 0.2);

        border: 1px solid rgba(255, 90, 101, 0.2);
        color: #ff5a65;
      }
    }
  }
  .block:first-child {
    margin-left: 0;
  }
  .block:last-child {
    margin-right: 0;
  }
  &__total,
  .total {
    margin-top: 17px;
    background: #0b1739;
    border: 1px solid #343b4f;
    border-radius: 8px;
    display: flex;
    .diagram {
      max-width: 676px;
      width: 100%;
      padding: 41px 41px 37px 41px;
      position: relative;
      &__wrap {
        display: flex;
        justify-content: space-between;
      }
    }
    .more {
      max-width: 370px;
      width: 100%;
    }

    &__block {
      &_pretitle {
        font-size: 14px;
        line-height: 14px;
        color: #aeb9e1;
        font-weight: 400;
        margin-bottom: 10px;
      }
      &_title {
        display: flex;
        align-items: center;
      }
      &_more {
        color: #aeb9e1;
        display: flex;
        align-items: center;
      }
    }
  }
  .cash {
    font-size: 24px;
    line-height: 32px;
    font-weight: 600;
    color: var(--color-white);
  }

  .percent {
    font-size: 10px;
    line-height: 14px;
    font-weight: 400;
    padding: 2px 4px;
    margin-left: 6px;
    border-radius: 2px;
    height: 20px;
    &_green {
      background-color: rgba(5, 193, 104, 0.2);
      border: 1px solid rgba(5, 193, 104, 0.2);
      color: #14ca74;
    }
    &_red {
      background-color: rgba(255, 90, 101, 0.2);

      border: 1px solid rgba(255, 90, 101, 0.2);
      color: #ff5a65;
    }
  }
}
.more {
  padding: 25px 27px;
  position: relative;
  &__diagram {
    margin-top: 27px;
    margin-bottom: 21px;
    position: relative;
    &_row {
      display: flex;
      flex-flow: column;
      max-width: 312px;
    }
    &_item {
      padding-left: 9px;
      padding-right: 9px;
      span:before {
        content: "";
        width: 4px;
        height: 50px;
        display: block;
        margin: 0 3.5px;
        box-sizing: content-box;
      }

      span:nth-child(odd):before {
        background-color: #cb3cff;
      }
      span:nth-child(even):before {
        background-color: #00c2ff;
      }
      span:nth-child(2):before {
        height: 41px;
      }
      span:nth-child(4):before {
        height: 31px;
      }
      span:nth-child(5):before {
        height: 45px;
      }
      span:nth-child(6):before {
        height: 15px;
      }
      span:nth-child(7):before {
        height: 41px;
      }
      span:nth-child(8):before {
        height: 59px;
      }
      span:nth-child(10):before {
        height: 36px;
      }
      span:nth-child(11):before {
        height: 59px;
      }
      span:nth-child(12):before {
        height: 43px;
      }
      span:nth-child(13):before {
        height: 52px;
      }
      span:nth-child(14):before {
        height: 25px;
      }
      span:nth-child(15):before {
        height: 43px;
      }
      span:nth-child(16):before {
        height: 33px;
      }
      span:nth-child(17):before {
        height: 52px;
      }
      span:nth-child(18):before {
        height: 43px;
      }
      span:nth-child(19):before {
        height: 31px;
      }
      span:nth-child(20):before {
        height: 56px;
      }
      span:nth-child(21):before {
        height: 40px;
      }
      span:nth-child(22):before {
        height: 46px;
      }
      span:nth-child(23):before {
        height: 28px;
      }
      span:nth-child(24):before {
        height: 52px;
      }
      span:nth-child(25):before {
        height: 44px;
      }
      span:nth-child(26):before {
        height: 56px;
      }
    }
    &_end {
      display: flex;
      justify-content: space-between;
      margin-top: 32px;
    }
    &_text {
      color: #aeb9e1;
      font-weight: 400;
      font-size: 12px;
      line-height: 14px;
    }
    &_btn {
      color: #cb3cff;
      font-weight: 400;
      font-size: 12px;
      line-height: 14px;
    }
  }
  .item {
    display: flex;
    flex-flow: column;
    justify-content: start;
    &__span {
      display: flex;
      align-items: end;
      max-width: 284px;
      width: 100%;
    }
    &__time {
      display: flex;
      align-items: end;
      color: #aeb9e1;
      justify-content: space-between;
      font-size: 8px;
      line-height: 12px;
      font-weight: 400;
      margin-top: 7px;
      max-width: 300px;
    }
  }
  &__diagram::after {
    content: "";
    display: block;
    width: calc(100% + 54px);
    height: 1px;
    background: #343b4f;
    position: absolute;
    left: -27px;
    bottom: -21px;
    opacity: 0.6;
  }
  &__session {
    .total__block_head {
      margin-top: 49px;
    }
    .total__block_title {
      margin-bottom: 22px;
    }
  }
}
.more::before {
  content: "";
  display: block;
  width: 1px;
  height: 100%;
  background: #343b4f;
  position: absolute;
  left: 0;
  top: 0;
  opacity: 0.6;
}
.revenue {
  display: flex;
  align-items: center;
  font-size: 12px;
  line-height: 14px;
  font-weight: 400;
}
.revenue::before {
  content: "";
  display: block;
  width: 7px;
  height: 7px;
  background: #cb3cff;
  border-radius: 50%;
  margin-right: 8px;
}
.expenses {
  display: flex;
  align-items: center;
  font-size: 12px;
  line-height: 14px;
  font-weight: 400;
  margin-left: 24px;
}
.expenses::before {
  content: "";
  display: block;
  width: 7px;
  height: 7px;
  background: #00c2ff;
  border-radius: 50%;
  margin-right: 8px;
}
.calendar {
  height: 30px;
  padding: 9px;
  margin-left: 17px;
  background: #0a1330;
  display: flex;
  align-items: center;
  border-radius: 4px;
  img:first-child {
    margin-right: 4px;
  }
  img:last-child {
    margin-left: 12px;
  }
}
@media (max-width: 1440px) {
  .dashboard__content {
    max-width: 1200px;
    padding: 35px 20px;
  }
  .dashboard .total .diagram {
    max-width: 400px;
    padding: 35px 20px;
  }
  .total__block_more {
    flex-flow: column;
    justify-content: start;
    align-items: start !important;
    gap: 10px;
  }
  .expenses {
    margin-left: 0;
  }
  .calendar {
    margin-left: 0;
  }
  .diagram__wrap {
    flex-flow: column;
  }
  .grafic {
    width: 350px !important;
    height: 294px !important;
    object-fit: unset;
  }
}
@media (max-width: 1024px) {
  .dashboard__content {
    max-width: 800px;
    padding: 35px 15px;
  }
}
</style>
