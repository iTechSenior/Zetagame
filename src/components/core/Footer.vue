<template>
  <v-footer id="core-footer" color="black">
    <div
      style="justify-content: center; padding: 20px 100px 0 100px; width: 100%;"
    >
      <div
        v-for="(logo, i) in logos"
        :key="i"
        style="width:118px; margin-left:20px; margin-right:20px; margin-bottom: 10px; display:inline-block;"
      >
        <img
          :src="logo.logo"
          style="max-height:50px; vertical-align: middle;"
          width="100%"
        />
      </div>
    </div>

    <!-- <div
      style="justify-content: space-between; padding: 0px 100px; display: flex;"
    >
      <material-logo :logourl="logo" />

      <div
        style="justify-content: center; padding: 0px 100px; display: flex; width: 40%"
      >
        <div
          v-for="(link, i) in links"
          :key="i"
          style="width:100px; display:inline-block;"
        >
          <img :src="link.logo" height="100" />
        </div>
      </div>

      <span class="bottom-text">{{ text }}</span>
    </div>-->

    <v-layout class="pl-5 pr-5">
      <v-flex xs12 lg4>
        <material-logo :logourl="logo" />
      </v-flex>
      <v-flex xs12 lg4>
        <v-layout justify-center>
          <div
            v-for="(link, i) in links"
            :key="i"
            style="width:100px; display:inline-block;"
          >
            <img :src="link.logo" height="100" class="link-icon" />
          </div>
        </v-layout>
      </v-flex>
      <v-flex xs12 lg4>
        <span class="bottom-text">{{ text }}</span>
      </v-flex>
    </v-layout>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    logo: 'img/logo.png',
    logos: [
      { name: 'evolution', logo: '/img/logos/providers/evolution.png' },
      { name: 'netent', logo: '/img/logos/providers/netent.png' },
      { name: 'kalamba', logo: '/img/logos/providers/kalamba.png' },
      { name: 'ezugi', logo: '/img/logos/providers/ezugi.png' },
      { name: 'havanero', logo: '/img/logos/providers/havanero.png' },
      { name: 'evoplay', logo: '/img/logos/providers/evoplay.png' },
      { name: 'pariplay', logo: '/img/logos/providers/pariplay.png' },
      { name: 'luckystreak', logo: '/img/logos/providers/luckystreak.png' },
      { name: 'onetouch', logo: '/img/logos/providers/onetouch.png' },
      { name: 'tomhorn', logo: '/img/logos/providers/tomhorn.png' },
      { name: 'ganapati', logo: '/img/logos/providers/ganapati.png' },
      { name: 'quickspin', logo: '/img/logos/providers/quickspin.png' },
      { name: 'endorphina', logo: '/img/logos/providers/endorphina.png' },
      { name: 'betsoft', logo: '/img/logos/providers/betsoft.png' },
      { name: 'gamomat', logo: '/img/logos/providers/gamomat.png' },
      { name: 'gameart', logo: '/img/logos/providers/gameart.png' },
      { name: 'fugaso', logo: '/img/logos/providers/fugaso.png' },
      { name: 'playngo', logo: '/img/logos/providers/playngo.png' },
      { name: 'elk', logo: '/img/logos/providers/elk.png' },
      { name: 'slotmotion', logo: '/img/logos/providers/slotmotion.png' }
    ],
    links: [
      { name: 'twitter', logo: '/img/logos/social/twitter.png' },
      { name: 'facebook', logo: '/img/logos/social/facebook.png' },
      { name: 'whatsapp', logo: '/img/logos/social/whatsapp.png' },
      { name: 'instagram', logo: '/img/logos/social/instagram.png' }
    ],
    text: 'Lorem ipsum dolares bardakum nasturan my logesnas'
  })
}
</script>

<style>
.v-footer {
  display: block !important;
  height: unset !important;
}
#core-footer .logo {
  bottom: unset;
  left: unset;
  position: unset;
  margin-top: 1rem;
  float: left;
  /* width: 30%; */
}
#core-footer .bottom-text {
  margin-top: 3rem;
  width: 100%;
  text-align: right;
  float: right;
}
.link-icon {
  cursor: pointer;
}
</style>
