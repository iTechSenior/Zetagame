<template>
  <div class="sb-tree-list">
    <ul class="sb-sports-list">
      <li v-for="(item, index) in items" :key="index">
        <a class="sb-sports-item" @click="togglePanel(item.id)">
          <img class="sb-icon" :src="item.icon" />
          {{ item.name }}
          <span class="sb-count">
            {{ item.count }}
            <div v-if="item.status == 1" class="sb-status on"></div>
            <div v-else class="sb-status off"></div>
          </span>
        </a>
        <ul v-if="item.children" :id="`ul_${item.id}`">
          <li v-for="(item1, id1) in item.children" :key="id1">
            <a class="sb-country-item" @click="togglePanel(item1.id)">
              <img class="sb-icon" :src="item1.icon" />
              {{ item1.name }}
              <span class="sb-count">
                {{ item1.count }}
                <div v-if="item1.status == 1" class="sb-status on"></div>
                <div v-else class="sb-status off"></div>
              </span>
            </a>
            <ul v-if="item1.children" :id="`ul_${item1.id}`">
              <li v-for="(item2, id2) in item1.children" :key="id2">
                <a class="sb-team-item">
                  <img class="sb-icon" :src="item2.icon" />
                  {{ item2.name }}
                  <span class="sb-count">
                    {{ item2.count }}
                    <div v-if="item2.status == 1" class="sb-status on"></div>
                    <div v-else class="sb-status off"></div>
                  </span>
                </a>
              </li>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      default: () => {
        return []
      }
    }
  },
  data() {
    return {}
  },
  methods: {
    togglePanel(id) {
      let eId = `ul_${id}`
      let element = document.getElementById(eId)
      if (!element) return
      let computedStyle = window.getComputedStyle(element)
      let displayValue = computedStyle.getPropertyValue('display')
      if (displayValue === 'none') displayValue = 'block'
      else displayValue = 'none'
      element.style.display = displayValue
    }
  }
}
</script>

<style>
.sb-tree-list ul {
  padding-left: 0;
  -webkit-transition: display 2s;
  transition: display 2s, opacity 2s;
}
.sb-tree-list > ul ul {
  display: none;
}
.sb-tree-list {
  padding-bottom: 10px;
  padding-top: 5px;
  cursor: pointer;
}
.sb-tree-list li {
  list-style: none;
}
.sb-tree-list a {
  background-color: #252525;
  display: list-item;
  border-bottom: 1px solid black;
}
.sb-tree-list a:hover {
  background-color: #303030;
}
.sb-count {
  float: right;
  color: white;
}
.sb-icon {
  width: 12px;
  height: 12px;
  margin-top: 6px;
  margin-right: 5px;
}
.sb-status {
  float: right;
  width: 10px;
  height: 10px;
  margin-top: 6px;
  margin-left: 10px;
}
.sb-status.off {
  background-color: grey;
}
.sb-status.on {
  background-color: green;
}
.sb-sports-item,
.sb-country-item,
.sb-team-item {
  padding-right: 10px;
}
.sb-sports-item {
  padding-left: 10px;
}
.sb-country-item {
  padding-left: 30px;
}
.sb-team-item {
  padding-left: 50px;
}
</style>
