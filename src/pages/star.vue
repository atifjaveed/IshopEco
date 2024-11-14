<template>
  <q-pag>
  <div>
    <select v-model="selectedRating">
      <option v-for="rating in ratings" :key="rating.value" :value="rating.value">
        {{ rating.label }} {{ generateStars(rating.value) }}
      </option>
    </select>
   <div class="row">
    <div class="col-6 q-pa-md">
      <q-input
        filled
        class="q-my-sm"
        label="name"
        v-model="form.name"
        type="text"
      />
      <q-input
        filled
        class="q-my-sm"
        label="email"
        v-model="form.email"
        type="email"
      />
      <q-input
        filled
        class="q-my-sm"
        label="password"
        v-model="form.password"
        type="password"
      />
      <q-btn
        class="q-my-sm"
        color="red-14"
        label="add"
        @click="add"
      />
      <q-input
        class="q-my-sm"
        filled
        label="search"
        v-model="inputValue"
      />
      <q-btn
      class="q-my-sm"
        label="search"
        color="grey"
        @click="filterlist"
      />
    </div>
    <div class="col-6">
      <q-card style="width: 500px;" class="q-mt-md" v-for="item in result" :key="item">
        <q-card-section>
          <div>
            name: {{ item.name }}
          </div>
          <div>
            email:{{ item.email }}
          </div>
          <div>
            password:{{ item.password }}
          </div>
        </q-card-section>
      </q-card>
    </div>
   </div>
  </div>

</q-pag>
</template>

<script>
export default {
  data() {
    return {
      inputValue:'',
      result:[],
      form:{
        name:'',
        email:'',
        password:''
      },
      selectedRating: null,
      ratings: [
        { label: "1 Star", value: 1 },
        { label: "2 Stars", value: 2 },
        { label: "3 Stars", value: 3 },
        { label: "4 Stars", value: 4 },
        { label: "5 Stars", value: 5 },
      ],
    };
  },
  methods: {
    generateStars(count) {
      return '⭐️'.repeat(count);
    },
    add(){
      let obj={
        name:this.form.name,
        email:this.form.email,
        password:this.form.password
      }
      this.result.push(obj)
      console.log(this.result)
    },
    filterlist(){
      let filterData= this.result.filter((item)=>{
       this.result=this.result.filter((item)=>item.name.includes(this.inputValue)||item.email.includes(this.inputValue)||item.password.includes(this.password))
      })
    }
  },
};
</script>
