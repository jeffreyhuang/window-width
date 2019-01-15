<template>
  <div>
    <!-- <p>{{ height }}</p> -->
    <section class="hero is-primary">
      <div class="hero-body">
        <div class="container item__container">
          <div class="item__result">
            <h1 class="title">
              {{ width }}
            </h1>
            <h2 class="subtitle">
              Width
            </h2>
          </div>

          <div class="item__result">
            <h1 class="title">
              {{ height }}
            </h1>
            <h2 class="subtitle">
              Height
            </h2>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      width: '',
      height: ''
    }
  },
  methods: {
    getWidth () {
      return window.innerWidth
    },
    getHeight () {
      return window.innerHeight
    },
    show () {
      this.width = this.getWidth()
      this.height = this.getHeight()
    },
    addEvent (object, type, callback) {
      if (object == null || typeof(object) == 'undefined')
        return

      if (object.addEventListener) {
        object.addEventListener(type, callback, false)
      } else if (object.attachEvent) {
        object.attachEvent("on" + type, callback)
      } else {
        object["on"+type] = callback
      }
    }
  },
  mounted () {
    this.show()
    this.addEvent(window, 'resize', event => this.show())
  }
}
</script>

<style>
.item__container {
  text-align: center;
}
.item__result {
  display: inline-block;
  margin: 0 10px;
}
</style>
