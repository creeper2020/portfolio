<template>
  <nav>
    <div class="container">
      <div class="nav-columns">
        <div class="nav-column">
          <div class="nav-label">Contact</div>
          <div class="nav-infos">
            <ul class="nav-info">
              <li class="nav-info-label">Email</li>
              <li>
                <a :href="`mailto:${email}`">{{ email }}</a>
              </li>
            </ul>
            <ul class="nav-info">
              <li class="nav-info-label">Phone</li>
              <li>
                <a :href="`tel:${phone}`">{{ phone }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
<script>
import { VITE_APP_CONFIG } from '../config';
export default {
  name: 'Navigation',
  setup() {
    return {
      email: VITE_APP_CONFIG.email,
      phone: VITE_APP_CONFIG.phone,
    };
  },
};
</script>

<style lang="scss" scoped>
nav {
  left: 0;
  top: -1px;
  width: 100%;
  height: 100%;
  z-index: 1;
  display: none;
  position: absolute;
  overflow: hidden;
  background: $yellow;
  a {
    position: relative;
    &:after {
      content: '';
      position: absolute;
      width: 0;
      height: 2px;
      display: block;
      margin-top: 5px;
      right: 0;
      background: $black;
      transition: 0.4s ease;
    }
    &:hover {
      color: pink;
      &:after {
        width: 100%;
        left: 0;
        background: $black;
      }
    }
  }
  .nav-columns {
    transform: translateY(125px);
    display: flex;
    padding: 0 32px;
    @include media('<=654px') {
      flex-direction: column;
      @include media('<=phone') {
        padding: 0 16px;
      }
    }
    .nav-column {
      width: 45%;
      @include media('<=654px') {
        width: 100%;
      }
      &:last-child {
        width: 55%;
        @include media('<=654px') {
          width: 100%;
        }
      }
      .nav-label {
        margin-bottom: 3rem;
        font-size: 1.2rem;
        @include media('<=tablet') {
          font-size: 1rem;
          margin-bottom: 1.4rem;
        }
        @include media('<=phone') {
          font-size: 0.875rem;
          margin-bottom: 1.2rem;
        }
      }
      .nav-infos {
        display: flex;
        flex-wrap: wrap;
        @include media('<=654px') {
          justify-content: space-between;
        }
        .nav-info {
          padding: 0;
          width: 50%;
          &:nth-child(3) {
            @include media('<=654px') {
              display: none;
            }
          }
          .nav-info-label {
            font-weight: 600;
          }
          li {
            font-weight: 300;
            list-style: none;
            font-size: 1.4rem;
            margin-bottom: 1.2rem;
            @include media('<=tablet') {
              font-size: 1.2rem;
              margin-bottom: 1rem;
            }
            @include media('<=phone') {
              font-size: 1rem;
              margin-bottom: 0.875rem;
            }
            a {
              text-decoration: none;
              color: $black;
            }
          }
        }
      }
      .nav-links {
        padding: 0;
        margin: 0;
        li {
          list-style: none;
          margin-bottom: 2.4rem;
          @include media('<=phone') {
            margin-bottom: 1.6rem;
          }
          a {
            font-weight: 600;
            font-size: 2.8rem;
            text-decoration: none;
            color: $black;
            @include media('<=phone') {
              font-size: 2rem;
            }
          }
        }
      }
    }
  }
}
</style>
