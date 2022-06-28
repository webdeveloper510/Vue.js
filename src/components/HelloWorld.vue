<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
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
              <label class="mb-3">Mode:</label> <br/>
             
              <label class="mb-3">Shift:</label> <br/>
             
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
            </form>
        </div>
      </div>
   </div>
   <div class="col-md-9">
     <div class="card institution">
       <div class="card-body">
         <div class="row">
           <div class="col-md-3">
             <div >
               <img src="../assets/icons.png" height="100" class="imagess"/>
               <div class="text-center mb-4">
                 <h3>Estácio de Sá</h3>
               </div>
               <button class="btn btn-success form-control" data-bs-toggle="tooltip" data-bs-placement="top" title="By joining the scholarship through the Bolsa Mais Brasil program, the student is exempt from paying a monthly fee at the institution." >+1 bonus</button>
             </div>
           </div>
           <div class="col-md-9 ead">
             <h3>MANAGEMENT</h3>
             <label class="mt-3">Modalities:</label> <br/>
             <button class="btn btn-outline-success btn-sm" type="button">EAD</button>
             <button class="btn btn-outline-success mx-3 btn-sm" type="button">Semi-Present</button>
             <button class="btn btn-outline-success btn-sm" type="button">Presential</button>
             <br/>
             <label class="mt-3">Shifts :</label> <br/>
             <button class="btn btn-outline-success btn-sm" type="button">FREE</button>
             <button class="btn btn-outline-success mx-3 btn-sm" type="button">MORNING</button>
             <button class="btn btn-outline-success btn-sm" type="button">NIGHT</button>
             <br/>
             <label class="mt-3">Units:</label> <br/>
             <div class="d-flex">
              <button class="btn btn-outline-success btn-sm" type="button">CENTRO POLO - BELO HORIZONTE - MG</button>
             <button class="btn btn-outline-success mx-3 btn-sm" type="button">POLO SILVA LOBO - BELO HORIZONTE - MG</button>
             <div class="dropdown">
              <button class="btn btn-link dropdown-toggle btn-sm" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
                                    see all units
              </button>
              <div class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
               <button class="btn btn-outline-success" type="button">BELO HORIZONTE POLO - CASTELO - MG</button>
               <button class="btn btn-outline-success" type="button">BELO HORIZONTE POLO - SAVASSI - MG</button>
               <button class="btn btn-outline-success" type="button">EAD VENDA NOVA - MG</button>
               <button class="btn btn-outline-success" type="button">EAD VILARINHO - VENDA NOVA - MG</button>
               <button class="btn btn-outline-success" type="button">BELO HORIZONTE POLO - PLANALTO - MG</button>
               <button class="btn btn-outline-success" type="button">BELO HORIZONTE POLO - CAMARGOS - MG</button>
               <button class="btn btn-outline-success" type="button">BELO HORIZONTE POLO - BARRO PRETO - CENTER - MG</button>
               <button class="btn btn-outline-success" type="button">EAD BH BARREIRO - MG</button>
               <button class="btn btn-outline-success" type="button">EAD BH - OURO PRETO - MG</button>
               <button class="btn btn-outline-success" type="button">UNION POLO - BELO HORIZONTE - MG</button>
               <button class="btn btn-outline-success" type="button">EAD BELO HORIZONTE - SANTA IFIGÉNIA - MG</button>
               <button class="btn btn-outline-success" type="button">PADRE EUSTAQUIO POLO - BELO HORIZONTE - MG</button>
               <button class="btn btn-outline-success" type="button">EAD BELO HORIZONTE - BETANIA - MG</button>
               <button class="btn btn-outline-success" type="button">POLO PRADO - BELO HORIZONTE - MG</button>
               <button class="btn btn-outline-success" type="button">MEADOW</button>
               <button class="btn btn-outline-success" type="button">NEW SALE</button>
              </div>
            </div>
           </div>
           </div>
         </div>

         <div class="my-4">
           <hr/>
         </div>
         <div class="payment">
           <div class="row">
             <div class="col-md-9">
                <div class="row">
                  <div class="col-md-3">
                     <p>Modality: <b> EAD </b><br/>
                        Shift:<b> Free </b><br/>
                        Unit:<b>POLO CENTRO - BELO HORIZONTE - MG </b></p>
                  </div>
                  <div class="col-md-3">
                    <p>Type: <b> Bachelor </b><br/>
                      's Degree Duration: <br/> <b>4 year(s) </b><br/>
                      Installments:<b> 47 </b></p>
                  </div>
                  <div class="col-md-3">
                    <p class="p-0">Monthly payment: <br/>
                        <span class="frombrl">From BRL 466.50</span><br/>
                        For <b> BRL <br/><span class="brl">163.28</span> </b></p>
                        <small class="text-center">8785865 VB163.28 - 100</small>
                  </div>
                  <div class="col-md-3">
                    <p>Scholarship: <b> 65.00%</b> <br/>
                        Total Savings:
                       <b> BRL 14717.84 </b></p>
                  </div>
                </div>
             </div>
             <div class="col-md-3 text-center">
                <a href="#">see details</a> <br/>
                <button class="btn btn-success btn-sm" type="button">CHOOSE THIS BAG</button>
             </div>
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
