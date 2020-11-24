<template>
  <div id="app">
    <!-- <arbol :indice="0" titulo="Root">
      <arbol :indice="1" titulo="Child3" :conborde="true">
        <arbol :indice="4" titulo="Child3.1" :conborde="true"></arbol>
        <arbol :indice="5" titulo="Child3.2" :conborde="true"></arbol>
        <arbol :indice="6" titulo="Child3.3" :conborde="true"></arbol>
        <div>
          <u>
            <li>Uno</li>
            <li>Dods</li>
          </u>
        </div>
      </arbol>
      <arbol :indice="3" titulo="Child4" :conborde="true">
        <arbol :indice="4" titulo="Child5" :conborde="false">
          <div>
            <u>
              <li>Uno</li>
              <li>Dods</li>
            </u>
          </div>
        </arbol>
      </arbol>
      <div>Hola Mundo3</div>
    </arbol>-->

    <!-- <PanelAlarma></PanelAlarma> -->

    <div class="container">
      <!--Tab de navegación-->
      <tabs
        :ListTabs="['Dashboard','Tabla','Gráficos','Usuario']"
        v-on:tabSelect="(index)=>{tabActive=index+1;}"
      ></tabs>

      <div class="card tab-card" v-if="tabActive==1">
        <panel-alarma></panel-alarma>
      </div>
      <!--El cuerpo de -->
      <div class="card tab-card" v-if="tabActive==2">
        <div class="card-body row">
          <!-- <div class="col col-3"> -->
          <!-- Inicio De Arbol --->
          <!-- <tree-node nombre="Reconquista">
              <tree-node nombre="Las Flores"></tree-node>
              <tree-node nombre="San Geronimo">
                <tree-node nombre="Casa 52" :device="true">
                  <node-sensor>Temperatura</node-sensor>
                  <node-sensor>Temperatura</node-sensor>
                  <node-sensor>Temperatura</node-sensor>
                </tree-node>
              </tree-node>
              <tree-node nombre="Las Flores"></tree-node>
          </tree-node>-->
          <!--Fin De Arbol - -->

          <!-- <tree-node v-for="rama in arbol" :key="rama.name" :nombre="rama.name"></tree-node> -->
          <!-- </div> -->
          <tree-constructor></tree-constructor>
          <div class="col">
            <table class="table table-sm table-hover">
              <thead>
                <tr>
                  <th scope="col">#</th>
                  <th scope="col">First</th>
                  <th scope="col">Last</th>
                  <th scope="col">Handle</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(item,key) in items" v-bind:key="key">
                  <th scope="row">{{key+1}}</th>
                  <td>{{item.nombre}}</td>
                  <td>Otto</td>
                  <td>@mdo</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>

    <!-- <div class="card" style="width: 18rem;">
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
        <p
          class="card-text"
        >Some quick example text to build on the card title and make up the bulk of the card's content.</p>
        <a href="#" class="card-link">Card link</a>
        <a href="#" class="card-link">Another link</a>
      </div>
    </div>-->
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Fecha from "./components/Fecha.vue";
import Tabla from "./components/Tabla.vue";
import Arbol from "./components/Arbol.vue";

import PanelAlarma from "./components/PanelAlarma.vue";
import TreeNode from "./components/tree-node.vue";
import NodeSensor from "./components/node-sensor.vue";
import Tabs from "./components/tabs.vue";
import TreeConstructor from "./components/tree-constructor.vue";

export default Vue.extend({
  name: "App",
  components: {
    HelloWorld,
    Fecha,
    Tabla,
    Arbol,
    PanelAlarma,
    TreeNode,
    NodeSensor,
    Tabs,
    TreeConstructor
  },
  data: function() {
    return {
      a: 1,
      tabActive: 0,
      arbol: [
        {
          name: "Reconquista",
          sub: [
            {
              name: "San Gerónimo",
              sub: [
                { name: "Mi Casa", sub: [] },
                { name: "Tu Casa", sub: [] }
              ]
            },
            { name: "Hospital", sub: [] }
          ]
        }
      ],
      items: [
        { nombre: "Joder" },
        { nombre: "Test" },
        { nombre: "Tilla" },
        { nombre: "Marcar" },
        { nombre: "Menear" },
        { nombre: "Salto" },
        { nombre: "Aquí voy" },
        { nombre: "Aquí voy1" },
        { nombre: "Aquí voy2" },
        { nombre: "Aquí voy3" },
        { nombre: "Aquí voy4" },
        { nombre: "Aquí voy5" }
      ]
    };
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}

.tab-card {
  border-top-width: 0px;
  /* padding-top: 25px;
  padding-left: 50px;
  padding-right: 50px;
  padding-bottom: 50px; */
}
</style>
