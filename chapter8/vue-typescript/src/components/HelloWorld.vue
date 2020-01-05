<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-typescript" target="_blank" rel="noopener">typescript</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>
    <pre>{{obj}}</pre>
  </div>
</template>

<script lang="ts">
import Vue,{PropType} from 'vue';

export type HelloWorldObjProps = {
  name: string
}

type Todo = {
  id: string
}
type Data = {
  doneTodos: null | boolean,
  todos: Todo[]
}

export default Vue.extend({
  name: 'HelloWorld',
  props: {
    msg: String,
    obj: {
      type: Object as PropType<HelloWorldObjProps>,
      required: true
    },
  },
  data: (): Data => ({
    // doneTodos: null as null | boolean,
    // todos: [] as Array<{
    //     id: string
    // }>
    doneTodos: null,
    todos: []
  }),
  computed: {
    greet(): string {
      return 'hello world';
    },
    getDoneTodos(): boolean {
      if (this.doneTodos === null) {
        return false;
      }
      return this.doneTodos;
    }
  },
  methods: {
    hoge() {
      this.doneTodos = true; // Type '"hoge"' is not assignable to type 'null'.
      this.todos.push({id: 'hoge'}); // Argument of type '"hoge"' is not assignable to parameter of type 'never'.
    }
  }
});
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
