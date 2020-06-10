<template>
  <v-card
  class="mx-auto"
  >


    <v-container>
      <v-row dense>
        <v-col cols="12">
          <v-card
            color="#385F73"
            dark
          >
            <v-card-title class="headline">Unlimited music now</v-card-title>

            <v-card-subtitle>Listen to your favorite artists and albums whenever and wherever, online and offline.</v-card-subtitle>

            <v-card-actions>
              <v-btn text>Listen Now</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>

        <v-col
          v-for="(item, i) in items"
          :key="i"
          cols="4"
        >
          <v-card
            :color="item.color"
            dark
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title
                  class="headline"
                  v-text="item.title"
                ></v-card-title>

                <v-card-subtitle v-text="item.artist"></v-card-subtitle>
              </div>

              <v-avatar
                class="ma-3"
                size="125"
                tile
              >
                <v-img :src="item.src"></v-img>
              </v-avatar>
            </div>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="6">
        <v-card
            class="mt-12 max-auto"
          >
            <v-sheet
              class="v-sheet--offset mx-auto"
              color="cyan"
              elevation="12"
              max-width="calc(100% - 32px)"
            >
              <v-sparkline
                :labels="labels"
                :value="value1"
                color="white"
                line-width="2"
                padding="16"
              ></v-sparkline>
            </v-sheet>

            <v-card-text class="pt-0">
              <div class="title font-weight-light mb-2">User Registrations</div>
              <div class="subheading font-weight-light grey--text">Last Campaign Performance</div>
              <v-divider class="my-2"></v-divider>
              <v-icon
                class="mr-2"
                small
              >
                mdi-clock
              </v-icon>
              <span class="caption grey--text font-weight-light">last registration 26 minutes ago</span>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-container fluid>
            <v-sparkline
              :fill="fill"
              :gradient="gradient"
              :line-width="width"
              :padding="padding"
              :smooth="radius || false"
              :value="value"
              auto-draw
            ></v-sparkline>

            <v-divider></v-divider>

            <v-row>
              <v-col
                cols="12"
                md="6"
              >
                <v-row class="fill-height" align="center">
                  <v-item-group v-model="gradient" mandatory>
                    <v-row>
                      <v-item
                        v-for="(gradient, i) in gradients"
                        :key="i"
                        v-slot:default="{ active, toggle }"
                        :value="gradient"
                      >
                        <v-card
                          :style="{
                            background: gradient.length > 1
                              ? `linear-gradient(0deg, ${gradient})`
                              : gradient[0],
                            border: '2px solid',
                            borderColor: active ? '#222' : 'white'
                          }"
                          width="30"
                          height="30"
                          class="mr-2"
                          @click.native="toggle"
                        ></v-card>
                      </v-item>
                    </v-row>
                  </v-item-group>
                </v-row>
              </v-col>

              <v-col
                cols="12"
                md="6"
              >
                <v-slider
                  v-model="width"
                  label="Width"
                  min="0.1"
                  max="10"
                  step="0.1"
                  thumb-label
                ></v-slider>
              </v-col>

              <v-col cols="6">
                <v-row class="fill-height" align="center">
                  <v-switch v-model="fill" label="Filled"></v-switch>
                </v-row>
              </v-col>

              <v-col
                cols="12"
                md="6"
              >
                <v-slider
                  v-model="radius"
                  label="Radius"
                  min="0"
                  max="25"
                  thumb-label
                ></v-slider>
              </v-col>

              <v-col
                cols="12"
                md="6"
                offset-md="6"
              >
                <v-slider
                  v-model="padding"
                  label="Padding"
                  min="0"
                  max="25"
                  thumb-label
                ></v-slider>
              </v-col>
            </v-row>
          </v-container>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>
<script>
const gradients = [
   ['#222'],
   ['#42b3f4'],
   ['red', 'orange', 'yellow'],
   ['purple', 'violet'],
   ['#00c6ff', '#F0F', '#FF0'],
   ['#f72047', '#ffd200', '#1feaea'],
 ]
  export default {
    data: () => ({
      fill: true,
      gradient: gradients[4],
      gradients,
      padding: 8,
      radius: 10,
      value: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0],
      width: 2,
      items: [
        {
          color: '#1F7087',
          src: 'https://cdn.vuetifyjs.com/images/cards/foster.jpg',
          title: 'Supermodel',
          artist: 'Foster the People',
        },
        {
          color: '#952175',
          src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
          title: 'Halcyon Days',
          artist: 'Ellie Goulding',
        },
        {
          color: '#952175',
          src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
          title: 'Halcyon Days',
          artist: 'Ellie Goulding',
        },
      ],
      labels: [
        '12am',
        '3am',
        '6am',
        '9am',
        '12pm',
        '3pm',
        '6pm',
        '9pm',
      ],
      value1: [
        200,
        675,
        410,
        390,
        310,
        460,
        250,
        240,
      ],
    }),
  }
</script>