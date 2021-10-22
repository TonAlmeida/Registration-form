<template>
  <form  @submit='send'>
            <div class="form-grup">
                <label for="name">Nome</label>
                <input
                    class='form-control'
                    type="text"
                    size='25'
                    placeholder=" Digite seu nome"
                    id='name'
                    v-model='people.name'
                    required
                />
            </div>
            <div class="form-grup">
                <label for="lastName">Sobrenome</label>
                <input
                    class='form-control'
                    type="text"
                    size='25'
                    placeholder=" Digite seu sobrenome"
                    id='lastName'
                    v-model='people.lastName'
                    required
                />
            </div>
            <div class="form-grup">
                <label for="e-mail">E-mail</label>
                <input
                    class='form-control'
                    type="email"
                    size='25'
                    placeholder=" Digite seu e-mail"
                    id='e-mail'
                    v-model='people.email'
                    required
                />
            </div>
            <div class="form-grup">
                <label for="tel">Telefone</label>
                <input
                    class='form-control'
                    type="tel"
                    size='25'
                    placeholder=" Digite seu telefone"
                    id='tel'
                    v-model='people.tel'
                    required
                />
            </div>
            <hr>
            <div class="form-grup emphasis">
                <input
                    class='form-check-input'
                    type="checkbox"
                    id='checkPeople'
                    v-model='people.checkPeople'
                />
                <label class="form-check-label" for="checkPeople">Pessoa Juridica</label>
            </div>
            <hr>
            <div v-if='people.checkPeople' class="form-grup">
                <label for="cnpj">CNPJ</label>
                <input
                    class='form-control'
                    type="number"
                    size="25"
                    placeholder=" Digite seu CNPJ"
                    id='cnpj'
                    v-model='people.cnpj'
                    required
                />
            </div>
            <div v-else class="form-grup">
                <label for="cpf">CPF</label>
                <input
                    class='form-control'
                    type='number'
                    size="25"
                    placeholder=" Digite seu CPF"
                    id='cpf'
                    v-model='people.cpf'
                    required
                />
            </div>
            <div class='container-button'>
                <button type="reset" class='btn btn-light' @reset='reset'>
                    Limpar
                </button>
                <button type="submit" class="btn btn-primary">
                    Cadastrar
                </button>
            </div>
        </form>
</template>

<script>
export default {
        name: 'form-client',
        props: {
        },
        data() {
            return {
                people: {
                    name: '',
                    lastName: '',
                    tel: '',
                    email: '',
                    checkPeople: false,
                    cpf: '',
                    cnpj: ''
                }
            }
        },
        watch: {
            checkPeople() {
                this.people.checkPeople = !this.people.checkPeople
            }
        },
        methods: {
            send(e) {
                e.preventDefault()
                this.$emit('adicione', this.people)
                this.reset(e)
            },
            reset(e) {
                e.preventDefault()
                this.people.name = ''
                this.people.lastName = ''
                this.people.tel = ''
                this.people.email = ''
                this.people.checkPeople = false
                this.people.cpf = ''
                this.people.cnpj = ''
            }
        }
    }
</script>
    
<style>
    form{
        background: #fff;
        border-radius: 20px;
        padding: 20px;
        margin: 20px;
    }
    .emphasis{
        margin-left: 20px;
    }
    .container-button{
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin: 10px;
    }
</style>