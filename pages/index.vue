<template>
  <v-card
    color="white"
    class="mx-auto"
    max-width="1500"
    outlined
  >
    <v-container>
      <v-row dense>
        <v-col
          v-for="(item, i) in items"
          :key="i"
          cols="12"
        >
          <v-card
            :color="item.color"
            outlined
            dark
          >
            <div class="d-flex flex-no-wrap">
              <img
                :src="item.src"
                class="image"
                width="400"
                height="400"
              >

              <div>
                <div class="pt-10 pl-12" style="font-size:30px">
                  <h1> <span class="black--text">New </span> <span class="amber--text">Winter</span>EW </h1>
                  <h1 class="black--text">
                    Arrivals
                  </h1>
                  <v-card-subtitle class="text-h6 black--text" v-text="item.artist" />
                </div>
                <v-card-actions>
                  <v-btn
                    class="ml-12 mt-3"
                    color="amber"
                    large
                    min-width="200"
                    @click="buyPage"
                  >
                    Buy Now
                  </v-btn>
                </v-card-actions>
              </div>
            </div>
          </v-card>
        </v-col>

        <v-col
          v-for="(item, i) in items2"
          :key="i"
          cols="4"
          class="img-wrapper"
        >
          <v-card
            :color="item.color"
            dark

            max-height="200"
          >
            <div class="inner-img d-flex flex-no-wrap">
              <v-img class="inner-img" :src="item.src" width="150" height="150" />

              <div>
                <v-card-subtitle v-text="item.artist" />

                <div class="text-right pb-10 pr-5">
                  <v-btn
                    class="white--text"
                    :color="item.color"
                    left
                    small
                    @click="buyPage"
                  >
                    Buy Now
                  </v-btn>
                </div>
              </div>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
export default {
  name: 'IndexPage',
  data () {
    return {
      items: [
        {
          color: 'white',
          src: '/2-shoe.png',
          title: 'Supermodel text sample',
          artist: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam aliquet tellus lectus, quis egestas turpis ornare sit amet. Nulla vel vestibulum ipsum, at pharetra orci. Suspendisse lectus risus, molestie ac elit vel, rhoncus laoreet neque.'
        }],
      items2: [
        {
          color: 'red darken-4',
          src: '/1-shoe.png',
          artist: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam aliquet tellus lectus, quis egestas turpis ornare sit amet. Nulla vel vestibulum ipsum.'
        },
        {
          color: 'brown lighten-1',
          src: '/2-shoe.png',
          artist: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam aliquet tellus lectus, quis egestas turpis ornare sit amet. Nulla vel vestibulum ipsum.'
        },
        {
          color: 'indigo darken-4',
          src: '/3-shoe.png',
          artist: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam aliquet tellus lectus, quis egestas turpis ornare sit amet. Nulla vel vestibulum ipsum.'
        }]
    }
  },
  methods: {
    buyPage () {
      this.$router.push('/buypage')
    }
  }
}
</script>
<style>
.img-wrapper {
  width: 400px;
  height: 400px;
  overflow: hidden;
}

.inner-img {
  transition: 0.3s;
}

.inner-img:hover {
  transform: scale(1.1);
}

/* Other styling elements, that are not necessary for the example */

.img-wrapper {
  display: inline-block;
  box-sizing: border-box;
}
</style>
