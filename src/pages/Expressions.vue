<template>
  <div class="expressions container">
    <div class="row">
      <div class="col-12">
        <h1>Expressions</h1>
        <p>
          As you continue through this lesson, you will see some terminology
          that you may or may not have encountered in the past.
        </p>
        <h3>Vue helps you bridge the gap between html, css, and js</h3>
        <p>
          A cool and helpful feature of Vue is the ability to use Expressions in
          our HTML
        </p>
        <p>Example: {{ state.handleEg }}</p>
        <p>
          Vue parses your HTML and looks specifically for the double curly
          braces (aka: handlebars, mustache brackets). When Vue comes across a
          set of these brackets it essentially says this: Pause HTML
          {{ state.val }} Restart HTML.
        </p>
        <p>
          Remember in vanilla javascript we had to use a template string in our
          javascript and manually inject it into our html through the dom.
        </p>
        <h5>Vanilla Javascript Approach</h5>
        <pre><code class="language-javascript">let template = `
&lt;div class="player-card"&gt; 
  &lt;button class="btn btn-xs btn-danger remove" id="${player.id}"&gt;Remove&lt;/button&gt; 
  &lt;div&gt; 
    &lt;img src="http://s.nflcdn.com/static/content/public/image/fantasy/transparent/200x200" /&gt; 
  &lt;/div&gt; 
  &lt;div&gt; 
    &lt;span&gt;${player.name}&lt;/span&gt; 
  &lt;/div&gt; 
  &lt;div&gt; 
    &lt;span&gt;${player.position}&lt;/span&gt; 
  &lt;/div&gt; 
  &lt;div&gt; 
    &lt;span&gt;${player.number}&lt;/span&gt; 
  &lt;/div&gt; 
&lt;/div&gt;;
`
document.getElementById('player').innerHTML = html;</code></pre>
        <p>
          Writing a full scale application with techniques like above quickly
          become cumbersome and difficult to read. Thanks to Vue, HTML
          Templating becomes a lot easier, as you will see as you continue this
          project. Look at the example below to see the Vue approach.
        </p>
        <h5>Vue Approach</h5>
        <pre><code class="language-markup">&lt;div class="player-card"&gt;
    &lt;div&gt;
        &lt;img :src="player.photo" /&gt;
    &lt;/div&gt;
    &lt;div&gt;
        &lt;span&gt;{{state.player.name}}&lt;/span&gt;
    &lt;/div&gt;
    &lt;div&gt;
        &lt;span&gt;{{state.player.position}}&lt;/span&gt;
    &lt;/div&gt;
    &lt;div&gt;
        &lt;span&gt;{{state.player.number}}&lt;/span&gt;
    &lt;/div&gt;
&lt;/div&gt;</code></pre>
        <p>
          What is nice about this approach is you don't have to leave your html
          while you are trying to figure out how you want something to look.
          Also you never have to write using string concatenation and keep track
          of all the '""' + '"". It is similar to string interpolation as we did
          above, but allows writing real html with full syntax highlighting and
          formatting.
        </p>
        <p>
          You might not see the power of these expressions yet, but thats okay.
          Try the exercises below (located in the Expressions Excercise.vue) and
          then move on to the next section.
        </p>
      </div>
      <exercise></exercise>
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
import { onMounted, reactive } from "vue";
import Exercise from "../components/ExpressionsExercise.vue";
export default {
  name: "expressions",
  setup() {
    // @ts-ignore
    onMounted(() => Prism.highlightAll())
    
    const state = reactive({
      val: "{{ Evaluate Javascript Code }}",
      player: {
        name: "{{ state.player.name }}",
        position: "{{ state.player.position }}",
        number: "{{ state.player.number }}",
      },
      handleEg: "{{2 + 2}}",
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