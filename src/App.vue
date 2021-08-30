<template>
  <div id="app">
    <div v-if="!user.result">
      <h1>Fazer cadastro</h1>
      <form>
        <label>Nome</label>
        <input type="text" v-model="user.name" />
        <label>Email</label>
        <input type="text" v-model="user.email" />
        <label>Senha</label>
        <input type="password" v-model="user.password" />
        <label>Idade</label>
        <input type="number" v-model="user.age" />
        <label>
          Escolha seu sexo
          <select v-model="user.selectedSex">
            <option v-for="item in user.sex" :key="item.id">
              {{ item.type }}
            </option>
          </select>
        </label>
        <label> Qual nível você se considera? </label>
        <div>
          <label>
            <input
              v-model="user.programmingLevel"
              value="junior"
              type="radio"
            />
            Junior
          </label>
          <label>
            <input v-model="user.programmingLevel" value="pleno" type="radio" />
            Pleno
          </label>
          <label>
            <input
              v-model="user.programmingLevel"
              value="senior"
              type="radio"
            />
            Senior
          </label>
        </div>
        <label> Selecione as tecnologias que você mais utiliza </label>
        <label>
          <input
            type="checkbox"
            v-model="user.mostUsedTechnologies"
            value="html"
          />
          html
        </label>
        <label>
          <input
            type="checkbox"
            v-model="user.mostUsedTechnologies"
            value="css"
          />
          Css
        </label>
        <label>
          <input
            type="checkbox"
            v-model="user.mostUsedTechnologies"
            value="javascript"
          />
          javascript
        </label>
        <label>
          <input
            type="checkbox"
            v-model="user.mostUsedTechnologies"
            value="python"
          />
          Python
        </label>
        <label>
          <input
            type="checkbox"
            v-model="user.mostUsedTechnologies"
            value="java"
          />
          Java
        </label>
        <label>
          <input
            type="checkbox"
            v-model="user.mostUsedTechnologies"
            value="c#"
          />
          C#
        </label>
        <label>Contrato de uso</label>
        <textarea cols="30" rows="10" readonly>
           Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum sit amet aliquam turpis. Duis mattis mi non elit gravida venenatis. Nunc ut mollis ligula. Phasellus sed turpis elementum nibh blandit gravida. Praesent viverra, lorem vel cursus porta, justo mauris lacinia eros, eu posuere dui diam quis sem. Sed sapien velit, ultricies sed dapibus vel, euismod ut justo. Aliquam diam dui, bibendum in mattis sit amet, tristique nec odio. Praesent sed commodo est. Fusce ac posuere enim. Integer nisi nisl, malesuada eu egestas a, venenatis sit amet magna. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Mauris vitae ullamcorper nibh. Vivamus nec augue enim. Suspendisse accumsan pharetra velit vel varius.

          Mauris sed tortor consequat nunc tristique tempor nec at felis. Integer nec magna cursus, accumsan ligula quis, ornare urna. Cras aliquet massa a venenatis vulputate. Etiam porta hendrerit est, et blandit massa eleifend eget. Vivamus sit amet sodales est, ut interdum lacus. Sed id tincidunt mi, eu tristique lacus. Quisque condimentum diam tellus. In porttitor pulvinar nisl in imperdiet. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Morbi dignissim lectus eget orci tincidunt fermentum. Vivamus venenatis eu nunc quis suscipit. Fusce a aliquam arcu. Proin dignissim nisl lectus, at ultrices quam semper pharetra.

          Morbi vel lectus vel nisl venenatis efficitur. Cras enim mauris, placerat vel tempus ac, euismod eu sem. In turpis metus, ultrices ut est vel, tempus dignissim mauris. Vivamus in feugiat purus. Cras quis mattis augue, in ullamcorper eros. Vivamus eu nisi volutpat, sagittis nisl vitae, molestie nisi. Vestibulum at arcu at eros rutrum imperdiet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Etiam dignissim tempor massa. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Vivamus vitae sollicitudin augue.
         </textarea
        >
        <label>
          <input type="checkbox" v-model="user.userContract" />
          Li e aceito os termos de uso
        </label>
        <button
          :disabled="
            !user.name ||
            !user.email ||
            !user.password ||
            !user.age ||
            !user.selectedSex ||
            !user.programmingLevel ||
            user.mostUsedTechnologies.length === 0 ||
            !user.userContract
          "
          @click="enviar"
          type="submit"
        >
          Enviar
        </button>
      </form>
    </div>

    <hr />

    <div class="item" v-show="user.result">
      <h1>Informações</h1>
      Nome: {{ user.name }} <br />
      Email: {{ user.email }} <br />
      Senha: {{ user.password }} <br />
      Idade: {{ user.age }}<br />
      Sexo: {{ user.selectedSex }}<br />
      Nivel: {{ user.programmingLevel }}
      <ul>
        Tecnologias Utilizadas:
        <li v-for="item in user.mostUsedTechnologies" :key="item">
          {{ item }}
        </li>
      </ul>
      Contrato: {{ user.userContract ? "Aceito" : "Não aceito" }}
    </div>
  </div>
</template>
<script>
import "./css/styles.css";
export default {
  name: "App",
  data() {
    return {
      user: {
        name: "",
        email: "",
        password: "",
        age: 0,
        programmingLevel: "",
        mostUsedTechnologies: [],
        sex: [
          { id: 1, type: "Masculino" },
          { id: 2, type: "feminino" },
          { id: 3, type: "outro" },
        ],
        userContract: false,
        selectedSex: "",
        result: false,
      },
    };
  },
  methods: {
    enviar(e) {
      e.preventDefault();
      if (
        confirm(
          "Clique em OK para cadastrar \nClique em Cancelar para cancelar"
        )
      ) {
        alert("Cadastrado com sucesso");
        this.user.result = true;
      } else {
        this.user.result = false;
      }
    },
  },
};
</script>
