<script>
export default {
  data() {
    return {
      errorName: '',
      errorPas: '',
      inputName: '',
      inputPassword: '',
      inputSecondPassword: '',
      Pas:'',
      Name:''
    };
  },
  methods: {
    handleSubmit() {
      this.errorName = '';
      this.errorPas = '';

      if (this.inputName.trim() !== '') {
        console.log('Имя:', this.inputName);
        this.errorName = ''
        } else   {this.errorName = 'Обязательное поле'}

        if (this.inputPassword.trim() === '' ) {
             this.errorPas = 'Обязательное поле';
            }
        else if (this.inputPassword.length <= 3 ) {this.errorPas = 'минимальное кооличество символов 5'}

        else if (this.inputPassword.trim() !== this.inputSecondPassword){
            this.errorSecPas = 'пароли не совпадают'
        } else {console.log(this.inputPassword);
        this.errorSecPas = ''; this.errorPas = ''; this.Pas = this.inputPassword; this.Name = this.inputName
        }
    }
  }
};
</script>

<template>
  <div id="app" >
    <form @submit.prevent="handleSubmit" class="form">

        
      <label for="inputName">Введите имя:</label>
        <p v-if="errorName" class="error" >{{errorName}}</p>
      <input type="name" id="inputName" v-model="inputName">
        
      <label for="inputPassword">Введите пароль:</label>
        <p v-if="errorPas" class="error">{{errorPas}}</p>
      <input type="password" id="inputPassword" v-model="inputPassword">

      <label for="inputSecondPassword">Подвердите пароль:</label>
        <p v-if="errorSecPas" class="error">{{errorSecPas}}</p>
      <input type="password" id="inputSecondPassword" v-model="inputSecondPassword">
      
      <button type="submit">Сохранить</button>
    </form>
    <p>Имя: {{Name}} </p>
    <p>Пароль: {{Pas}} </p>
  </div>
</template>

<style scoped>
</style>
