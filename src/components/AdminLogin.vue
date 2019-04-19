import Vue from 'vue'
<template>
  <div id="vue_det">
    bring a component in anoter one
    <HelloWorld>
    </HelloWorld>
    <HelloWorld>
    </HelloWorld>
    <hr>
    show object with a method
    <h1>{{mydetails()}}</h1>
    <hr>
    show data html
    <div v-html="htmlcontent"></div>
    <hr>
    show computed imput
    <div id = "computed_props">
      FirstName : <input type="text" v-model="computedfirstname">
      <br>
      <br>
      LastName : <input type="text" v-model="computedlastname">
      <br>
      <br>
      <h1>My name is {{computedfirstname}} {{computedlastname}}</h1>
      <h1>Using computed method : {{getfullname}}</h1>
    </div>
    <hr>
    computed input with get and set
    <br>
    <input type="text" v-model="fullname">
    <h1>{{obj.firstname}}</h1>
    <h1>{{obj.lastname}}</h1>
    <hr>
    convert with a watch property
    <br>
    <br>
    Kilometers: <input type="text" v-model="kilometers">
    Meters: <input type="text" v-model="meters">
    <hr>
    Vbind a attribute
    <br>
    <br>
    <a v-bind:href="hreflink" target="_blank">Click Me</a>
    <hr>
    Vbind a class html
    <br>
    <br>
    <div v-bind:class="{active:isactive}">
      <strong>{{title}}</strong>
    </div>
    <hr>
    Vbind multiple class html
    <br>
    <br>
    <div class="info" v-bind:class="{active: isActive, 'displayError': hasError}">
      {{title2}}
    </div>
    <hr>
    vbind with class in array
    <br>
    <br>
    <div v-bind:class="[infoclass, errorclass]">
      {{stringTestVbindArray}}
    </div>
    <hr>
    v-bind with bool
    <br>
    <br>
    <div v-bind:class = "[isActive ? infoclass : '', haserror ? errorclass : '']">{{vbindwithboolTitle}}</div>
  </div>
</template>

<script>
var obj = {
  firstname: 'Ria',
  lastname: 'Singh',
  address: 'Mumbai'
}

export default {
  name: 'AdminLogin',
  data () {
    return {
      obj: obj,
      computedfirstname: '',
      computedlastname: '',
      htmlcontent: '<h1>Vue Js Template</h1>',
      kilometers: 0,
      meters: 0,
      hreflink: 'http://www.google.com',
      isactive: true,
      title: 'test v-bind a class',
      title2: 'test v-bind multiple class',
      isActive: true,
      hasError: false,
      infoclass: 'info',
      errorclass: 'displayError',
      stringTestVbindArray: 'Testing to apply a multiple class with array',
      hasErrorBool: false,
      vbindwithboolTitle: 'v-bind with bool'
    }
  },
  methods: {
    mydetails: function () {
      return 'I am ' + this.obj.firstname + ' ' + this.obj.lastname + ' from ' + this.obj.address
    }
  },
  computed: {
    getfullname: function () {
      return this.computedfirstname + ' ' + this.computedlastname
    },
    fullname: {
      get: function () {
        return obj.firstname + ' ' + obj.lastname
      },
      set: function (name) {
        var fname = name.split(' ')
        obj.firstname = fname[0]
        obj.lastname = fname[1]
      }
    }
  },
  watch: {
    kilometers: function (val) {
      this.kilometers = val
      this.meters = val * 1000
    },
    meters: function (val) {
      this.kilometers = val / 1000
      this.meters = val
    }
  },
  components: {
    HelloWorld: () => import('./HelloWorld.vue')
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.active {
  background: red;
}
.info {
  color: #00529B;
  background-color: #BDE5F8;
}
div {
  margin: 10px 0;
  padding: 12px;
}
.displayError{
  color: #D8000C;
  background-color: #FFBABA;
}
</style>
