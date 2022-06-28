<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
     <div class="whatsapp">
       <div class="container">
         <div class="row">
           <div class="col-md-3">
               <div class="Rodape">
                 <p class="contatoItemRodape "> <i class="fa fa-phone"></i> 0800-441-4321 </p>
                    <p> Mon-Fri: 8 am to 8 pm</p>
               </div>
           </div>
           <div class="col-md-3">
             <div class="Rodape">
               <p class="contatoItemRodape "><i class="fa fa-whatsapp"></i> whatsapp </p>
                 <p> Mon-Fri: 8am to 10pm <br/>
                  Saturday: 8am to 2pm</p>
             </div>
           </div>
           <div class="col-md-3">
             <div class="Rodape">
               <p class="contatoItemRodape "> <i class='far fa-comment-dots'></i> live chat </p>
                 <p> Mon-Fri: 9am to 8pm <br/>
                  Saturday: 8am to 2pm </p>
             </div>
           </div>
           <div class="col-md-3">
             <div class="Rodape">
               <p class="contatoItemRodape "> <i class="fa fa-question-circle"></i> help Center </p>
                 <p> help at all times </p>
             </div>
           </div>
         </div>
       </div>
     </div>
</template>
