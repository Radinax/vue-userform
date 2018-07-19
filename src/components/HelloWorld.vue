<template>
  <div class="hello">
    <h1>Hey Welcome to my App :D</h1>
    <form v-on:submit="addUser">
      <ul>
        <!-- Name -->
        <input type="text" v-model="newUser.firstName" placeholder="FirstName" />
        <input type="text" v-model="newUser.lastName" placeholder="LastName" />
        <br />
        <!-- Gender -->
        <input type="radio" name="gender" id="female" value="female" v-model="newUser.gender">
        <label for="female">Female</label>
        <input type="radio" name="gender" id="male" value="male" v-model="newUser.gender">
        <label for="female">Male</label>
        <br />
        <!-- Identification -->
        <select v-model="newUser.idType">
          <option disabled value="Tipo de Identificacion">Tipo de identificacion</option>
          <option>Cedula</option>
          <option>Pasaporte</option>
        </select>
        <span>{{ newUser.idType }}</span>
        <br />
        <input type="text" v-model="newUser.id" placeholder="Numero de identificacion" />
        <br />
        <!-- Type of Blood -->
        <label>Tipo de Sangre</label>
        <br />
        <input type="radio" name="blood" value="O+" v-model="newUser.blood"><label>O+</label>
        <input type="radio" name="blood" value="O-" v-model="newUser.blood"><label>O-</label>
        <input type="radio" name="blood" value="A+" v-model="newUser.blood"><label>A+</label>
        <input type="radio" name="blood" value="A-" v-model="newUser.blood"><label>A-</label>
        <input type="radio" name="blood" value="B+" v-model="newUser.blood"><label>B+</label>
        <input type="radio" name="blood" value="B-" v-model="newUser.blood"><label>B-</label>
        <input type="radio" name="blood" value="AB+" v-model="newUser.blood"><label>AB+</label>
        <input type="radio" name="blood" value="AB-" v-model="newUser.blood"><label>AB-</label>
        <br />
        <!-- Phone -->
        <select v-model="newUser.phoneType">
          <option>Celular</option>
          <option>Telefono</option>
        </select>
        <select v-model="newUser.countryCode">
          <option>+506</option>
          <option>+58</option>
        </select>
        <input type="text" v-model="newUser.phoneNumber" placeholder="Numero de Telefono" />
        <input type="email" v-model="newUser.email" placeholder="Correo" />
        <br />
        <!-- Testing -->
        <li v-for="user in users" v-bind:key="user.firstName">
          {{user.firstName}} {{user.lastName}}
        </li>
        <br />
        <!-- Submit -->
        <input type="submit" value="submit"/>
      </ul>
    </form>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      newUser: {},
      users: []  
    }
  },
  methods: {
    addUser: function(e) {
      this.users.push({
        firstName: this.newUser.firstName,
        lastName: this.newUser.lastName,
        gender: this.newUser.gender,
        id: this.newUser.id,
        idType: this.newUser.idType,
        blood: this.newUser.blood,
        phoneType: this.newUser.phoneType,
        countryCode: this.newUser.countryCode,
        phoneNumber: this.newUser.phoneNumber,
        email: this.newUser.email
      });
      console.log(this.newUser);
      e.preventDefault();
    }
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>
