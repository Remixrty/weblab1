<template>
    <div>
        <v-stepper v-model="numStep">
            <v-stepper-header>
                <v-stepper-step :complete="numStep > 1" step="1">
                    Вход
                </v-stepper-step>
                 <v-divider></v-divider>
                <v-stepper-step :complete="numStep > 2" step="2">
                    Регистрация
                </v-stepper-step>
                 <v-divider></v-divider>
                <v-stepper-step :complete="numStep > 3" step="3">
                    Ваши данные
                </v-stepper-step>
            </v-stepper-header>
            <v-stepper-items>
                <v-stepper-content step="1">
                    <v-card  class="card"
                        elevation="10">
                        <Step1  @Accept="AcceptName" @AcceptRegister="AcceptRegister"/>
                        
                    </v-card>
                    
                </v-stepper-content>
                <v-stepper-content step="2">
                    <v-card  class="card"
                        elevation="10">
                        <Step2  @Accept="AcceptMail"/>
                    </v-card>
                </v-stepper-content>
                <v-stepper-content step="3">
                    <v-card  class="card"
                        elevation="10">
                        <Step3  :Person="Person"/>
                    </v-card>
                </v-stepper-content>
            </v-stepper-items>
        </v-stepper>
    </div>    
</template>

<script>
import Step1 from './Steps/Step1.vue'
import Step2 from './Steps/Step2.vue'
import Step3 from './Steps/Step3.vue'
export default {
    name: 'Stepper',
    components:{
        Step1,
        Step2,
        Step3
    },
    data:function(){
        return{
            Person: {
                Email:"",
                Password:"",
                
            },
            numStep: 1
            
        }
    },
    methods:{
        AcceptName: function(Email, Password){
            this.Person.Email = Email
            this.Person.Password = Password
            this.numStep = this.numStep+2
        },
        AcceptRegister: function(){
            this.numStep = this.numStep+1
        },
        AcceptMail: function(Email, Password){
            this.Person.Email = Email
            this.Person.Password = Password
            this.numStep = this.numStep+1
        },
        
    }
}
</script>

<style scoped>
.card{
    margin: 10% 10%;
    padding: 5% ;
    
}

</style>