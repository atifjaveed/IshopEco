<template>
  <!-- <q-btn @click="senddatatoparent">send data to parent </q-btn> -->
  <div class="q-pa-md">
    <q-btn
    label="Add Data"
    color="primary"
    @click="dialog = true"
    />
    <q-dialog v-model="dialog">
      <q-card style="width: 600px;">
        <q-card-section>
          <q-select
            v-for="item in array"
            :key="item"
            class="q-mt-sm"
            outlined
            behavior="menu"
            :label="item.label"
            v-model="item.model"
            :options="item.option"
            option-label="label"
            option-value="label"
            emit-value
            map-options
          />
        </q-card-section>
        <q-card-section class="row items-center q-gutter-sm">
          <q-btn
          v-close-popup
          label="Close"
          color="red-14"
          />
          <q-btn
          @click="addRecord"
          label="+add"
          color="primary"
          />
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import { LocalStorage } from 'quasar';
import { ref } from 'vue';
export default {
  props:['array'],
  // name: 'ComponentName',
  data () {
    return {
      dialog: ref(false),
      iShopArray: LocalStorage.getItem('array') ?? []
    }
  },
  methods: {
    addRecord() {
      let obj = {
        price : this.array[0].model,
        location: this.array[1].model,
        rating : this.array[2].model,
        Values  : this.array[3].model,
        ownership  : this.array[4].model,
        commitment   : this.array[5].model,
        made : this.array[6].model,
        ships : this.array[7].model,
        size   : this.array[8].model,
      }
      this.array[0].model=''
      this.array[1].model=''
      this.array[2].model=''
      this.array[3].model=''
      this.array[4].model=''
      this.array[5].model=''
      this.array[6].model=''
      this.array[7].model=''
      this.array[8].model=''
      this.iShopArray.push(obj)
      this.dialog= false
      // console.log(this.iShopArray)
      this.$emit('data_emit', this.iShopArray)

    },
    // senddatatoparent(){
    // }
  },

}
</script>
