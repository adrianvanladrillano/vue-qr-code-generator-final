<template>
  <div>
    <v-container>
      <!-- QR Selection -->
      <v-row class="text-center">
        <v-col>
          <h1
            class="display-2 white--text font-weight-black"
          >What type of QR Codes can I create for free?</h1>
          <p class="font-weight-black text-h4 mt-2">Forever free. Even if the creator dies.</p>
          <p class="mt-2 white--text">
            We offer these Static QR Codes that are completely for free and will
            never expire. Once generated, it’s yours forever but you will not be
            able to edit the content or track its scans.
          </p>
        </v-col>
      </v-row>
      <div v-if="qr_mode != null">
        <v-container fill-height height="100vh" class="text-center">
          <v-row>
            <v-col>
              <v-card height="100%" class="px-5 py-5">
                <v-btn color="primary" @click="qr_mode = null" text>
                  <v-icon left>mdi-chevron-left</v-icon>Change QR Type
                </v-btn>

                <!-- vCard -->
                <div v-if="qr_mode == 'vCard'" class="text-center">
                  <h1 class="font-weight-medium">Calling Card Qr Code</h1>
                  <p class="body-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>

                  <v-row dense class="px-15">
                    <v-col>
                      <v-text-field dense outlined label="First name" v-model="v_firstname"></v-text-field>
                    </v-col>
                    <v-col>
                      <v-text-field dense outlined label="Last name" v-model="v_lastname"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-row dense class="px-15">
                    <v-col>
                      <v-text-field dense outlined label="Mobile" v-model="v_mobile"></v-text-field>
                    </v-col>
                    <v-col>
                      <v-text-field dense outlined label="Phone " v-model="v_phone"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-row dense class="px-15">
                    <v-col>
                      <v-text-field dense outlined label="Email " v-model="v_email"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-row dense class="px-15">
                    <v-col>
                      <v-text-field dense outlined label="Website" v-model="v_website"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-row dense class="px-15">
                    <v-col>
                      <v-text-field dense outlined label="Street" v-model="v_street"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-row dense class="px-15">
                    <v-col cols="8">
                      <v-text-field dense outlined label="City" v-model="v_city"></v-text-field>
                    </v-col>
                    <v-col>
                      <v-text-field dense outlined label="Zip/Postal Code" v-model="v_zip"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-row dense class="px-15">
                    <v-col cols="6">
                      <v-text-field dense outlined label="Region" v-model="v_region"></v-text-field>
                    </v-col>
                    <v-col>
                      <v-text-field dense outlined label="Province" v-model="v_province"></v-text-field>
                    </v-col>
                  </v-row>

                  <p>
                    <strong>
                      TIP: Enter whatever you want. you can put url inside it as
                      well.
                    </strong>
                    <br />Example use cases: Messages, Event Invite and etc.
                  </p>
                </div>

                <!-- URL -->
                <div v-if="qr_mode == 'URL'" class="px-15">
                  <h1 class="font-weight-medium">URL Qr Code</h1>
                  <p class="body-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
                  <v-textarea
                    height="100%"
                    class="custom-label-color"
                    flat
                    solo
                    placeholder="Enter url here."
                    v-model="qr_url"
                  ></v-textarea>
                  <p>
                    <strong>How to use it with facebook, twitter, instagram?</strong>
                    <br />- Go to your profile in a browser and copy the link.
                    <br />Example:
                    <a
                      href="https://www.facebook.com/zuck"
                      style="text-decoration: none"
                    >https://www.facebook.com/zuck</a>
                  </p>

                  <p>
                    <strong>
                      How to use it to promote your App Store/Playstore
                      application?
                    </strong>
                    <br />- Search your application in a browser and copy the link.
                    <br />Example:
                    <a
                      href="https://play.google.com/store/apps/details?id=com.facebook.katana&hl=en&gl=US"
                      style="text-decoration: none"
                    >https://play.google.com/store/apps/details?id=com.facebook.katana&hl=en&gl=US</a>
                  </p>
                </div>

                <!-- TEXT -->
                <div v-if="qr_mode == 'TEXT'" class="px-15">
                  <h1 class="font-weight-medium">Text Qr Code</h1>
                  <p class="body-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
                  <v-textarea
                    height="100%"
                    class="custom-label-color"
                    flat
                    solo
                    placeholder="Enter text here."
                    v-model="qr_text"
                  ></v-textarea>
                  <p>
                    <strong>
                      TIP: Enter whatever you want. you can put url inside it as
                      well.
                    </strong>
                    <br />Example use cases: Messages, Event Invite and etc.
                  </p>
                </div>

                <!-- SMS -->
                <div v-if="qr_mode == 'SMS'" class="px-15">
                  <h1 class="font-weight-medium">SMS Qr Code</h1>
                  <p class="body-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
                  <v-text-field label="Your number" outlined dense v-model="sms_number"></v-text-field>
                  <v-textarea label="Message" outlined dense v-model="sms_message"></v-textarea>

                  <p>
                    <strong>
                      TIP: Use this type to send a predefined text message to
                      any phone number.
                    </strong>
                    <br />Most users used this type for: Inquiries, recruitment and
                    many more.
                  </p>
                </div>

                <!-- EMAIL -->
                <div v-if="qr_mode == 'EMAIL'" class="px-15">
                  <h1 class="font-weight-medium">Email Qr Code</h1>
                  <p class="body-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
                  <v-text-field label="Your email" outlined dense v-model="email_address"></v-text-field>
                  <v-text-field label="Subject" outlined dense v-model="email_subject"></v-text-field>
                  <v-textarea label="Message" outlined dense v-model="email_message"></v-textarea>

                  <p>
                    <strong>
                      TIP: Use this type to send a predefined email to any email
                      address.
                    </strong>
                    <br />Example use cases: Inquiries, recruitment and etc.
                  </p>
                </div>

                <!-- WIFI -->
                <div v-if="qr_mode == 'WIFI'" class="px-15">
                  <h1 class="font-weight-medium">Wifi Qr Code</h1>
                  <p class="body-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
                  <v-text-field label="Network name" outlined dense v-model="wifi_name"></v-text-field>
                  <v-text-field label="Password" outlined dense v-model="wifi_password"></v-text-field>
                  <v-autocomplete
                    label="Encryption"
                    :items="wifi"
                    item-text="label"
                    item-value="value"
                    outlined
                    dense
                    v-model="wifi_enc"
                  ></v-autocomplete>
                </div>
              </v-card>
            </v-col>

            <v-col cols="4">
              <v-card class="px-5 py-5">
                <v-row>
                  <v-col class="px-10 py-5">
                    <qrcode-vue
                      :value="qr_value"
                      level="H"
                      :background="qr_bg"
                      :foreground="qr_fg"
                      size="300"
                    />
                  </v-col>
                </v-row>

                <v-row>
                  <v-col>
                    <v-text-field v-model="qr_bg" v-mask="mask" hide-details class="ma-0 pa-0" solo>
                      <template v-slot:append>
                        <v-menu
                          v-model="menu"
                          top
                          nudge-bottom="105"
                          nudge-left="16"
                          :close-on-content-click="false"
                        >
                          <template v-slot:activator="{ on }">
                            <div :style="swatchStyle" v-on="on" />
                          </template>
                          <v-card>
                            <v-card-text class="pa-0">
                              <v-color-picker v-model="qr_bg" flat />
                            </v-card-text>
                          </v-card>
                        </v-menu>
                      </template>
                    </v-text-field>
                  </v-col>
                </v-row>
                <v-row>
                  <v-col>
                    <v-text-field
                      v-model="qr_fg"
                      v-mask="mask2"
                      hide-details
                      class="ma-0 pa-0"
                      solo
                    >
                      <template v-slot:append>
                        <v-menu
                          v-model="menu2"
                          top
                          nudge-bottom="105"
                          nudge-left="16"
                          :close-on-content-click="false"
                        >
                          <template v-slot:activator="{ on }">
                            <div :style="swatchStyle2" v-on="on" />
                          </template>
                          <v-card>
                            <v-card-text class="pa-0">
                              <v-color-picker v-model="qr_fg" flat />
                            </v-card-text>
                          </v-card>
                        </v-menu>
                      </template>
                    </v-text-field>

                    <v-btn class="mt-5" block color="primary">Download QR</v-btn>
                  </v-col>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </div>

      <div v-if="qr_mode == null">
        <v-row>
          <v-col cols="4">
            <v-card @click="SelectQR('URL')">
              <v-card-title>Dynamic URL</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('TEXT')">
              <v-card-title>Plain Text</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('vCard')">
              <v-card-title>Calling Card</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('SMS')">
              <v-card-title>SMS</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('EMAIL')">
              <v-card-title>Email</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="4">
            <v-card @click="SelectQR('WIFI')">
              <v-card-title>Wifi</v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sed
                accusamus deleniti porro exercitationem in. Laborum nemo unde
                beatae libero, porro voluptates nihil inventore fugit cum
                corporis! Voluptatum eligendi sed sunt.
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </div>
    </v-container>
  </div>
</template>
<script>
import QrcodeVue from 'qrcode.vue'

export default {
  components: {
    QrcodeVue
  },
  data() {
    return {
      wifi: [
        { label: 'None', value: 'None' },
        { label: 'WPA/WPA2', value: 'WPA/WPA2' },
        { label: 'WEP', value: 'WEP' }
      ],
      // Colors
      qr_bg: '#FFFFFF',
      qr_fg: '#000000',

      //   types

      qr_url: '',
      qr_text: '',

      sms_number: '',
      sms_message: '',

      email_address: '',
      email_subject: '',
      email_message: '',

      wifi_name: '',
      wifi_password: '',
      wifi_enc: '',

      v_firstname: '',
      v_lastname: '',
      v_mobile: '',
      v_phone: '',
      v_email: '',
      v_website: '',
      v_street: '',
      v_city: '',
      v_zip: '',
      v_region: '',
      v_province: '',

      color: '#1976D2FF',
      mask: '!#000000',
      mask2: '!#FFFFFF',
      menu: false,
      menu2: false,

      // qr_mode: null,
      qr_mode: null,
      value: 'https://example.com'
    }
  },
  computed: {
    qr_value() {
      if (this.qr_mode == 'URL') {
        return this.qr_url
      }
      if (this.qr_mode == 'TEXT') {
        return this.qr_text
      }
      if (this.qr_mode == 'SMS') {
        return 'smsto:' + this.sms_number + '?body=' + this.sms_message
      }
      if (this.qr_mode == 'EMAIL') {
        return (
          'mailto:' +
          this.email_address +
          '?subject=' +
          this.email_subject +
          '&body=' +
          this.email_message
        )
      }
      if (this.qr_mode == 'WIFI') {
        return `WIFI:T:WPA;S:${this.wifi_name};P:${this.wifi_password};H:`
      }
      if (this.qr_mode == 'vCard') {
        return `BEGIN:VCARD VERSION:3.0 N:Stafford;Zena FN:Zena Stafford ORG:Lloyd and Franklin Inc TITLE:Adipisci impedit an ADR:;;#1F Petronia St㰨 Buenamar Subd;Iusto deleniti dolor;Odio iure aut culpa;21410;Lorem numquam do eli TEL;WORK;VOICE:+1 (298) 351-1504 TEL;CELL:09281597391 TEL;FAX:+1 (102) 302-7901 EMAIL;WORK;INTERNET:zena.stafford@gmail.com URL:https://www.hapaqiwuwoqa.info END:VCARD`
      }
    },
    swatchStyle() {
      return {
        backgroundColor: this.qr_bg,
        cursor: 'pointer',
        height: '30px',
        width: '30px',
        border: '1px solid #e1e1e1',
        borderRadius: this.menu ? '50%' : '4px',
        transition: 'border-radius 200ms ease-in-out'
      }
    },
    swatchStyle2() {
      return {
        backgroundColor: this.qr_fg,
        cursor: 'pointer',
        height: '30px',
        width: '30px',
        border: '1px solid #e1e1e1',
        borderRadius: this.menu2 ? '50%' : '4px',
        transition: 'border-radius 200ms ease-in-out'
      }
    }
  },
  methods: {
    SelectQR(type) {
      this.qr_mode = type
    }
  }
}
</script>
<style>
.custom-placeholer-color textarea,
.custom-label-color textarea {
  font-size: 2em;
  font-weight: 500;
  text-align: center;
}
</style>