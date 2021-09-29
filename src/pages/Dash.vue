<template>
  <q-layout>
    <div>
      <div class="row justify-between">
        <div class="col2">
          <div class="text-h5 q-mb-xs">Overview</div>
        </div>
        <div class="col2">
          <q-btn icon-right="add_circle" style="background: #6763E3; color: white" label="Add Funds" />
        </div>
      </div>
      <div>
        <div class="row">
          <div class="col-12 col-md">
            <q-card class="my-card">
              <img src="../assets/graph.jpg">
            </q-card>
          </div>
          <div class="col-12 col-md">
            <q-card class="my-card">
              <img src="../assets/pie.jpg">
            </q-card>
          </div>
          <div class="col-12 col-md">
            <q-card class="my-card" bordered>
              <q-card-section avatar align="center">
                <q-avatar size="96px">
                  <img src="../assets/profile-pic-01.jpg">
                </q-avatar>
              </q-card-section>
              <q-card-section align="center">
                <q-item-label>Nick Heraseimenka</q-item-label>
                <q-item-label caption>United States</q-item-label>
              </q-card-section>
              <q-separator />
              <q-list>
                <q-item clickable>
                  <q-item-section avatar>
                    <q-avatar>
                      <img src="../assets/profile-pic-02.jpg" />
                    </q-avatar>
                  </q-item-section>

                  <q-item-section>
                    <q-item-label>Drew James</q-item-label>
                    <q-item-label caption>United States</q-item-label>
                    <q-space />
                    <q-item-label caption>Mobile: 9876543210</q-item-label>
                  </q-item-section>
                </q-item>

                <q-item clickable>
                  <q-item-section avatar>
                    <q-avatar>
                      <img src="../assets/profile-pic-03.jpg" />
                    </q-avatar>
                  </q-item-section>

                  <q-item-section>
                    <q-item-label>Bavid Kames</q-item-label>
                    <q-item-label caption>United States</q-item-label>
                    <q-space />
                    <q-item-label caption>Mobile: 9876543210</q-item-label>
                  </q-item-section>
                </q-item>

                <q-item clickable>
                  <q-item-section avatar>
                    <q-avatar>
                      <img src="../assets/profile-pic-04.jpg" />
                    </q-avatar>
                  </q-item-section>

                  <q-item-section>
                    <q-item-label>Lavid Emes</q-item-label>
                    <q-item-label caption>United States</q-item-label>
                    <q-space />
                    <q-item-label caption>Mobile: 9876543210</q-item-label>
                  </q-item-section>
                </q-item>
              </q-list>
            </q-card>
          </div>
        </div>
        <div class="row">
          <div class="my-table col-12 col-md-8">
            <q-table
              class="my-sticky-virtscroll-table"
              virtual-scroll
              v-model:pagination="pagination"
              :rows-per-page-options="[0]"
              :virtual-scroll-sticky-size-start="48"
              row-key="index"
              title="Referer"
              :rows="rows"
              :columns="columns"
            />
          </div>
          <div class="col-12 col-md-4">
            <q-card>
              <q-card-section>
                <div class="row items-center no-wrap">
                  <div class="col">
                    <label>Product Video</label>
                  </div>
                  <div class="">
                    <q-btn flat dense rounded icon="more_vert" />
                  </div>
                </div>
                <div class="">
                  <q-img src="../assets/videothumbnail.png" />
                </div>
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
    </div>
  </q-layout>
</template>

<script>
import { ref } from 'vue'

const columns = [
  {
    name: 'index',
    label: '#',
    field: 'index'
  },
  {
    name: 'name',
    required: true,
    label: 'Dessert (100g serving)',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'calories', align: 'center', label: 'Calories', field: 'calories', sortable: true },
  { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
  { name: 'carbs', label: 'Carbs (g)', field: 'carbs' },
  { name: 'protein', label: 'Protein (g)', field: 'protein' },
  { name: 'sodium', label: 'Sodium (mg)', field: 'sodium' },
  { name: 'calcium', label: 'Calcium (%)', field: 'calcium', sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10) },
  { name: 'iron', label: 'Iron (%)', field: 'iron', sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10) }
]

const seed = [
  {
    name: 'Frozen Yogurt',
    calories: 159,
    fat: 6.0,
    carbs: 24,
    protein: 4.0,
    sodium: 87,
    calcium: '14%',
    iron: '1%'
  },
  {
    name: 'Ice cream sandwich',
    calories: 237,
    fat: 9.0,
    carbs: 37,
    protein: 4.3,
    sodium: 129,
    calcium: '8%',
    iron: '1%'
  },
  {
    name: 'Eclair',
    calories: 262,
    fat: 16.0,
    carbs: 23,
    protein: 6.0,
    sodium: 337,
    calcium: '6%',
    iron: '7%'
  },
  {
    name: 'Cupcake',
    calories: 305,
    fat: 3.7,
    carbs: 67,
    protein: 4.3,
    sodium: 413,
    calcium: '3%',
    iron: '8%'
  },
  {
    name: 'Gingerbread',
    calories: 356,
    fat: 16.0,
    carbs: 49,
    protein: 3.9,
    sodium: 327,
    calcium: '7%',
    iron: '16%'
  },
  {
    name: 'Jelly bean',
    calories: 375,
    fat: 0.0,
    carbs: 94,
    protein: 0.0,
    sodium: 50,
    calcium: '0%',
    iron: '0%'
  },
  {
    name: 'Lollipop',
    calories: 392,
    fat: 0.2,
    carbs: 98,
    protein: 0,
    sodium: 38,
    calcium: '0%',
    iron: '2%'
  },
  {
    name: 'Honeycomb',
    calories: 408,
    fat: 3.2,
    carbs: 87,
    protein: 6.5,
    sodium: 562,
    calcium: '0%',
    iron: '45%'
  },
  {
    name: 'Donut',
    calories: 452,
    fat: 25.0,
    carbs: 51,
    protein: 4.9,
    sodium: 326,
    calcium: '2%',
    iron: '22%'
  },
  {
    name: 'KitKat',
    calories: 518,
    fat: 26.0,
    carbs: 65,
    protein: 7,
    sodium: 54,
    calcium: '12%',
    iron: '6%'
  }
]

// we generate lots of rows here
let rows = []
for (let i = 0; i < 1000; i++) {
  rows = rows.concat(seed.slice(0).map(r => ({ ...r })))
}
rows.forEach((row, index) => {
  row.index = index
})

export default {
  setup () {
    return {
      columns,
      rows,

      pagination: ref({
        rowsPerPage: 0
      })
    }
  }
}
</script>

<style lang="sass" scoped>
.row > div
  padding: 10px 15px

  label
    color: blue-grey
    letter-spacing: .01785714em
    font-size: .875rem
    font-weight: 500
    line-height: 1.25rem

  q-item-label
    color: blue-grey
    letter-spacing: .01785714em
    font-size: .875rem
    font-weight: 500
    line-height: 1.25rem

.my-sticky-virtscroll-table
  /* height or max-height is important */
  height: 410px

  .q-table__top,
  .q-table__bottom,
  thead tr:first-child th /* bg color is important for th; just specify one */
    background-color: #fff

  thead tr th
    position: sticky
    z-index: 1
  /* this will be the loading indicator */
  thead tr:last-child th
    /* height of all previous header rows */
    top: 48px
  thead tr:first-child th
    top: 0

.my-table
  position: relative
</style>
