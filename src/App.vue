<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue';
</script>

<template>
<div class="top-header">
  <div class="container">
    <div class="row">
      <div class="col-md-3">
        <p>HOW IT WORKS</p>
      </div>
       <div class="col-md-3">
        <p>0800-441-4321</p>
      </div>
       <div class="col-md-3 text-center">
        <p> FACEBOOK</p>
      </div>
       <div class="col-md-3 text-center">
        <p> INSTAGRAM</p>
      </div>
    </div>
  </div>
</div>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
          <a class="navbar-brand" href="#"><img src="./assets/logo.png" height="70px" width="100%" alt="logo"/></a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <a class="nav-link " href="#">PARTNER INSTITUTIONS</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">CONTACT US</a>
              </li>
              <li class="nav-item">
                <a class="nav-link " href="#" >Pedro Santos</a>
              </li>
              <li class="nav-item">
                <a class="nav-link " href="#" >REGISTRATION</a>
              </li>
              <li> <button class="btn btn-success" type="button">STUDENT PORTAL</button></li>
            </ul>
           
          </div>
        </div>
      </nav>
  </header>
    <div class="container-fluid">
      <nav aria-label="breadcrumb">
        <ol class="breadcrumb mt-5">
          <li class="breadcrumb-item"><a href="#">MORE BRAZIL SCHOLARSHIP</a></li>
          <li class="breadcrumb-item active" aria-current="page">COURSES</li>
        </ol>
      </nav>
      <h3 class="mb-5">Courses with Scholarships - Bolsa Mais Brasil</h3>
      <HelloWorld/>
    </div>
</template>

<style>
@import '@/assets/base.css';

#app {
  margin: 0 auto;
  font-weight: normal;
}

</style>
