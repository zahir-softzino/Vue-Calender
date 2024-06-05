<template>
  <div class="w-full">
    <AppHeader />
    
    <CalenderComponent />   
    
  </div>
  
</template>

<script>
 
  import AppHeader from "./components/AppHeader.vue"
  import CalenderComponent from "./components/CalenderComponent.vue"
export default {
  components: {AppHeader, CalenderComponent},
  
}
</script>

