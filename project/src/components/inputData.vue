<template>
  <div class="container">
    <h3> Get Data Form whith Vue.js </h3>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Register</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Username</label>
                    <input type="text" id="username" class="form-control" v-model.lazy="userData.userName">
                    
                  </div>
                  <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" class="form-control" v-model.lazy.trim="userData.password">
                  </div>
                  <div class="form-group">
                    <label for="age">Age</label>
                   <input type="number" id="age" class="form-control" v-model.number="userData.age">
                  
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Descripcion</label><br>
                  <textarea id="message" rows="3" class="form-control" v-model.lazy.trim="userData.destripcionTextarea"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input type="checkbox" value="Software" v-model="userData.interest"> Software
                    </label>
                    <label>
                      <input type="checkbox" value="Hardware" v-model="userData.interest"> Hardware
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input type="radio" value="erkek" v-model="userData.gender"> Male
                  </label>
                  <label>
                    <input type="radio" value="kadin" v-model="userData.gender"> Famale
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>Şehir</label>
                  <select class="form-control" v-model="userData.selectedCity">
                    <option v-for="city in userData.cities" :key="city">{{ city }}</option>
                    
                  </select>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button
                    class="btn btn-primary" @click.prevent="submit">Submit!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmited">
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Form Data</h4>
            </div>
            <div class="panel-body">
              <p>Username: {{ userData.userName }}</p>
              <p>Password: {{ userData.password }}</p>
              <p>Age: {{userData.age}}</p>
              <p style="white-space: pre;">Descripcion: {{ userData.destripcionTextarea }} </p>
              <p><strong>İnterest</strong></p>
              <ul>
                <li v-for="item in userData.interest" :key="item">{{item }}</li>
                
              </ul>
              <p>Gender: {{ userData.gender }}</p>
              <p>City: {{ userData.selectedCity }}</p>
              <p>Toggle: {{ isSubmited }}</p>
            </div>
          </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    data : function () {
      return {
          userData : {
            userName : "",
            password : "",
            age : null,
            destripcionTextarea : "",
            interest : [],
            gender : "",
            cities : ["istanbul" , "Ankara", "İzmir", "Samsun","Konya"],
            selectedCity : ""

          },

          isSubmited : false, 

      }
    },

    methods : {
          submit () {
              this.isSubmited = true;
          }
    }
  }
</script>

<style>

</style>
