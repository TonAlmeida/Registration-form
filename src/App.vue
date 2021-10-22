<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <FormClients @adicione='add' ></FormClients>
    <TableClients
      v-if='registered.length >= 1'
      @editObject='edit'
      @delete='del'
      :list='Cregistered'
    ></TableClients>
  </div>
</template>

<script>
import FormClients from './components/FormClients.vue'
import TableClients from './components/table-clients.vue'

export default {
      name: 'App',
      data() {
        return {
          title: 'VueJS-form',
          registered: []
        }
      },
      components: {
        FormClients,
        TableClients
      },
      methods: {
        add(people) {
          this.registered.push(JSON.stringify(people))
        },
        del(index) {
          this.registered.splice(index, 1)
        },
        edit(e) {
          const index = e.target.id,
                type = e.target.type,
                value = e.target.value
          this.Cregistered[index][type] = value
          console.log(this.Cregistered)

        }
      },
      computed: {
          Cregistered() {
            return this.registered.map(i => JSON.parse(i))
          }
      }
}
</script>

<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
    min-height: 100vh;
    background: linear-gradient(to right, rgb(0,242,96), rgb(5,117,230));
    
    display: flex;
    justify-content: center;
    align-items: center;
}
#app {
    min-width: 100%;
    min-height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
h1{
  position: absolute;
  top: 100px;
  background: #0005;
  padding: 20px;
  border-radius: 10px;
  color: #fff;
}
</style>
