<template>
    <div class="container">
      <table about='clique para editar' class="table table-bordered  table-hover" >
        <thead>
          <tr>
            <td>Nome</td>
            <td>e-mail</td>
            <td>Telefone</td>
            <td>Remover</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for='item in fullNameList' :key='item.fullName'>
            <td>
              <input
                @keyup.enter='editObj'
                :id='fullNameList.indexOf(item)'
                type="text"
                v-model="item.fullName"
                value='item.fullName'
                title='Digite e pressione [Enter] para salvar'
              />
            </td>
            <td>
              <input
                @keyup.enter='editObj'
                :id='fullNameList.indexOf(item)'
                type="email"
                v-model="item.email"
                value='item.email'
                title='Digite e pressione [Enter] para salvar'
              />
            </td>
            <td>
              <input
                @keyup.enter='editObj'
                :id='fullNameList.indexOf(item)'
                type="tel"
                size="7" v-model="item.tel"
                value='item.tel'
                title='Digite e pressione [Enter] para salvar'
              />
            </td>
            <td class='tdButtons' >
              <a class="btn btn-danger" @click="remove(fullNameList.indexOf(item))">
                X
              </a>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
</template>

<script>
export default {
    name: 'table-client',
    props: {
      list: {
        type: Array
      }
    },
    methods: {
      remove(index) {
        this.$emit('delete', index)
      },
      editObj(e) {
        this.$emit('editObject', e)
      }
    },
    computed: {
      fullNameList() {
        this.list.forEach(o=>o.fullName=o.name+' '+o.lastName)
        return this.list
      }
    }
}
</script>

<style>
    .container{
      margin: 20px;
      min-width: 700px;
      width: fit-content;
    }
    table thead{
      background: #0005;
      color: white;
    }
    a{
      opacity: .1;
    }
    tr:hover a{
      opacity: .8;
    }
    .tdButtons{
      display: flex;
      align-items: center;
      justify-content: space-evenly;

    }
    td > input{
      background: rgba(0,0,0,0);
      border: none;
      height: 40px;
    }
</style>