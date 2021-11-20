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
           <div class="text-h3">Todo</div>
           <div class="text_sutbitle1">{{ todaysDate }}</div>
         </div>
         <q-img 
         src="../statics/sea.jpg"
         class="header-image absolute-top"/>
    </q-header>

      <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 185px); margin-top: 185px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item to="/" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>
              <q-item-section>
                Todo
              </q-item-section>
            </q-item>

             <q-item to="/help" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>
              <q-item-section>
                Help
              </q-item-section>
            </q-item>
            
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="../statics/sea.jpg" style="height: 185px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://scontent-frt3-1.xx.fbcdn.net/v/t1.6435-9/100713259_3873325919406105_6290945495892230144_n.jpg?_nc_cat=107&ccb=1-5&_nc_sid=09cbfe&_nc_ohc=ZDqMGc7AO98AX_R8rPe&_nc_ht=scontent-frt3-1.xx&oh=71ac9ce2e419909f1442b0516238a1e6&oe=61B693C5">
            </q-avatar>
            <div class="text-weight-bold">Grzegorz Staniewicz</div>
            <div>@g_staniewicz</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

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
];

import { defineComponent, ref } from 'vue'
import { date } from 'quasar'

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
  computed: {
    todaysDate(){
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd D MMMM')
    }
  }
})
</script>


<style lang="scss">
  .header-image{
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%)
  }
  </style>
