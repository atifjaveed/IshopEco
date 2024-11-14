<template>
  <q-page padding>
    <!-- content -->
    <Compofdialog :array="fitlers" @data_emit="handeldata"/>
    <div class="row justify-center">
      <Compofishop :message="fitlers"/>
      <div class="col-8 q-px-lg">
        <div class="shadow-2 q-mt-md" v-for="item in array" :key="item">
          <div class="row">
            <div class="col-3 q-pa-sm">
              <q-img width="200px" src="logo.png"/>
            </div>
            <div class="col-3">
              <div class="text-h4 text-weight-bold q-pt-lg">
                We Sell Resale
                <div>
                  price: {{ item.price }}
                </div>
                <div>
                <span class="text-h5 text-weight-bold"> Ships from : {{ item.ships }}</span>
              </div>
            </div>
            </div>
            <div class="col-3">
              <div class="q-pt-md">
                <span class="text-h5 text-weight-bold">Business Values : </span>{{ item.Values }}

              </div>
              <div>
                <span class="text-h5 text-weight-bold"> Ownership : </span>{{ item.ownership }}
              </div>
              <div>
                <span class="text-h5 text-weight-bold"> Eco Commitment : </span>{{ item.commitment }}
              </div>
              <div>
                <span class="text-h5 text-weight-bold"> Business Size : </span>{{ item.size }}
              </div>
            </div>
            <div class="col-3 text-right">
              <div>
               {{ item.rating }}
              </div>
              <div>
                0 Sustainability Reviews
              </div>
              <div>
                {{ item.location }}
              </div>
              <div>
                <span class="text-h5 text-weight-bold"> Made in : </span>{{ item.made }}
              </div>
              <q-btn
              label="view map"
              color="orange"
              />
            </div>
          </div>
      </div>
    </div>
    </div>
    {{ selcted_filters }}
  </q-page>
</template>

<script>

import { LocalStorage } from 'quasar';
import Compofdialog from 'src/components/compofdialog.vue';
import Compofishop from 'src/components/compofishop.vue';


export default {
  components: { Compofishop, Compofdialog },
    data() {
        return {
            array:LocalStorage.getItem('array')?? [],
            fitlers: [
                {
                    label: 'price',
                    option:[
                      {label:'$',model: false, field:'price'},
                      {label:'$$',model:false, field:'price'},
                      {label:'$$$',model:false, field:'price'},
                      {label:'$$$$',model:false, field:'price'}
                    ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'location',
                    option:[
                      {label:'Online',model:false,field:'location'},
                      {label:'Local Retailers',model:false, field:'location'}
                    ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'customer rating',
                    option:[
                      {label:'5',model:false,field:'rating'},
                      {label:'4',model:false,field:'rating'},
                      {label:'3',model:false,field:'rating'},
                      {label:'2',model:false,field:'rating'},
                      {label:'1',model:false,field:'rating'}
                    ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'Business Values',
                    option:[
                      {label:'B-Corp Certified',model:false, field:'Values'},
                      {label:'Chemical Checked',model:false, field:'Values'},
                      {label:'Energy Efficient',model:false, field:'Values'},
                      {label:'Fair Trade',model:false, field:'Values'},
                      {label:'Source Traceable',model:false, field:'Values'},
                      {label:'Social Activism',model:false, field:'Values'},
                      {label:'Climate Activism',model:false, field:'Values'}
                    ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'Ownership',
                    option:[
                    {label:'Asian owned',model:false,field:'ownership'},
                    {label:'Black owned',model:false, field:'ownership'},
                    {label:'Disabled ownedt',model:false, field:'ownership'},
                    {label:'Hispanic Latinx owned',model:false, field:'ownership'},
                    {label:'Indigenous owned',model:false,field:'ownership'},
                    {label:'LGBTQ+ owned',model:false, field:'ownership'},
                    {label:'Veteran owned',model:false, field:'ownership'},
                    {label:'Woman owned',model:false, field:'ownership'}
                  ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'Eco Commitment',
                    option:[
                    {label:'Circular Program',model:false, field:'commitment'},
                    {label:'Organic Materials',model:false,field:'commitment'},
                    {label:'Plastic-Free Product',model:false,field:'commitment'},
                    {label:'Plastic-Free Shipping',model:false,field:'commitment'},
                    {label:'Vegan Materials',model:false,field:'commitment'},
                    {label:'100% Eco-Marketplace',model:false,field:'commitment'},
                    {label:'Partial Eco-Marketplace',model:false,field:'commitment'}
                  ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'Made In',
                    option:[
                    {label:'Canada',model:false,field:'made'},
                    {label:'Caribbean (non-USA)',model:false,field:'made'},
                    {label:'Central America',model:false,field:'made'},
                    {label:'Mexico',model:false, field:'made'},
                    {label:'USA',model:false,field:'made',option:[
                      {
                        label:'new york',model:false
                      },
                      {
                        label:'new york',model:false
                      }
                    ]}
                  ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'Ships From',
                    option:[
                    {label:'Canada',model:false, field:'ships'},
                    {label:'Central America',model:false,field:'ships'},
                    {label:'Mexico',model:false,field:'ships'},
                    {label:'USA',model:false,field:'ships',option:[
                    {
                        label:'new york',model:false
                      },
                      {
                        label:'new york',model:false
                      }
                    ]}
                  ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                },
                {
                    label: 'Business Size',
                    option:[
                    {label:'Small Business',model:false,field:'size'},
                    {label:'Large Business',model:false,field:'size'}
                  ],
                    class: 'fit row wrap justify-start items-start content-start',
                    model:''
                }

            ]
        };
    },
    computed:{
    selcted_filters() {
      return this.getSelectedFilters(this.fitlers)
    }
  },
  watch:{
    selcted_filters(){
      this.filterData();
    }
  },
  methods:{
    getSelectedFilters(message){
      let result=[];
      message.forEach(item =>{
        let selected= item?.option?.filter(item=>item.model);
        if(selected?.length){
          result.push(...selected);
        }
        let nestedFilters=item?.option?.filter(item=> item?.option?.length);
        if(nestedFilters?.length){
          result.push(...this.getSelectedFilters(item.option));
        }
      });
      return result;
    },
    filterData (){
      this.array = LocalStorage.getItem('array') ?? [];
      if(!this.selcted_filters?.length){
        this.array = LocalStorage.getItem('array') ?? [];
      }else{
        let prices =this.getSelectedFiltersByField('price');
        let locations=this.getSelectedFiltersByField('location');
        let rating = this.getSelectedFiltersByField('rating');
        let values = this.getSelectedFiltersByField('Values');
        let Ownership =this.getSelectedFiltersByField('ownership');
        let Commitment =this.getSelectedFiltersByField('commitment');
        let MadeIn =this.getSelectedFiltersByField('made');
        let ships=this.getSelectedFiltersByField('ships')
        let Size = this.getSelectedFiltersByField('size');

        if(prices.length){
          this.array = this.array.filter(item => prices.includes(item.price));
        }
        if(locations.length){
          this.array = this.array.filter(item => locations.includes(item.location));
        }
        if(rating.length){
          this.array = this.array.filter(item => rating.includes(item.rating));
        }
        if(values.length){
          this.array = this.array.filter(item => values.includes(item.Values));
        }
        if(Ownership.length){
          this.array = this.array.filter(item => Ownership.includes(item.ownership));
        }
        if(Commitment.length){
          this.array = this.array.filter(item => Commitment.includes(item.commitment));
        }
        if(MadeIn.length){
          this.array = this.array.filter(item => MadeIn.includes(item.made));
        }
        if(ships.length){
          this.array = this.array.filter(item => ships.includes(item.ships));
        }
        if(Size.length){
          this.array = this.array.filter(item => Size.includes(item.size));
        }
      }
    },
    getSelectedFiltersByField(field){
      let filternames=[];
      this.selcted_filters.forEach(item=>{
        if(item.field== field){
          filternames.push(item.label);
        }
      })
      return filternames ?? [];
    },
    handeldata(data){
        this.array=data
        LocalStorage.set('array', this.array)
        console.log(this.array)
      },
  }

}
</script>
