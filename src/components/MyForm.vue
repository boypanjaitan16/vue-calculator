<template>
    <div class="container-fluid" id="myForm">
        <div class="row">
            <div class="col-lg-4 col-md-4 offset-lg-4 offset-md-4">
                <div class="result" style="margin-bottom: 20px;">
                    <!-- 
                    <p class="helper" v-if="fullOpr.length !== 0">
                        <small v-bind="fullOpr">{{ fullOpr }}</small>
                    </p> 
                    -->
                    <input v-model="value" type="text" class="form-control" placeholder="Result"/>
                </div>
                <div class="row">
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(1)">1</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(2)">2</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(3)">3</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(4)">4</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(5)">5</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(6)">6</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(7)">7</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(8)">8</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-dark" type="button" @click="updateValue(9)">9</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-primary" type="button" @click="doOperation('+')">+</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-primary" type="button" @click="doOperation('-')">-</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-primary" type="button" @click="doOperation('*')">*</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-primary" type="button" @click="doOperation('/')">/</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-danger" type="button" @click="clearValue">C</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-danger" type="button" @click="clearLast">&#8592;</button>
                    </div>
                    <div class="col-lg-3 col-md-3">
                        <button class="btn btn-success" type="button" @click="getResult">=</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name    : 'MyForm',
    data(){
        return{
            title   : 'Your Form',
            value   : '',
            result  : 0,
            first   : 0,
            second  : 0,
            operation   : '',
            fullOpr     : ''
        }
    },
    methods : {
        updateValue(val){
            const oldVal    = this.value.toString();
            this.value      = oldVal+val;
        },
        clearValue(){
            this.value      = '';
            this.second     = 0;
            this.first      = 0;
            this.operation  = '';
        },
        clearLast(){
            const val       = this.value.toString();
            this.value      = val.substring(0, val.length - 1);
        },
        doOperation(opr){
            this.first      = parseFloat(this.value);
            this.value      = '';
            this.operation  = opr;
            
        },
        getResult(){
            const second    = parseFloat(this.value);
            switch(this.operation){
                case '-':
                    this.result = this.first - second;
                    break;
                case '+':
                    this.result = this.first + second;
                    break;
                case '*':
                    this.result = this.first * second;
                    break;
                case '/':
                    this.result = this.first / second;
                    break;
                default:
                    this.result = this.first;
                    break;
            }

            this.second = second;
            this.value  = this.result;
            this.first  = this.result;
            this.operation  = '';
        }
    },
    computed    : {
    } 
}
</script>
<style scoped>
    h2{
        text-align: center;
        font-weight: bold;
    }
    button{
        width: 100%;
        margin-top: 10px;
    }
    .helper{
        
        text-align: left;
        margin-top: 10px;
    }
    .helper * {
        font-weight: bold;
    }
</style>