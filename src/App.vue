<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn depressed href="https://github.com/katsunory/px-vw-calculator" target="_blank">
        <v-icon>fab fa-github</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container grid-list-md>
        <v-layout row>
          <v-flex xs6>
            <v-select v-model.number="baseWidth" :items="devices" label="Device"></v-select>
          </v-flex>
          <v-flex xs6>
            <v-text-field v-model.number="baseWidth" type="number" label="Base Width" suffix="px"></v-text-field>
          </v-flex>
        </v-layout>
        <v-layout row>
          <v-flex xs6>
            <v-text-field v-model.number="fontSizePx" type="number" label="Font Size (px)" value="10" suffix="px"></v-text-field>
          </v-flex>
          <v-flex xs6>
            <v-text-field type="text" label="Font Size (vw)" :value="calcVw" suffix="vw" readonly></v-text-field>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex>
            <v-textarea label="FontSize scales with window size.（フォントサイズが画面幅に応じて拡縮します）" value="Hello world." :style="{fontSize: `${calcVw}vw`}"></v-textarea>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer app>
      <v-text class="ml-2">&copy; 2018</v-text>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data: function() {
    return ({
      title: 'px-vw-calclator',
      selectedDevice: null,
      devices: [
        {
          text: "iPhone5/SE",
          value: 320,
        },
        {
          text: "iPhone6/7/8/X",
          value: 375,
        },
        {
          text: "iPhone6/7/8 Plus",
          value: 414,
        },
        {
          text: "Responsive",
          value: "",
        },
      ],
      baseWidth: 320,
      fontSizePx: 10,
    });
  },
  computed: {
    calcVw() {
      return (100 / this.baseWidth) * this.fontSizePx;
    }
  }
}
</script>
