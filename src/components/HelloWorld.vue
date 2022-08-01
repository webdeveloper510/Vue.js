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
       details6: [],
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
      modeValue: [],
      shiftValue: [],
      status: Boolean = false,
    }
  },
  computed: {
    sortedCategories() {

    }

  },
  methods: {
    getData() {
      this.details = responseData.scholarships
      // this.details5 = responseData.scholarships
      console.log(this.details1)
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
          var shifts = [], modalities = [], units = []
          for (let t = 0; t < this.CS_DATA_LIST.length; t++) {
            this.CS_DATA_LIST[t].course.name === e.course.name && this.CS_DATA_LIST[t].school.name === e.school.name && this.CS_DATA_LIST[t].content_level.name === e.content_level.name && this.CS_DATA_LIST[t].scholarships.push(e);
          }
        });

      this.details = this.CS_DATA_LIST
      this.getMode()

    },
    getData1() {
      responseData.scholarships.map(async (t) => {
        if ((this.SCHOLARSHIPS.push(t), this.details5.length > 0)) {
          let e = this.details5.find((e) => e.course.name === t.course.name && e.school.name === t.school.name);

          if (null == e) {
            let e = { course: t.course, school: t.school, content_level: t.content_level, modalities: [], shifts: [], units: [], scholarships: [] };
            this.details5.push(e);
          }
        } else {
          let e = { course: t.course, school: t.school, content_level: t.content_level, modalities: [], shifts: [], units: [], scholarships: [] };
          this.details5.push(e);
        }
      }),

        responseData.scholarships.map(async (t) => {
          const e = await t;
          var shifts = [], modalities = [], units = []
          for (let t = 0; t < this.details5.length; t++) {
            this.details5[t].course.name === e.course.name && this.details5[t].school.name === e.school.name && this.details5[t].content_level.name === e.content_level.name && this.details5[t].scholarships.push(e);

          }
        });
      this.details3 = this.details5
      console.log(this.details3)
      // this.getMode()

    },
    async getMode() {
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

      for (var i = 0; i < this.CS_DATA_LIST.length; i++) {
        this.getModalities(await this.CS_DATA_LIST[i].scholarships, i)
        this.getShifts(await this.CS_DATA_LIST[i].scholarships, i)
        this.getUnitss(await this.CS_DATA_LIST[i].scholarships, i)

      }
    },
    getModalities(t, index) {
      let e = "",
        a = [];

      t.map((t) => {
        if (a.length > 0) {
          let e = a.find((e) => e.id === t.content_modality.id);
          null == e && a.push(t.content_modality);
        } else a.push(t.content_modality);
      })
      this.CS_DATA_LIST[index].modalities.push(...a)
    },
    getShifts(t, index) {
      let e = "",
        a = [];

      t.map((t) => {
        if (a.length > 0) {
          let e = a.find((e) => e.id === t.content_shift.id);
          null == e && a.push(t.content_shift);
        } else a.push(t.content_shift);
      })

      this.CS_DATA_LIST[index].shifts.push(...a)
      console.log(this.CS_DATA_LIST)
    },
    getUnitss(t, index) {
      let e = "",
        a = [];

      t.map((t) => {
        if (a.length > 0) {
          let e = a.find((e) => e.id === t.unit.id);
          null == e && a.push(t.unit);
        } else a.push(t.unit);
      })

      this.CS_DATA_LIST[index].units.push(...a)

    },
    changeModalities(data1, index) {
      var filterData = {
        scholarships: []
      }
      if (this.modeValue.length > 0 && this.shiftValue.length > 0) {
        location.reload()
      }
      else {
        var filter1 = []
        filter1 = this.details5
        this.CS_DATA_LIST[index].scholarships = this.details5[index].scholarships
        this.modeValue = []
        this.modeValue.push(data1.name)
        console.log(this.CS_DATA_LIST)
        this.CS_DATA_LIST[index].scholarships.filter((data, index) => {
          // console.log('i am here',data)
          if (data.content_modality.name == data1.name) {
            return filterData.scholarships.push(data)
          }
        }
        )
        this.CS_DATA_LIST[index]['scholarships'] = filterData.scholarships
        this.details = filterData.scholarships
        console.log('filterData', this.details)
      }


    },
    changeShifts(data2, index) {
      var filterData = []
      var filter1 = []
      this.shiftValue = []
      this.shiftValue.push(data2.name)
      console.log(this.CS_DATA_LIST, index)
      if (this.modeValue.length == 0) {
        alert('selecione a modalidade')
      }
      else {
        console.log(this.CS_DATA_LIST)
        this.CS_DATA_LIST[index].scholarships.filter((data, index) => {
          if (data.content_shift.name == data2.name && data.content_modality.name == this.modeValue[0]) {
            return filterData.push(data)

          }
        }
        )
        console.log(filterData)
        this.CS_DATA_LIST[index]['scholarships'] = filterData
        this.details5 = this.CS_DATA_LIST[index]['scholarships']
        console.log(this.details5)
        // this.details=filterData;
      }

    },
    changeUnits(data3, index) {
      var filterData = []
      var filter1 = []
      filter1 = this.details
      delete filter1.scholarships
      this.CS_DATA_LIST[index].scholarships = filter1
      console.log(this.CS_DATA_LIST, index)
      if (this.modeValue.length == 0) {
        alert('selecione a modalidade')
      }
      else {
        console.log(this.CS_DATA_LIST)
        this.CS_DATA_LIST[index].scholarships.filter((data, index) => {
          if (data.unit.name == data3.name && data.content_modality.name == this.modeValue[0] && data.content_shift.name == this.shiftValue[0]) {
            return filterData.push(data)

          }
        }
        )
        console.log(filterData)
        this.CS_DATA_LIST[index]['scholarships'] = filterData
        this.details5 = this.CS_DATA_LIST[index]['scholarships']
        console.log(this.details5.length)
        // this.details=filterData;
      }
    },
    //this one 
    async modeChange(event) {
      let filterResults =[] 
      filterResults= this.CS_DATA_LIST
      if (event.target.value != 'Ver Todos') {
        this.details4=filterResults
        this.details4.map(async (t,index) => {
          const e = await t;
          console.log(e)
          var scholarship=[]
          var shifts = [], modalities = [], units = []
          for (var t = 0; t < this.details4[index].scholarships.length; t++) {
             console.log(this.details4[index].scholarships[t].content_modality.name===event.target.value)
             if(this.details4[index].scholarships[t].content_modality.name.toLowerCase()===event.target.value.toLowerCase()){
              // scholarship.push(this.details4[index].scholarships[t])
              // this.details6[index]=this.details4[index]
               scholarship.push(this.details4[index].scholarships[t])
             }
            
          }
          if(scholarship.length>0){
            delete t.scholarships
            this.details6[index]=t
             this.details6[index]['scholarships']=scholarship
          }
          else{
             this.details6[index]=[]
          }
                    console.log(this.details6)
       
        });
        
      }
    },
  async  modeChange1(event) {
      console.log(this.details6)
      let dataValue=[]
      let filterData=[];
      dataValue=this.details6
      console.log(dataValue)
      if (event.target.value != 'Ver Todos') {
        if (this.details6.length > 0) {
          this.details6.map(async (t,index) => {
          const e = await t;
          console.log(e)
          let scholarship=[]
          var shifts = [], modalities = [], units = []
          for (let t = 0; t < dataValue[index].scholarships.length; t++) {
             console.log(dataValue[index].scholarships[t].content_shift.name===event.target.value)
             if(dataValue[index].scholarships[t].content_shift.name===event.target.value){
              // scholarship.push(this.details4[index].scholarships[t])
              // this.details6[index]=this.details4[index]
               scholarship.push(dataValue[index].scholarships[t])
             }
            
          }
          if(scholarship.length>0){
            delete t.scholarships
            filterData[index]=t
             filterData[index]['scholarships']=scholarship
          }
          else{
           console.log( filterData[index])
          }
                    console.log(filterData)
       
        });
        }
        else {
          this.details4.scholarships.filter((data, index) => {
            if (data.content_shift.name == event.target.value) {
              return filterData.push(data)
            }
            // this.details.scholarships = filterData
          }
          )
          // this.details = this.details.filter((data, index) => {
          //   return data.content_shift.name == event.target.value
          // })
          this.details3 = this.details.scholarships
        }

      }
      else {
        this.details = this.details4
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
    this.getData1()
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
      <div class="col-md-9" v-if="CS_DATA_LIST.length == 0">
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
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data"
                        @click="changeShifts(data, index)">{{
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
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data"
                        @click="changeUnits(data, index)">{{ data
                        }}</label>
                    </div>
                  </div>

                </div>
              </div>
            </div>

            <div class="my-4">
              <hr />
            </div>
            <div v-if="details.length != 0">
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
            <div v-if="details.length == 0">
              <p>Não há bolsas disponíveis com os itens selecionados, mude a unidade, turno ou modalidade selecionada.
              </p>
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

      <div class="col-md-9" v-if="CS_DATA_LIST.length > 0">
        <div class="card institution" v-for="(data, index) in CS_DATA_LIST" :key='data'>
          <div class="card-body">
            <div class="row">
              <div class="col-md-3">
                <div>
                  <img :src="data.school?.image" height="100" class="imagess" />
                  <div class="text-center mb-4">
                    <h3>{{ data.school?.name }}</h3>
                  </div>
                  <!-- <div v-html="data.more_bonus_text_button">
                  </div> -->

                </div>
              </div>
              <div class="col-md-9 ead">
                <h3>{{ data.course?.name }}</h3>
                <div>
                  <label class="mt-3">Modalities:</label> <br />

                  <div class="btn-group" role="group" aria-label="Basic checkbox toggle button group">
                    <div v-for="data in data.modalities" :key='data' class="mx-1">
                      <input type="radio" class="btn-check" name="btnradio" v-bind:id="data.name + index"
                        autocomplete="off">
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data.name + index"
                        @click="changeModalities(data, index)">{{
                            data.name
                        }}</label>
                    </div>
                  </div>

                  <br />
                  <label class="mt-3">Shifts :</label> <br />
                  <div class="btn-group" role="group" aria-label="Basic checkbox toggle button group">
                    <div v-for="data in data.shifts" :key='data' class="mx-1">
                      <input type="radio" class="btn-check" name="btnradio1" v-bind:id="data.name + index"
                        autocomplete="off">
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data.name + index"
                        @click="changeShifts(data, index)">{{
                            data.name
                        }}</label>
                    </div>
                  </div>
                  <br />
                  <label class="mt-3">Units:</label> <br />
                  <div class="btn-group" role="group" aria-label="Basic checkbox toggle button group"
                    style="flex-wrap:wrap">
                    <div v-for="data in data.units" :key='data' class="mx-1">
                      <input type="radio" class="btn-check" name="btnradio2" v-bind:id="data.name + index"
                        autocomplete="off">
                      <label class="btn btn-outline-success btn-sm" v-bind:for="data.name + index"
                        @click="changeUnits(data, index)">{{ data.name
                        }}</label>
                    </div>
                  </div>

                </div>
              </div>
            </div>

            <div class="my-4">
              <hr />
            </div>
            <div>
              <div v-if="data.scholarships.length > 0">
                <div class="payment" v-for="data1 in data.scholarships" :key='data1'>
                  <div class="row">
                    <div class="col-md-9">
                      <div class="row">
                        <div class="col-md-3">
                          <p>Modality: <b> {{ data1?.content_modality?.name }} </b><br />
                            Shift:<b> {{ data1?.content_shift?.name }} </b><br />
                            Unit:<b>{{ data1?.unit?.name }} </b></p>
                        </div>
                        <div class="col-md-3">
                          <p>Type: <b> {{ data1?.content_type?.name }} </b><br />
                            's Degree Duration: <br /> <b>{{ data1?.duration }} {{ data1?.duration_type }} </b><br />
                            Installments:<b> {{ data1?.discount_installments }} </b></p>
                        </div>
                        <div class="col-md-3">
                          <p class="p-0">Monthly payment: <br />
                            <span class="frombrl">From BRL {{ data1?.original_price }}</span><br />
                            For <b> BRL <br /><span class="brl">{{ data1?.comission_amount }}</span> </b>
                          </p>
                          <small class="text-center">8785865 VB163.28 - 100</small>
                        </div>
                        <div class="col-md-3">
                          <p>Scholarship: <b> {{ data1?.percent }}%</b> <br />
                            Total Savings:
                            <b> BRL {{ data1?.economy_total }} </b>
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
              <div v-if="data.scholarships.length == 0">
                <p>Não há bolsas disponíveis com os itens selecionados, mude a unidade, turno ou modalidade selecionada.
                </p>
              </div>
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
