<template>
  <q-layout view="lHh lpR fFf" class="GPL__layout bg-grey-1">
    <q-header elevated class="bg-white text-grey-8" height-hint="64">
      <q-toolbar class="GPL__toolbar" style="height: 54px">
        <q-btn
          flat
          dense
          round
          @click="toggleLeftDrawer"
          aria-label="Menu"
          icon="menu"
          class="q-mx-md"
        />

        <q-input class="GPL__toolbar-input" dense borderless v-model="search" placeholder="Search Transactions, items or help">
          <template v-slot:prepend>
            <q-icon v-if="search === ''" name="search" />
            <q-icon v-else name="clear" class="cursor-pointer" @click="search = ''" />
          </template>
        </q-input>

        <q-space />


        <q-space />

        <div class="q-pd-md row items-center no-wrap">
          <q-btn round dense flat color="grey-8" icon="notifications">
            <q-badge color="green" floating>
            </q-badge>
            <q-menu :offset="[350, 10]">
              <q-list style="min-width: 400px">
                <q-item clickable>
                  <q-item-section avatar>
                    <q-avatar>
                      <img src="../assets/profile-pic-02.jpg" />
                    </q-avatar>
                  </q-item-section>

                  <q-item-section>
                    <q-item-label align="right" caption>1 min</q-item-label>
                    <q-item-label>Drew James</q-item-label>
                    <q-item-label caption>Start working on it</q-item-label>
                  </q-item-section>
                </q-item>

                <q-item clickable>
                  <q-item-section avatar>
                    <q-avatar>
                      <img src="../assets/profile-pic-05.jpg" />
                    </q-avatar>
                  </q-item-section>

                  <q-item-section>
                    <q-item-label align="right" caption>1 min</q-item-label>
                    <q-item-label>Alexa Mary</q-item-label>
                    <q-item-label caption>Come over</q-item-label>
                  </q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section avatar>
                    <q-avatar>
                      <img src="../assets/profile-pic-06.jpg" />
                    </q-avatar>
                  </q-item-section>

                  <q-item-section>
                    <q-item-label align="right" caption>1 min</q-item-label>
                    <q-item-label>Eva Maria</q-item-label>
                    <q-item-label caption>Dont miss this, My boy</q-item-label>
                  </q-item-section>
                </q-item>
              </q-list>
            </q-menu>
            <q-tooltip>Notifications</q-tooltip>
          </q-btn>
          <q-btn v-if="$q.screen.gt.xs" flat dense no-wrap label="John Doe" color="primary" icon-right="expand_more" no-caps class="">
            <q-menu :offset="[50, 10]">
              <q-list class="text-grey-8" style="min-width: 100px">
                <q-item v-for="menu in createMenu" :key="menu.text" clickable v-close-popup aria-hidden="true">
                  <q-item-section avatar>
                    <q-icon :name="menu.icon" />
                  </q-item-section>
                  <q-item-section>{{ menu.text }}</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
          <q-btn rounded flat dense>
            <q-avatar size="26px">
              <img src="../assets/profile-pic-01.jpg">
            </q-avatar>
            <q-tooltip>Account</q-tooltip>
          </q-btn>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      class="bg-blue-grey-9"
      :width="240"
      v-model="leftDrawerOpen"
      bordered
    >
      <q-scroll-area class="fit">
        <q-toolbar class="bg-blue-grey-10 GPL__toolbar">
          <q-toolbar-title class="row items-center text-grey-1">
            A C M E
          </q-toolbar-title>
        </q-toolbar>

        <q-list padding>
          <q-item v-for="link in links1" :key="link.text" :to="link.to" clickable class="GPL__drawer-item">
            <q-item-section avatar>
              <q-icon :name="link.icon" />
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ link.text }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'GooglePhotosLayout',
  setup () {
    const leftDrawerOpen = ref(false)
    const search = ref('')
    const storage = ref(0.26)
    function toggleLeftDrawer () {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }
    return {
      leftDrawerOpen,
      search,
      storage,
      links1: [
        { icon: 'home', text: 'Home' },
        { icon: 'assessment', text: 'Dashboard', to: '/dash' },
        { icon: 'mail', text: 'Inbox' },
        { icon: 'list_alt', text: 'Products' },
        { icon: 'settings', text: 'Admin' }
      ],
      createMenu: [
        { icon: 'person_outline', text: 'My Profile' },
        { icon: 'receipt', text: 'Billing' },
        { icon: 'logout', text: 'Logout' }
      ],
      toggleLeftDrawer
    }
  }
}
</script>

<style lang="sass">
.GPL
  &__toolbar
    height: 54px
  &__toolbar-input
    width: 35%
  &__drawer-item
    line-height: 24px
    margin-right: 12px
    .q-item__section--avatar
      padding-left: 12px
      .q-icon
        color: #S14DDC
    .q-item__label:not(.q-item__label--caption)
      color: white
      letter-spacing: .01785714em
      font-size: .875rem
      font-weight: 500
      line-height: 1.25rem
    &--storage
      border-radius: 0
      margin-right: 0
      padding-top: 24px
      padding-bottom: 24px
  &__side-btn
    &__label
      font-size: 12px
      line-height: 24px
      letter-spacing: .01785714em
      font-weight: 500
  @media (min-width: 1024px)
    &__page-container
      padding-left: 94px
</style>
