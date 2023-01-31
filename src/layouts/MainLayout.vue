<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />


      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Tasks</div>
        <div class="text-subtitlel">{{ todaysDate }}</div>

        </div>


    </q-header>


<q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item
            to="/"
            clickable
            v-ripple>
              <q-item-section avatar>
                <q-icon name="List" />
              </q-item-section>

              <q-item-section>
                List
              </q-item-section>
            </q-item>

            <q-item
            to="/help"
            exact
             clickable
             v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                help
              </q-item-section>
            </q-item>


          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://4.bp.blogspot.com/-nh7t3e7yC1U/Vs3BJQKqv9I/AAAAAAAAAlk/FujpekavCk0/w1200-h630-p-k-no-nu/inspira%25C3%25A7%25C3%25A3o16.jpg" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="ip.jpg">
            </q-avatar>
            <div class="text-weight-bold" >Cindy Zacarias</div>
            <div>@Cindy_Zacarias</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <KeepAlive>
        <router-view />
      </KeepAlive>

    </q-page-container>
  </q-layout>
</template>

<script>

import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'
import { date } from 'quasar'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)


    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }



},
computed:{
      todaysDate(){
        const timeStamp = Date.now()
         return date.formatDate(timeStamp, 'dddd D MMMM')
      }
    }


})

</script>

<style>
div{
  color: black;

}
</style>
