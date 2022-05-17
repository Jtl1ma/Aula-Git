<template>

<Banner></Banner>
  <div class="main-container">
    
  <h1>Monte sua Massa:</h1>
  <Form></Form>
  
  </div>
</template>

<script>
import Banner from "@/components/Banner.vue";
import Form from "@/components/Form.vue";
// @ is an alias to /src


export default {
  name: 'HomeView',
  components: {
    Banner,
    Form
}
}
</script>
