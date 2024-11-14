<template>

    <div class="col-2">
      <div>
        <q-list bordered class="rounded-borders">
          <q-expansion-item
            v-for="item in message" :key="item"
            expand-separator
            :label="item.label"
            style="font-size: 20px;"
          >
            <div  v-for="x in item.option" :key="x">
              <q-expansion-item v-if="x?.option?.length">
                <template v-slot:header>
                  <div class="full-width">
                    <q-checkbox
                    :label="x.label"
                    v-model="x.model"

                    />
                  </div>
                </template>
                <q-card>
                  <q-card-section>
                    <q-input filled v-modle="text">
                    <template v-slot:append>
                      <q-icon name="search"/>
                    </template>
                    </q-input>
                    <div class="" v-for="c in x.option" :key="c">
                      <q-checkbox v-model="c.model" :label="c.label"/>
                    </div>
                  </q-card-section>
                </q-card>
              </q-expansion-item>
             <q-checkbox
                  v-else
                  :class=" item.class"
                  :label="x.label"
                  v-model="x.model"
                >
                <q-rating
                v-if="item.label == 'customer rating'"
                  v-model="x.label"
                  size="1.5em"
                  icon="star"
                />
              </q-checkbox>
            </div>
          </q-expansion-item>
        </q-list>
        {{ selcted_filters }}
      </div>
    </div>

</template>

<script>
import { LocalStorage } from 'quasar';


export default {
  // name: 'ComponentName',
props:['message'],
  data () {
    return {
      model:''

    }
  },

}
</script>
