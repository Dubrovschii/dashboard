<script setup>
import logo from "../assets/img/Logo.svg";
import arrow from "../assets/img/sidebar-arrow.svg";
import iconschevron from "../assets/img/Chevron.svg";
import iconssearch from "../assets/img/Input.svg";
import iconshome from "../assets/img/Home.svg";
import iconsstar from "../assets/img/Features.svg";
import iconsusers from "../assets/img/Users.svg";
import iconspricing from "../assets/img/Pricing.svg";
import iconsintegrations from "../assets/img/Integrations.svg";

import iconssettings from "../assets/img/Settings.svg";
import iconswebflow from "../assets/img/Webflow.svg";
import iconsacc from "../assets/img/Group.svg";
</script>

<template>
  <section class="sidebar">
    <div class="sidebar__content">
      <div class="sidebar__head">
        <figure class="sidebar__logo">
          <img :src="logo" alt="logo" />
          Dashdark X
        </figure>
        <button class="sidebar__btn">
          <img :src="arrow" alt="arrow" />
        </button>
      </div>
      <div class="sidebar__menu">
        <div class="sidebar__menu_search-wrapper">
          <input
            class="sidebar__menu_search"
            type="text"
            placeholder="Search for..."
          />
          <img
            class="sidebar__search-icon"
            :src="iconssearch"
            alt="Search Icon"
          />
        </div>
        <div class="sidebar__menu_link active">
          <button class="sidebar__menu_btn link_active">
            <img :src="iconshome" alt="" class="preicons" />
            <span>Dashboard</span>
            <img :src="iconschevron" alt="" class="iconschevron" />
          </button>
          <div class="sidebar__menu_smallwr smallwr">
            <button class="smallwr__btn">All pages</button>
            <button class="smallwr__btn smallwr__btn_active">Reports</button>
            <button class="smallwr__btn">Products</button>
            <button class="smallwr__btn">Task</button>
          </div>
        </div>
        <div class="sidebar__menu_link">
          <button class="sidebar__menu_btn">
            <img :src="iconsstar" alt="" class="preicons" />
            <span>Features</span>
            <img :src="iconschevron" alt="" class="iconschevron" />
          </button>
        </div>
        <div class="sidebar__menu_link">
          <button class="sidebar__menu_btn">
            <img :src="iconsusers" alt="" class="preicons" />
            <span>Users</span>
            <img :src="iconschevron" alt="" class="iconschevron" />
          </button>
        </div>
        <div class="sidebar__menu_link">
          <button class="sidebar__menu_btn">
            <img :src="iconspricing" alt="" class="preicons" />
            <span>Pricing</span>
            <img :src="iconschevron" alt="" class="iconschevron" />
          </button>
        </div>
        <div class="sidebar__menu_link">
          <button class="sidebar__menu_btn">
            <img :src="iconsintegrations" alt="" class="preicons" />
            <span>Integrations</span>
            <img :src="iconschevron" alt="" class="iconschevron" />
          </button>
        </div>

        <div class="sidebar__menu_sub">
          <div class="sidebar__menu_link">
            <button class="sidebar__menu_btn">
              <img :src="iconssettings" alt="" class="preicons" />
              <span>Settings</span>
              <img :src="iconschevron" alt="" class="iconschevron" />
            </button>
          </div>
          <div class="sidebar__menu_link">
            <button class="sidebar__menu_btn">
              <img :src="iconswebflow" alt="" class="preicons" />
              <span>Template pages</span>
              <img :src="iconschevron" alt="" class="iconschevron" />
            </button>
          </div>
          <div class="sidebar__menu_link sidebar__menu_log">
            <button class="sidebar__menu_btn">
              <img :src="iconsacc" alt="" class="preicons" />
              <div class="sidebar__menu_btn_log">
                <span>John Carter</span>
                <span>Account settings</span>
              </div>
              <img :src="iconschevron" alt="" class="iconschevron" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.sidebar {
  max-width: 300px;
  width: 100%;
  background: var(--background-color);
  padding: 38px 28px;

  &__head {
    display: flex;
    justify-content: space-between;
  }

  &__logo {
    color: var(--color-white);
    font-size: 20px;
    line-height: 22px;
    font-weight: 600;
    display: flex;
    align-items: center;

    img {
      margin-right: 6px;
    }
  }

  &__menu {
    margin-top: 20px;
    display: flex;
    flex-flow: column;
    &_link {
      display: flex;
      align-items: center;
      height: 42px;
      position: relative;
    }
    &_btn {
      display: flex;
      align-items: center;
      width: 100%;
      font-size: 14px;
      color: #aeb9e1;
      padding: 0;
      span {
        margin-left: 6px;
      }
      .iconschevron {
        rotate: -90deg;
      }
      &_log {
        display: flex;
        flex-flow: column;
        align-items: start;
        span:first-child {
          color: var(--color-white);
        }
        span:last-child {
          font-size: 12px;
          font-weight: 400;
        }
      }
    }
    &_sub {
      position: relative;
      margin-top: 21px;
      .sidebar__menu_link:first-child {
        margin-top: 21px;
      }
    }
    &_sub::before {
      content: "";
      width: calc(100% + 30px);
      height: 1px;
      display: block;
      background: #343b4f;
      position: absolute;
      left: -28px;
    }
    &_log {
      margin-top: 21px;
    }
  }

  .sidebar__btn {
    background: none;
    border: none;
    cursor: pointer;
  }
  .sidebar__menu_search-wrapper {
    position: relative;
    margin-bottom: 30px;
  }

  .sidebar__menu_search {
    width: 100%;
    padding: 10px 40px 10px 38px;
    font-size: 12px;
    font-weight: 400;
    line-height: 14px;
    border: 1px solid #343b4f;
    border-radius: 4px;
    outline: none;
    background: #0b1739;
    color: #aeb9e1;
  }

  .sidebar__search-icon {
    position: absolute;
    left: 10px;
    top: 50%;
    transform: translateY(-50%);
    width: 13px;
    height: 13px;
    pointer-events: none;
  }
}

.active {
  min-height: 218px;
  .link_active {
    position: absolute;
    top: 0;
  }
  span {
    color: #cb3cff;
  }
  .iconschevron {
    rotate: 0deg;
  }
}

.smallwr {
  display: flex;
  flex-flow: column;
  height: 100%;
  position: absolute;
  top: 42px;
  height: calc(218px - 42px);
  width: 100%;
  &__btn {
    color: #aeb9e1;
    height: 42px;
    padding: 0;
    text-align: left;
    width: 100%;
    display: block;
    &_active {
      color: var(--color-white);
      background: #0a1330;
      position: relative;
      display: flex;
      align-items: center;
      padding-left: 11px;
    }
    &_active::before {
      content: "";
      width: 3px;
      height: 100%;
      display: block;
      background: #cb3cff;
      position: absolute;
      left: 0;
      border-top-left-radius: 4px;
      border-bottom-left-radius: 4px;
    }
  }
}
.iconschevron {
  position: absolute;
  right: 0;
}
</style>
