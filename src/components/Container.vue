<template>
  <div class="row">
    <div class="col-sm">
    <h4>Django RestApi Data</h4>
    <br/>
      <table class="table">
        <thead>
          <th>Id</th>
          <th>Name</th>
          <th>Price</th>
          <th>Status</th>
        </thead>
        <tbody>
          <tr v-for="laptop in laptops" v-bind:key="laptop.id">
            <td>{{ laptop.id }}</td>
            <td>{{ laptop.name }}</td>
            <td>{{ laptop.price }}</td>
            <td>{{ laptop.status }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Container',
  props: {
    msg: String
  },
  data(){
    return{
      laptops:'',
      id:'',
      name:'',
      price:'',
      status:''
    }
  },
  mounted(){
    this.getAll()
  },
  methods:{
    getAll(){
      axios.get('http://localhost:8000/api/laptops')
      .then((res)=>{
        this.laptops=res.data
      })
    }
  }
}
</script>


<style scoped>

</style>
