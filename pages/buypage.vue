<template>
  <transition name="home">
    <div>
      <v-card
        color="black"
        class="mx-auto"
        max-width="2000"
        outlined
        rounded
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
                      <h1> <span class="white--text">Buy </span> <span class="amber--text">Women Shoe</span></h1>
                      <h1 class="white--text">
                        Now
                      </h1>
                      <v-card-subtitle class="text-h6 white--text" v-text="item.artist" />
                    </div>
                  </div>
                </div>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
      <v-container class="grey lighten-5">
        <v-form ref="form" @submit.prevent="onSubmit">
          <v-row>
            <v-col md="6" class="ml-md-auto">
              <v-card class="pa-2" outlined tile rounded>
                <v-container>
                  <p><b>Billing Address</b></p>
                  <v-row>
                    <v-col
                      cols="12"
                      sm="6"
                    >
                      <v-text-field
                        v-model="first"
                        label="First Name"
                        :rules="fieldRules"
                        outlined
                      />
                    </v-col>

                    <v-col
                      cols="12"
                      sm="6"
                    >
                      <v-text-field
                        v-model="last"
                        label="Last Name"
                        :rules="fieldRules"
                        outlined
                      />
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col
                      cols="12"
                      sm="12"
                    >
                      <v-text-field
                        v-model="email"
                        label="Email Address"
                        :rules="emailRules"
                        outlined
                      />
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col
                      cols="12"
                      sm="12"
                    >
                      <v-text-field
                        v-model="address"
                        label="Street Address"
                        :rules="fieldRules"
                        outlined
                      />
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col
                      cols="12"
                      sm="12"
                    >
                      <v-text-field
                        v-model="address"
                        :rules="fieldRules"
                        outlined
                      />
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col
                      cols="12"
                      sm="6"
                    >
                      <v-select
                        v-model="state"
                        :items="states"
                        :rules="fieldRules"
                        outlined
                        label="State/Province"
                      />
                    </v-col>

                    <v-col
                      cols="12"
                      sm="6"
                    >
                      <v-text-field
                        v-model="city"
                        label="City"
                        :rules="fieldRules"
                        outlined
                      />
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col
                      cols="12"
                      sm="6"
                    >
                      <v-text-field
                        v-model="pin"
                        label="Zip/Postal Code"
                        :rules="pinRules"
                        outlined
                      />
                    </v-col>

                    <v-col
                      cols="12"
                      sm="6"
                    >
                      <v-text-field
                        v-model="phone"
                        label="Phone"
                        :rules="phoneNumberRules"
                        outlined
                      />
                    </v-col>
                  </v-row>
                  <v-checkbox
                    v-model="checkbox"
                    label="My billing and shipping address are the same"
                  />
                  <v-checkbox
                    v-model="account"
                    label="Create an account for latter use"
                  />
                </v-container>
              </v-card>
              <v-card class="pa-2" outlined tile rounded>
                <v-card>
                  <v-card-title class="blue darken-1 white--text font-weight-black title">
                    PAYMENT
                    DETAILS<v-spacer />

                    <v-img
                      aspect-ratio="3.075"
                      max-height="40"
                      :src="URL_IMAGE"
                      position="right"
                      contain
                    />
                  </v-card-title>

                  <v-card-text class="pb-10">
                    <v-row>
                      <v-col cols="6">
                        <v-subheader class="grey--text text--lighten-1 pl-0 subheader">
                          CARDHOLDER NAME
                        </v-subheader>
                        <v-text-field
                          single-line
                          outlined
                          label="Johny Relative"
                          hide-details
                        />
                      </v-col>

                      <v-col cols="6">
                        <v-subheader class="grey--text text--lighten-1 pl-0 subheader">
                          CARD NUMBER
                        </v-subheader>
                        <v-text-field
                          v-model="valueOfCardNumber"
                          single-line
                          outlined
                          mask="credit-card"
                          hide-details
                        />
                      </v-col>

                      <v-col col="4">
                        <v-subheader class="grey--text text--lighten-1 pl-0 subheader">
                          EXPIRY DATE
                        </v-subheader>
                        <v-select
                          :items="MonthList"
                          label="Month"
                          outlined
                          hide-details
                        />
                      </v-col>

                      <v-col col="4">
                        <v-subheader
                          class="grey--text text--lighten-1 pl-0 subheader"
                        />
                        <v-select
                          :items="YearList"
                          label="Year"
                          outlined
                          hide-details
                        />
                      </v-col>

                      <v-col col="4">
                        <v-subheader class="grey--text text--lighten-1 pl-0 subheader">
                          CVV
                        </v-subheader>
                        <v-text-field single-line outlined hide-details />
                      </v-col>
                    </v-row>
                  </v-card-text>
                  <p class="pb-5 pl-5">
                    <v-icon color="blue">
                      mdi-shield-lock
                    </v-icon> We Protect your payment information using encryption
                  </p>
                </v-card>
              </v-card>
            </v-col>
            <v-col md="4" class="ml-md-auto">
              <v-card class="pa-2" outlined rounded tile>
                <p><b>Billing Summary</b></p>
                <v-row style="height:40px">
                  <v-col cols="6" class="pl-5">
                    <p>Subtotal</p>
                  </v-col>
                  <v-col cols="6" class="text-right pr-5">
                    <p>$3000</p>
                  </v-col>
                </v-row>
                <v-row style="height:40px">
                  <v-col cols="6" class="pl-5">
                    <p>Discount</p>
                  </v-col>
                  <v-col cols="6" class="text-right pr-5">
                    <p>-$100</p>
                  </v-col>
                </v-row>
                <v-row style="height:40px">
                  <v-col cols="6" class="pl-5">
                    <p class="ma-0 pa-0">
                      Warranty
                    </p>
                    <p style="font-size:12px" class="blue--text ma-0">
                      remove
                    </p>
                  </v-col>
                  <v-col cols="6" class="text-right pr-5">
                    <p>-$100</p>
                  </v-col>
                </v-row>
                <v-row style="height:40px">
                  <v-col cols="6" class="pl-5">
                    <p>Shipping</p>
                  </v-col>
                  <v-col cols="6" class="text-right pr-5">
                    <p>$0</p>
                  </v-col>
                </v-row>
                <v-row style="height:40px">
                  <v-col cols="6" class="pl-5">
                    <p>Tax</p>
                  </v-col>
                  <v-col cols="6" class="text-right pr-5">
                    <p>-$100</p>
                  </v-col>
                </v-row>
                <p />
                <hr>
                <p />
                <v-row style="height:40px">
                  <v-col cols="6" class="pl-5">
                    <p><b>Grand Total </b></p>
                  </v-col>
                  <v-col cols="6" class="text-right pr-5">
                    <p>$2700</p>
                  </v-col>
                </v-row>
                <v-row style="height:80px">
                  <v-col cols="12">
                    <v-text-field
                      v-model="comment"
                      label="Order Comment"
                      :rules="fieldRules"
                      outlined
                    />
                  </v-col>
                </v-row>
                <v-checkbox
                  v-model="checkbox"
                  label="Please check to acknowledge our privacy"
                />
                <div class="text-center">
                  <v-btn
                    color="primary"
                    max-width="1000"
                    large
                    @click="onBuy"
                  >
                    Pay $2700.00
                  </v-btn>
                </div>
              </v-card>
            </v-col>
          </v-row>
        </v-form>
      </v-container>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'InspirePage',
  transition: 'home',
  data () {
    return {
      first: 'John',
      last: 'Doe',
      email: 'wise123@wise.com',
      address: ' ',
      state: '',
      city: '',
      pin: '123456',
      phone: '+1234567890',
      checkbox: true,
      account: false,
      comment: '',
      paypal: '',
      cardnumbe: '1234 1234 1234 1234',
      fieldRules: [v => !!v || 'This field is required'],
      emailRules: [
        v => !!v || 'E-mail is required',
        v =>
          /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) ||
          'E- mail must be valid'
      ],
      // var mailformat = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
      phoneNumberRules: [
        value => !!value || 'Please enter 10 digits.',
        value =>
          Number.isInteger(Number(value)) || 'The value must be an integer',
        // eslint-disable-next-line eqeqeq
        value => (value && value.length == 10) || 'must be 10 digits'
      ],
      pinRules: [
        value => !!value || 'Please enter 6 digits',
        value =>
          Number.isInteger(Number(value)) || 'The value must be an integer',
        // eslint-disable-next-line eqeqeq
        value => (value && value.length == 6) || 'must be 6 digits'
      ],
      states: ['AP', 'TG', 'GOA'],
      items: [
        {
          color: 'black',
          src: '/2-shoe.png',
          title: 'Supermodel text sample',
          artist: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam aliquet tellus lectus, quis egestas turpis ornare sit amet. Nulla vel vestibulum ipsum, at pharetra orci. Suspendisse lectus risus, molestie ac elit vel, rhoncus laoreet neque.'
        }],
      URL_IMAGE: 'https://i.imgur.com/lY1wk82.pn',
      YearList: ['2030', '2029', '2028', '2017', 'whatever'],
      MonthList: [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'Jully',
        'August',
        'September',
        'October',
        'November',
        'December'
      ],
      valueOfCardNumber: '4478 6322 9923 8990'
    }
  },
  methods: {
    onBuy () {
      if (this.$refs.form.validate()) {
      // eslint-disable-next-line no-console
        console.log('Product Buy')
      }
    }
  }
}
</script>
<style>
  .home-enter-active, .home-leave-active { transition: opacity .5s; }
  .home-enter, .home-leave-active { opacity: 0; }
</style>
