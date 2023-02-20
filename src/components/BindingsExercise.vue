<template>
  <div class="binding-exercise container">
    <div class="row">
      <div class="col-12">
        <div class="border p-1">
          <h5>One Way Data Binding</h5>
          <p>
            Use the property "message" on the data object in our component for
            one way data binding to display the message in our template. Replace
            the comment with the property name "state.message" in the curlies.
            Check out what happens below. Now go change the value of message in
            our components script area and see what happens.
          </p>
          <p>{{state.message}}</p>
        </div>
        <div class="border p-1">
          <h5>Two Way Data Binding</h5>
          <p>
            Use a v-model to bind an input value from our html to a property in
            the components data object. Then reference that data property in the
            html to display the value. Notice Vue will rerender each time the
            value changes.
          </p>
          <!-- add a v-model to this input that will reference "myName" within the state object-->
          <input v-model="state.myName" />
          <!-- reference "myName" from the state -->
          <p class="active">{{state.myName}}</p>
        </div>
        <div class="border p-1">
          <h5>Class Binding</h5>
          <p>
            Use class binding to reference a property(isActive) in the
            components data object to determine when to add the class to the
            elements class list. Then change the value of that data
            property(isActive) to true. Notice Vue will rerender each time the
            value changes.
          </p>
          <div class="active">
            <!-- add a class binding attribute to the p tag that references the state isActive value -->
            <p>This text will get WILD AND WACKY on active</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import { reactive } from "vue";
export default {
  name: "binding-exercises",
  setup() {
    // NOTE typically state will be abstracted to a global AppState
    const state = reactive({
      //create a property called myName and set its value to "type your name here"
      message: "me may ma mo mu me may ma mo me may ma mo mu me may ma mo me may ma mo mu",
      //change isActive to true
      isActive: false,
    });
    return { state };
  },
};
</script>


<style scoped>
.inactive {
  color: rgb(0, 0, 0);
}

.active {
  animation: color-change 1s infinite;
}
@keyframes color-change {
  0% { color: #ff00a6; }
  50% { color: rgb(38, 184, 33); }
  100% { color: #ff00a6; }
}
</style>