<template>
  <div class="tree-menu">
    <div class="node-parent" @click="toggle">
      <div class="node">
        <div class="level">{{ level }}</div>
        <p>{{ code }}</p>
        <h3>{{ name }}</h3>
      </div>
    </div>
    <TreeMenu
      v-show="show"
      v-for="item in children"
      :key="item.id"
      :children="item.children"
      :name="item.name"
      :code="item.code"
      :level="item.level"
    />
  </div>
</template>

<script>
export default {
  name: "TreeMenu",
  props: ["name", "code", "level", "children"],
  data() {
    return {
      show: false,
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
  },
};
</script>

<style scoped>
p,
h3 {
  display: inline-block;
  margin: 0;
  padding: 0;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
  color: #666666;
}

.tree-menu {
  position: relative;
  list-style: none;
  margin-left: 32px;
  width: auto;
}

p {
  font-size: 12px;
  padding: 0 20px 0 9px;
}
.level {
  display: inline-block;
  width: 18px;
  height: 18px;
  text-align: center;
  background: #48647f;
  border-radius: 3px;
  color: #dcdcdc;
  font-size: 12px;
  line-height: 18px;
}
.node-parent {
  padding-bottom: 16px;
}
.node {
  display: flex;
  justify-content: start;
  text-align: center;
  background: #f0f0f0;
  border-radius: 4px;
  padding: 6px 7px;
}
.tree-menu:before {
  content: "";
  position: absolute;
  top: -16px;
  width: 2px;
  height: 100%;
  left: -16px;
  background: #dcdcdc;
}

.tree-menu:first-child:before {
  width: unset;
}
.node-parent:before {
  content: "";
  position: absolute;
  top: 1rem;
  width: 16px;
  height: 2px;
  background: #dcdcdc;
  left: -16px;
}
.tree-menu:first-child > .node-parent:before {
  width: unset;
}
.tree-menu:last-child:before {
  height: 33px;
}
.node:hover {
  background: #999999;
  cursor: pointer;
}
/* ul:nth-child(2) {
  height: 70px;
} */
</style>
