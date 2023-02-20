<template>
  <div class="computed-properties container">
    <div class="row">
      <div class="col-12">
        <h1>Computed Properties</h1>
        <p>
          We have learned expressions, which can be really nice in our
          templates, but too much logic in the template can be problematic.
          Another reason to use computed properties is they give us the ability
          to access the same computed value in several places in the template.
        </p>
<pre>
<code class="language-markup">
&lt;div class="reverse-message"&gt;
    &lt;p&gt;Original Message: {{state.val}}&lt;/p&gt;
    &lt;p&gt;Computed Reversed Message: {{state.val2}}&lt;/p&gt;
&lt;/div&gt;</code>
</pre>
<pre>
<code class="language-javascript">
export default {
    name: 'computed-properties-exercise',
    setup() {
      const state = reactive({
        message: "Hello World!"
        reversedMessage: computed(()=> state.message.split("").reverse().join('')) 
    })
    return {
      state
    }
  }
}</code>
</pre>
        <p>
          Notice the "reversedMessage" reference is accessing a property on the
          state that happens to be a method that is set up to return a value.
          The reversedMessage method is written under the computed property on
          our state. The computed is referencing the original "message" property
          on the component and is performing an action on it and returning the
          result for us to use as many times as needed in the component.
        </p>
        <p>Try this one yourself in the ComputedPropertiesExercise.vue</p>
        <hr />
        <h1>Exercise</h1>
        <exercise></exercise>
      </div>
    </div>
  </div>
  <ul class="list-group">
          <li class="list-group-item active bg-info">
            <p>Glossary of Terms</p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">Vue</b> - A frontend javascript framework that
              makes building user interfaces easier.
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">Component</b> - A .vue file that contains an HTML
              template, script area for javascript, and a style area for css.
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">Page</b> - A collection and layout of various
              components.
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">Data Binding</b> - A connection between a property
              on the component(in the data() return object) and the template.
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">AppState</b> - The AppState utilizes the observer
              pattern and a single source of truth for all components in the app
              using vue's reactive wrapper.
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">Router</b> - The Vue Router is used to evaluate the
              address in the url and determine which page should be displayed.
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">V Directives</b> - The special directives for Vue,
              all begin with a v and tell Vue to use some special behind the
              scene processes. Examples: v-if, v-for, v-show
            </p>
          </li>
          <li class="list-group-item border">
            <p class="mb-0">
              <b class="m-0">Reactive</b> - When the data on the page updates
              automatically based on the state of the application, the user is
              not required to refresh the page to get the needed data.
            </p>
          </li>
        </ul>
</template>


<script>
import { computed, onMounted, reactive } from "vue";
import Exercise from "../components/ComputedPropertiesExercise.vue";
export default {
  name: "computed-properties",
  setup() {
    // @ts-ignore
    onMounted(() => Prism.highlightAll())
    
    const state = reactive({
      val: "{{ state.message }}",
      val2: "{{ state.reversedMessage }}",
      message: "Hello World!",
      reversedMessage: computed(() => {
        state.message.split("").reverse().join("");
      }),
    });
    return {
      state,
    };
  },
  components: { Exercise },
};
</script>


<style scoped>
</style>
