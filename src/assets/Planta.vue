<template>
  <iframe id="online-alarm-kur-iframe" src="https://embed-countdown.onlinealarmkur.com/pt/#2024-11-11T00:00:00@America%2FSao_Paulo" width="360" height="80" style="display: block; margin: 0px auto; border: 0px;"></iframe>

  <section style="display: flex">

    <svg id="svg-wrapper"  viewBox="0 0 1069 797" shape-rendering="geometricPrecision"
       text-rendering="geometricPrecision">

    <path troke-linejoin="round" v-for="path in Object.values(svgPaths)" :key="path.id" :id="path.id" :d="path.d"  :opacity="path.opacity"
    :fill="path.fill" :stroke="path.stroke" :stroke-width="path.strokeWidth"/>
    <text font-size="14" fill="black" v-for="path in Object.values(svgPaths)" :key="path.id">
      <textPath :href="`#${path.id}`">
        {{path.text}}
      </textPath>
    </text>
  </svg>
  <ul>
    <li v-for="item in Object.values(svgPaths)" :key="item.id" style="display: flex; gap: 4px; cursor: pointer" @click="focusSpace(item)" >
      <div :style="`background: ${item.fill};`" style="width: 40px; height: 20px;"/>
      <span>{{item.text}}</span>
    </li>
  </ul>
  </section>
</template>
<script setup lang="ts">
import { ref } from 'vue';
interface ISvg {
  [key: string]: ISvgPath

}
interface ISvgPath {
  id: string
  d: string
  fill: string
  stroke: string
  strokeWidth: number
  transform?: string // Campo opcional, caso algum path tenha transform
  text?: string // Campo opcional, caso algum path tenha transform
  opacity?: string
}


const svgPaths = ref({
  "svg-contorno": {
    id: "svg-contorno",
    d: "M428.220499,742.757644l-57.915674-1.288343v24.367442l-182.397512-1.740531v-13.053988h-5.221594L57.367443,753.653021L46.053988,742.339566v-35.680898l-18.275582,1.740531.870266-162.739705l8.702658-4.351329v-2.610797l1.740531-49.605151v-121.837207h113.303327l15.906311,24.842231l9.162625-7.436915-4.351329-88.50831l4.351329-49.863958l99.210301,1.740532l2.610798-22.626911h16.53505v-112.264289l22.626911-.870266-1.740532-29.589037l11.313456-10.443189h103.56163l4.351329-20.88638l15.664785-.870266l120.966946-.870265l1.740532,27.848505h71.361796l.870265,14.794519l78.323923-.870266.870265-23.497176l65.269936-3.481064l10.443189,7.832393l9.233434-7.832393l80.403944,53.831726l33.0701-44.258802l115.745352,76.583391l16.53505,81.804985-4.351329,41.772759L870.195703,398.499998l10.443189,20.100689-80.064454,57.437543l24.367443,42.643024-92.347557,67.010467v13.053987L534.5,737.117972l-7.189024-9.572925L503.8138,698.826275l.870266-67.880732-6.091861-22.626911-85.286049-1.740532-2.610797,20.88638l20.886379,16.53505-3.361239,98.758114Z",
    fill: "#d9d9d9",
    stroke: "black",
    strokeWidth: 2.138,
  },
  "svg-soccer-simulation": {
    id: "svg-soccer-simulation",
    d: "M654.51051,320.401647h156.167628v-117.368218h-155.197643l-.969985,117.368218Z",
    fill: "#ad341f",
    stroke: "black",
    strokeWidth: 2.138,
    text:'Soccer Simulation'
  },
  "svg-on-stage": {
    id: "svg-on-stage",
    d: "M629.290892,293.24206l-258.986067,2.909956v-11.639824l-24.249632,1.939971-1.649191-164.919541l283.661614-3.298391l1.223276,175.007829Z",
    fill: "#2b8655",
    stroke: "black",
    strokeWidth: 2.138,
    text:'On Stage'
  },
  "svg-auditorio": {
    id: "svg-auditorio",
    d: "M410.695359,476.038232v130.53987h87.896846v-130.53987h-87.896846Z",
    fill: "#851fad",
    stroke: "black",
    strokeWidth: 2.138,
    text:'Auditório'
  },
  "svg-ieee": {
    id: "svg-ieee",
    d: "M404.293522,598.74571h-29.149808l.549997-115.552676l27.499818.549996l1.099993,115.00268Z",
    fill: "#5fad1f",
    stroke: "black",
    strokeWidth: 2.138,
    text:'IEEE'
  },
  "svg-rc-home": {
    id: "svg-rc-home",
    d: "M376.24371,627.46448l-.55,86.17703h-58.98706v-86.17703h59.53706Z",
    fill: "#ad1fa6",
    stroke: "black",
    strokeWidth: 2.138,
    text:'@home'
  },
  "svg-tv-mnr": {
    id: "svg-tv-mnr",
    d: "M403.193529,678.441743l14.299905-.549997l1.099992,35.749763-15.399899-.000001.000002-35.199765Z",
    fill: "#ad911f",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'TV MNR'
  },
  "svg-rbc-challenge": {
    id: "svg-rbc-challenge",
    d: "M247.544558,436.993339l-.549996,52.09888h91.299396v-53.748869l-90.7494,1.649989Z",
    fill: "#ad1f5a",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Robocup Challenge'
  },
  "svg-humanoid": {
    id: "svg-humanoid",
    d: "M238.19462,506.842877l.549996,99.735225l84.69944-.000001v-99.185229l-85.249436-.549995Z",
    fill: "#ad511f",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Humanoid'
  },
  "svg-rc-work": {
    id: "svg-rc-work",
    d: "M238.744616,627.464482v86.177028h57.075657l-.000001-86.177028h-57.075656Z",
    fill: "#1fadad",
    stroke: "black",
    strokeWidth: 2.138,
    transform: "matrix(1.091966 0 0 1-23.130893 0)",
    text:'@work'
  },
  "svg-ssl": {
    id: "svg-ssl",
    d: "M77.045686,489.092221q0,224.549289.549996,224.549289t95.517113.000002l4.351328-224.549293-100.418437.000002Z",
    fill: "#1fad72",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Soccer Simulation'
  },
  "svg-flying": {
    id: "svg-flying",
    d: "M39.962127,445.243286l112.43306-1.64999.000001-76.338287h-113.303328l.870267,77.988277Z",
    fill: "#1f21ad",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Flying'
  },
  "svg-comp": {
    id: "svg-comp",
    d: "M228.294685,292.131209v93.343589l96.587087.296377v-93.639966h-96.587087Z",
    fill: "#39ad1f",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Comp'
  },
  "svg-food": {
    id: "svg-food",
    d: "M 557.377 445.243 h 89.1601 v -106.292 l -89.1601 -0.000001 v 106.292 Z",
    fill: "#e85d45",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Alimentação'
  },
  "svg-cowork2": {
    id: "svg-cowork2",
    d: "M801.444704,184.802257v-40.57622h44.633545l18.374138-25.991804L801.444703,72.2349l-33.456542,62.804068h-24.49885v49.763289h57.955393Z",
    fill: "#71d5ab",
    stroke: "black",
    text:'Cowork 1',
    strokeWidth: 2.138,

  },
  "svg-cowork": {
    id: "svg-cowork",
    d: "M773.347285,371.543774l27.227153,58.246985l69.621264-45.130437-24.117457-45.709128-72.73096,32.59258Z",
    fill: "#82f1c3",
    stroke: "black",
    strokeWidth: 2.138,
    text:'Cowork 2'
  },
  "svg-chapadao-do-ceu": {
    id: "svg-chapadao-do-ceu",
    d: "M891.082082,367.255009l62.178634-33.162884-13.780603-37.940107-69.28441,28.753038l20.886379,42.349953Z",
    fill: "#f1bd82",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'SBR'
  },
  "svg-cavalcante": {
    id: "svg-cavalcante",
    d: "M864.452384,274.136566l11.483836,46.265081l40.576221-14.636318-9.18707-37.513865-42.872987,5.885102Z",
    fill: "#f18296",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'SBR 2'
  },
  "svg-aruana": {
    id: "svg-aruana",
    d: "M864.452384,225.401681l42.87299,6.962126v35.887659l-42.872987,5.885101q-.000006-48.734885-.000003-48.734886Z",
    fill: "#f1ce82",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Trusstee'
  },
  "svg-juizes": {
    id: "svg-juizes",
    d: "M654.51051,144.226037l.969985,40.57622h88.008817l-1.531178-40.57622h-87.447624Z",
    fill: "#4a4269",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Coordenação OBR e Juízes'
  },
  "svg-stands": {
    id: "svg-stands",
    d: "M358.893806,338.95119v79.649499L534.5,418.600688v-79.649494l-175.606194-.000004Z",
    fill: "#f182e8",
    stroke: "black",
    strokeWidth: 2.138,
    text: 'Stands'
  },
} as ISvg)

function focusSpace(item : ISvgPath){

  item.opacity = '0.3'

  setTimeout(() => {
    item.opacity = '1'
  }, 500);

}


defineOptions({
  name: 'PlantaBaixa'
})
</script>
<style scoped>
svg {
  height: 100vh;
}
</style>
