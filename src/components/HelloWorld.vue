<script >
import axios from 'axios'
import { responseData } from '../data.js'

export default {
  data() {
    return {
      details: [],
      details1: [],
      details2: [],
      details3: [],
      details4: [],
      details5: [],
      CS_DATA_LIST: [],
      filterResults: [],
      SCHOLARSHIPS: [],
      newData: [],
      mode: ['Ver Todos'],
      shift: ['Ver Todos'],
      course: ['Ver Todos'],
      mode1: [],
      shift1: [],
      course1: [],
      units: [],

      status: Boolean = false,
    }
  },
  methods: {
    getData() {
      this.details = responseData.scholarships
      this.details1 = responseData.scholarships
      // this.details.map((data)=>{
      //   console.log(data)
      // })
      responseData.scholarships.map(async (t) => {
        if ((this.SCHOLARSHIPS.push(t), this.CS_DATA_LIST.length > 0)) {
          let e = this.CS_DATA_LIST.find((e) => e.course.name === t.course.name && e.school.name === t.school.name);
          if (null == e) {
            let e = { course: t.course, school: t.school, content_level: t.content_level, modalities: [], shifts: [], units: [], scholarships: [] };
            this.CS_DATA_LIST.push(e);
          }
        } else {
          let e = { course: t.course, school: t.school, content_level: t.content_level, modalities: [], shifts: [], units: [], scholarships: [] };
          this.CS_DATA_LIST.push(e);
        }
      }),
        responseData.scholarships.map(async (t) => {
          const e = await t;
          console.log('t', t)
          for (let t = 0; t < this.CS_DATA_LIST.length; t++)
            this.CS_DATA_LIST[t].course.name === e.course.name && this.CS_DATA_LIST[t].school.name === e.school.name && this.CS_DATA_LIST[t].content_level.name === e.content_level.name && this.CS_DATA_LIST[t].scholarships.push(e);
        });

      this.details = this.CS_DATA_LIST[0]
      this.details1 = this.CS_DATA_LIST[0]
      console.log(this.details)
      this.getMode()
    },
    getMode() {
      responseData.scholarships.map((mode, index) => {
        this.mode.push(mode.content_modality.name)
        this.units.push(mode.unit.name)
        this.shift.push(mode.content_shift.name)
        this.course.push(mode.content_type.name)
        this.mode1.push(mode.content_modality.name)
        this.shift1.push(mode.content_shift.name)

      })

      let unique_mode = [...new Set(this.mode)]
      let unique_shift = [...new Set(this.shift)]
      let unique_course = [...new Set(this.course)]
      let unique_mode1 = [...new Set(this.mode1)]
      let unique_shift1 = [...new Set(this.shift1)]
      let units = [...new Set(this.units)]
      this.mode = unique_mode;
      this.shift = unique_shift;
      this.course = unique_course
      this.mode1 = unique_mode1;
      this.shift1 = unique_shift1;
      this.units = units;
    },
    changeModalities(data1) {
      var filterData = []
      // this.details.scholarships=[]
      console.log(this.CS_DATA_LIST[0].scholarships.length)
      // this.CS_DATA_LIST[0].scholarships.filter((data, index) => {
      //       if(data.content_modality.name == data1){
      //      return   filterData.push(data)

      //       } 
      //     }
      //     )
      responseData.scholarships.filter((data, index) => {
        if (data.content_modality.name == data1) {
          return filterData.push(data)

        }
      }
      )
      console.log(this.CS_DATA_LIST[0].scholarships.length)
      this.details4['scholarships'] = filterData
      this.details.scholarships = filterData;
    },
    changeShifts(data2) {
      var filterData = []
      if (this.details4.scholarships == undefined) {
        alert('selecione a modalidade')
      }
      else {
        this.details4.scholarships.filter((data, index) => {
          if (data.content_shift.name == data2) {
            return filterData.push(data)

          }
        }
        )
        this.details5['scholarships'] = filterData
        this.details.scholarships = filterData;
        console.log(this.details4)
      }

    },
    changeUnits(data3) {
      var filterData = []
      if (this.details5.scholarships == undefined) {
        alert('selecione a modalidade')
      }
      else {
        this.details5.scholarships.filter((data, index) => {
          if (data.unit.name == data3) {
            return filterData.push(data)

          }
        }
        )
        this.details.scholarships = filterData;
      }
    },
    modeChange(event) {
      this.filterResults = this.details1
      if (event.target.value != 'Ver Todos') {
        var filterData=[];
         responseData.scholarships.filter((data, index) => {
        if (data.content_modality.name == event.target.value) {
          return filterData.push(data)

        }
      }
      )
      console.log(this.CS_DATA_LIST[0].scholarships.length)
      this.details4['scholarships'] = filterData
      this.details.scholarships = filterData;
      }
    else{
            this.details.scholarships = responseData.scholarships
                  this.details4['scholarships'] =  responseData.scholarships
    }
    },
    modeChange1(event) {
console.log(this.details4)
 var filterData=[];
      if (event.target.value != 'Ver Todos') {
         if (this.details4.scholarships==undefined) {
         responseData.scholarships.filter((data, index) => {
        if (data.content_shift.name == event.target.value) {
          return filterData.push(data)
        }
        this.details.scholarships=filterData
        console.log(this.details)
      }
      )
        }
        else {
              this.details4.scholarships.filter((data, index) => {
        if (data.content_shift.name == event.target.value) {
          return filterData.push(data)
        }
      this.details.scholarships=filterData
      }
      )
          // this.details = this.details.filter((data, index) => {
          //   return data.content_shift.name == event.target.value
          // })
          this.details3 = this.details.scholarships
        }
        
      }
      else {
    
            console.log('this is working12',this.details4)
         this.details=this.details4
         console.log(this.details)
        
      }
    },
    modeChange2(event) {
      this.filterResults = this.details
      if (event.target.value != 'Ver Todos') {
        this.status = true;

        this.filterResults.find((data, index) => {

          const flag = data.content_type.name == event.target.value
          if (flag) {
            this.newData.push(data)

          }
        }
        )
      }
    }

  },
  mounted() {
    this.getData()
  }
}
</script>

<template>
  <div class="container-fluid">
    <div class="row mb-5">
      <div class="col-md-3">
        <div class="card institution">
          <div class="card-body">
            <form>
              <label>Institution?</label>
              <select class="form-select mb-3" aria-label="Default select example">
                <option selected>Open this select menu</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
              <label>Find a Course:</label>
              <select class="form-select mb-3" aria-label="Default select example">
                <option selected>Open this select menu</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
              <label>City:</label>
              <select class="form-select mb-3" aria-label="Default select example">
                <option selected>Open this select menu</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
              <label class="mb-3">Mode:</label> <br />
              <div v-for="data in mode" :key='data'>
                <input type="radio" name="test_id1" @change="modeChange($event)" v-bind:value="data"> {{ data }}
              </div>
              <label class="mb-3">Shift:</label> <br />
              <div v-for="data in shift" :key='data'>
                <input type="radio" name="test_id2" @change="modeChange1($event)" v-bind:value="data"> {{ data }}
              </div>
              <label>Course Level:</label>
              <select class="form-select mb-3" aria-label="Default select example">
                <option selected>Open this select menu</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
              <label>Study area:</label>
              <select class="form-select mb-3" aria-label="Default select example">
                <option selected>Open this select menu</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
              <label class="mb-3">Course Type:</label>
              <div v-for="data in course" :key='data'>
                <input type="radio" name="test_id3" @change="modeChange2($event)" v-bind:value="data"> {{ data
                }}
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-9">
        <div class="card institution">
          <div class="card-body">
            <div class="row">
              <div class="col-md-3">
                <div>
                  <img :src="details.school?.image" height="100" class="imagess" />
                  <div class="text-center mb-4">
                    <h3>{{ details.school?.name }}</h3>
                  </div>
                  <!-- <div v-html="data.more_bonus_text_button">
                  </div> -->

                </div>
              </div>
              <div class="col-md-9 ead">
                <h3>{{ details.course?.name }}</h3>
                <div>
                  <label class="mt-3">Modalities:</label> <br />

                  <div class="btn-group" role="group" aria-label="Basic checkbox toggle button group">
                    <div v-for="data in mode1" :key='data' class="mx-1">
                      <input type="radio" class="btn-check" name="btnradio" v-bind:id="data" autocomplete="off">
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data" @click="changeModalities(data)">{{
                          data
                      }}</label>
                    </div>
                  </div>

                  <br />
                  <label class="mt-3">Shifts :</label> <br />
                  <div class="btn-group" role="group" aria-label="Basic checkbox toggle button group">
                    <div v-for="data in shift1" :key='data' class="mx-1">
                      <input type="radio" class="btn-check" name="btnradio1" v-bind:id="data" autocomplete="off">
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data" @click="changeShifts(data)">{{
                          data
                      }}</label>
                    </div>
                  </div>
                  <br />
                  <label class="mt-3">Units:</label> <br />
                  <div class="btn-group" role="group" aria-label="Basic checkbox toggle button group"
                    style="flex-wrap:wrap">
                    <div v-for="data in units" :key='data' class="mx-1">
                      <input type="radio" class="btn-check" name="btnradio2" v-bind:id="data" autocomplete="off">
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data" @click="changeUnits(data)">{{ data
                      }}</label>
                    </div>
                  </div>

                </div>
              </div>
            </div>

            <div class="my-4">
              <hr />
            </div>
            <div  v-if="details.scholarships?.length!=0">
            <div class="payment" v-for="data in details.scholarships" :key='data'>
              <div class="row">
                <div class="col-md-9">
                  <div class="row">
                    <div class="col-md-3">
                      <p>Modality: <b> {{ data?.content_modality?.name }} </b><br />
                        Shift:<b> {{ data?.content_shift?.name }} </b><br />
                        Unit:<b>{{ data?.unit?.name }} </b></p>
                    </div>
                    <div class="col-md-3">
                      <p>Type: <b> {{ data?.content_type?.name }} </b><br />
                        's Degree Duration: <br /> <b>{{ data?.duration }} {{ data?.duration_type }} </b><br />
                        Installments:<b> {{ data?.discount_installments }} </b></p>
                    </div>
                    <div class="col-md-3">
                      <p class="p-0">Monthly payment: <br />
                        <span class="frombrl">From BRL {{ data?.original_price }}</span><br />
                        For <b> BRL <br /><span class="brl">{{ data?.comission_amount }}</span> </b>
                      </p>
                      <small class="text-center">8785865 VB163.28 - 100</small>
                    </div>
                    <div class="col-md-3">
                      <p>Scholarship: <b> {{ data?.percent }}%</b> <br />
                        Total Savings:
                        <b> BRL {{ data?.economy_total }} </b>
                      </p>
                    </div>
                  </div>
                </div>
                <div class="col-md-3 text-center">
                  <a href="#">see details</a> <br />
                  <button class="btn btn-success btn-sm" type="button">CHOOSE THIS BAG</button>
                </div>
              </div>
            </div>
         </div>
         <div v-if="details.scholarships?.length==0">
         <p>Não há bolsas disponíveis com os itens selecionados, mude a unidade, turno ou modalidade selecionada.</p>
          </div>
          </div>
        </div>
        <!-- <div class="my-4">
        <nav aria-label="Page navigation example">
          <ul class="pagination">
            <li class="page-item"><a class="page-link" href="#">Previous</a></li>
            <li class="page-item"><a class="page-link" href="#">1</a></li>
            <li class="page-item"><a class="page-link" href="#">2</a></li>
            <li class="page-item"><a class="page-link" href="#">3</a></li>
            <li class="page-item"><a class="page-link" href="#">Next</a></li>
          </ul>
        </nav>
        </div> -->
      </div>
    </div>

  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

span.brl {
  font-size: 1.83em;
  color: #21293e;
  font-weight: bold;
}

h3 {
  font-size: 1.2rem;
}

span.frombrl {
  text-decoration: line-through;
}
</style>
