<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
    </div>-->
    <transition name="fade" mode="out-in">
      <router-view />
    </transition>
    <footer>
      <ul class="link-list">
        <li>
          <a
            href="https://www.instagram.com/hellofarnsco"
            target="_blank"
            rel="noopener noreferrer"
          >
            <font-awesome-icon :icon="['fab', 'instagram']" size="lg" />@hellofarnsco
          </a>
        </li>
        <li>
          <a
            href="https://www.anacorteswa.gov/333/Museum"
            target="_blank"
            rel="noopener noreferrer"
          >
            <font-awesome-icon :icon="['fas', 'school']" size="lg" />Anacortes Museum
          </a>
        </li>
        <li>
          <a
            href="https://www.anacorteswa.gov/422/Maritime-Heritage-Center-and-the-WT-Pres"
            target="_blank"
            rel="noopener noreferrer"
          >
            <font-awesome-icon :icon="['fas', 'ship']" size="lg" />W. T. Preston
          </a>
        </li>
      </ul>
    </footer>
  </div>
</template>

<style lang="scss">
@import "@/assets/scss/global.scss";
// Transition Styles
.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.3s;
  transition-property: opacity;
  transition-timing-function: ease;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}

// Typography
a {
  color: rgba(0, 0, 0, 0.75);
  font-weight: bold;
  text-decoration: none;

  transition: all 0.25s;

  &:hover {
    color: rgba(0, 0, 0, 1);
    text-decoration: underline;
  }
}

#app {
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
footer {
  background-color: rgba(0, 0, 0, 0.75);
  color: white;
  padding: 10px;

  a {
    color: rgba(255, 255, 255, 0.75);
    font-weight: bold;
    text-decoration: none;

    transition: all 0.25s;

    &:hover {
      color: rgba(255, 255, 255, 1);
      text-decoration: underline;
    }
  }

  .link-list {
    li {
      display: inline-block;

      padding: 5px;
      border-radius: 5px;

      background-color: rgba(0, 0, 0, 0);

      transition: background-color 0.25s;

      &:hover {
        background-color: rgba(0, 0, 0, 0.15);

        svg.svg-inline--fa {
          opacity: 1;
          transition: opacity 0.5s;
        }
      }

      svg.svg-inline--fa {
        margin-right: 5px;
        opacity: 0;
      }

      @media screen and (max-width: 960px) {
        display: block;
        padding: 10px 0;

        &:hover {
          background-color: rgba(0, 0, 0, 0);

          svg.svg-inline--fa {
            opacity: 1;
            transition: opacity 0.5s;
          }
        }

        svg.svg-inline--fa {
          margin-right: 5px;
          opacity: 1;
        }
      }
    }
  }
}
</style>
