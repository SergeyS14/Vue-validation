<script>
export default {
  data() {
    return {
      errorName: '',
      errorPas: '',
      errorSecPas: '',
      inputName: '',
      inputPassword: '',
      inputSecondPassword: '',
      Pas:'',
      Name:''
    };
  },
  computed:{
    isFormValid(){
      return(
        this.inputName.trim() !== '' &&
        this.inputPassword.trim() !== '' &&
        this.inputPassword.length >= 5 &&
        this.inputPassword.trim() === this.inputSecondPassword 
        
        

      );
    },
    btnActive(){
      return(
        this.inputName.trim() !== '' &&
        this.inputPassword.trim() !== '' && 
        this.inputPassword.length >= 5 &&
        this.inputPassword.trim() === this.inputSecondPassword 
      );
    },
    nameErrors() {
      return this.errorName 
    },

    pasErrors() {
      return this.errorPas;
    },

    secPasErrors() {
      return this.errorSecPas;
    }
  },

  methods: {
    handleSubmit() {
      
    },

    validateName() {
      this.errorName = '';
      
      if (this.inputName.trim() !== '') {
        console.log('Имя:', this.inputName);
        this.errorName = ''
        } else   {this.errorName = 'Обязательное поле'}
    },
    validatePassword(){
      this.errorPas = '';
      if (this.inputPassword.trim() === '' ) {
             this.errorPas = 'Обязательное поле';
            }
        else if (this.inputPassword.length <= 5 ) {this.errorPas = 'минимальное кооличество символов 5'}
    },
    validateSecondPassword(){
        if (this.inputPassword.trim() !== this.inputSecondPassword){
            this.errorSecPas = 'пароли не совпадают'
        } else {console.log(this.inputPassword);
        this.errorSecPas = '';  this.Pas = this.inputPassword; this.Name = this.inputName
        }
    }
  }
};
</script>

<template>
  <div id="app" class="validate" >
    <form @submit.prevent="handleSubmit" class="form">

        
      <label class="form__label" for="inputName">Введите имя:</label>
        <p v-if="errorName" class="form__error" >{{errorName}}</p>
      <input class="form__input" :class="{ 'error-form': nameErrors}" type="name" id="inputName" v-model="inputName" @input="validateName">
        
      <label class="form__label" for="inputPassword">Введите пароль:</label>
        <p v-if="errorPas" class="form__error">{{errorPas}}</p>
      <input class="form__input" :class="{ 'error-form': pasErrors}" type="password" id="inputPassword" v-model="inputPassword" @input="validatePassword">

      <label class="form__label" for="inputSecondPassword">Подвердите пароль:</label>
        <p v-if="errorSecPas" class="form__error">{{errorSecPas}}</p>
      <input class="form__input" :class="{ 'error-form': secPasErrors}" type="password" id="inputSecondPassword" v-model="inputSecondPassword" @input="validateSecondPassword">
      
      <button class="form__btn" :class="{'btn-active':btnActive}" type="submit" :disabled="!isFormValid" >Сохранить</button>
    </form>
    <p>Имя: {{Name}} </p>
    <p>Пароль: {{Pas}} </p>
  </div>
</template>

<style scoped>
</style>
