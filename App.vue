<template>
  <div>
    <!-- the username data property is defined with the value of "Joe" -->
    <h3>Text Interpolation</h3>
    <p>Good afternoon, {{ username }}</p>

    <!-- v-html on the <p> element binds it to the htmlContent data property. 
      The htmlContent contains the raw HTML as a string, meaning it will render the string formatted HTML." -->
    <h3>Raw HTML</h3>
    <p v-html="htmlContent"></p>

    <!-- the username data property is defined with the value of "Joe" -->
    <h3>Attribute Bindings</h3>
    <button :id="buttonId">Click here</button>

    <!-- the curly brackets display the value of the data property. 
      The computedMessage displays the computed property, which converts 'message'
      to uppercase. The click bind changes the value of 'message' -->
    <div>
    <h3>Javascript expressions inside syntax</h3>
    <p>Computed Message: {{ computedMessage }}</p>
    <button @click="changeMessage">Change Message</button>
  </div>

    <!-- The numbers array and result data is defined. In the methods section 
      'calculate sum' is defined. The 'numbers' array is calculated and assigns
      the result data property -->
      <h3>Methods</h3>
    <p>Result: {{ result }}</p>
    <button @click="calculateSum">Calculate Sum</button>
    
    <!-- the ref function defines a reactive variable 'count' with a value of 0.
      the incrementCount method increments the count cariable when the button is clicked. -->  
      <h3>Reactivity Fundamentals</h3>
    <p>Count: {{ count }}</p>
    <button @click="incrementCount">Increment</button>

    <!-- Displays the computed property reversedMessage -->
    <h3>Computed properties</h3>
    <p>Reversed Message: {{ reversedMessage }}</p>

    <!-- Bind the CSS class 'highlight' conditionally -->
    <h3>Binding HTML Class</h3>
    <p :class="{ 'highlight': isHighlighted }">Conditional Highlighted Text</p>

    <!-- Bind the text color dynamically using v-bind:style -->
    <h3>Binding Inline Styles</h3>
    <p :style="{ color: textColor }">Dynamic Text Color</p>

    <!-- Iterate over an object using v-for and display its key-value pairs -->
    <h3>v-for with an object</h3>
    <ul>
      <li v-for="(value, key) in myObject" :key="key">{{ key }}: {{ value }}</li>
    </ul>

     <!-- Iterate over a range of numbers using v-for -->
     <h3>v-for with a range</h3>
    <ul>
      <li v-for="number in range(1, 5)" :key="number">{{ number }}</li>
    </ul>

     <!-- Use v-for within a <template> to conditionally render items -->
      <h3>v-for on template</h3>
      <template v-for="(item, index) in items" :key="index">
      <p v-if="item.show">{{ item.text }}</p>
    </template>

    <!-- Use v-for with v-if to conditionally render items -->
    <h3>V-for with v-if</h3>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <p v-if="item.show">{{ item.text }}</p>
      </li>
    </ul>
    
    <!-- Use v-for with a custom component to render items -->
    <h3>V-for with a component</h3>
    <div v-for="(item, index) in items" :key="index">
      <item-component :item="item"></item-component>
    </div>

    <!-- Use @click for inline click event handling -->
    <h3>Inline Handlers</h3>
    <button @click="handleButtonClick">Click me</button>

    <!-- Use @click to call a method handler -->
    <h3>Method Handlers</h3>
    <button @click="handleButtonClick">Click me</button>

     <!-- Input type: text -->
     <h3>Form Input Bindings (v-model)</h3>
     <label for="text-input">Text Input:</label>
    <input type="text" id="text-input" v-model="textInput" />

    <p>Text Input Value: {{ textInput }}</p>

    <!-- Input type: checkbox -->
    <label for="checkbox-input">Checkbox Input:</label>
    <input type="checkbox" id="checkbox-input" v-model="checkboxInput" />

    <p>Checkbox Input Value: {{ checkboxInput }}</p>

    <!-- Input type: radio -->
    <label for="radio-input1">Radio Input 1:</label>
    <input type="radio" id="radio-input1" value="option1" v-model="radioInput" />
    <label for="radio-input2">Radio Input 2:</label>
    <input type="radio" id="radio-input2" value="option2" v-model="radioInput" />

    <p>Radio Input Value: {{ radioInput }}</p>

    <!-- Select -->
    <label for="select-input">Select Input:</label>
    <select id="select-input" v-model="selectInput">
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
      <option value="option3">Option 3</option>
    </select>

    <p>Select Input Value: {{ selectInput }}</p>

    <!-- Textarea -->
    <label for="textarea-input">Textarea Input:</label>
    <textarea id="textarea-input" v-model="textareaInput"></textarea>

    <p>Textarea Input Value:</p>
    <pre>{{ textareaInput }}</pre>

    <!-- Input type: text with .lazy modifier -->
    <h3> More Form Input Bindings (v-model)</h3>
    <label for="lazy-text-input">Lazy Text Input:</label>
    <input type="text" id="lazy-text-input" v-model.lazy="lazyTextInput" />

    <p>Lazy Text Input Value: {{ lazyTextInput }}</p>

    <!-- Input type: text with .number modifier -->
    <label for="number-input">Number Input:</label>
    <input type="text" id="number-input" v-model.number="numberInput" />

    <p>Number Input Value: {{ numberInput }}</p>

    <!-- Input type: text with .trim modifier -->
    <label for="trim-text-input">Trim Text Input:</label>
    <input type="text" id="trim-text-input" v-model.trim="trimTextInput" />

    <p>Trim Text Input Value: {{ trimTextInput }}</p>

    <!-- Display a message when the 'username' data property changes -->
    <h3>Watchers</h3>
    <p>Username: {{ username }}</p>

    <!-- Input to change the 'username' data property -->
    <input type="text" v-model="username" />

    <!-- Use ChildComponent and pass a user prop -->
    <h3>Components</h3>
    <ChildComponent :user="parentUser" @custom-event="handleCustomEvent" >

    <!-- Display custom event data -->
    <p>Custom Event Data: {{ customEventData }}</p>

    <!-- Slot content -->
    <p>This is content being passed through a slot.</p>
    </ChildComponent>


    <div>
    <!-- Router links -->
    <h3>Router</h3>
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
    <router-view></router-view> 
    </div>


  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';
import ItemComponent from './ItemComponent.vue';
import ChildComponent from './ChildComponent.vue';

// Define a data property for the 'id' attribute
const buttonId = 'my-button';

// Define a computed property using JavaScript expression inside template
const computedMessage = computed(() => message.value.toUpperCase());


// Defines a reactive variable using ref
const count = ref(0);

// Defines a method to increment the count
const incrementCount = () => {
  count.value++;
};

// Define the message data property
const message = ref("Welcome to SIT120");
const changeMessage = () => {
  message.value = "Good Afternoon!";
};

// Create a computed property to reverse the message
const reversedMessage = computed(() => {
  return message.value.split('').reverse().join('');
});

// Define a reactive variable for the class binding
const isHighlighted = ref(true);

// Define a reactive variable for the text color binding
const textColor = ref('red');

// Define an object to iterate over using v-for
const myObject = {
  firstName: 'Joe',
  lastName: 'Mac',
  age: 25,
};

// Define an array of items with a show property for conditional rendering
const items = [
  { text: 'example 1', show: true },
  { text: 'example 2', show: false },
  { text: 'example 3', show: true },
];

// Define a function to generate a range of numbers
function range(start, end) {
  return Array.from({ length: end - start + 1 }, (_, index) => start + index);
}

// Define a method to handle button click
const handleButtonClick = () => {
  // Click event happens here
  console.log("Button clicked!");
};

// Define reactive variables for form inputs
const textInput = ref('');
const checkboxInput = ref(false);
const radioInput = ref('');
const selectInput = ref('option1');
const textareaInput = ref('');

// Define reactive variables for form inputs with modifiers
const lazyTextInput = ref('');
const numberInput = ref(0);
const trimTextInput = ref('');

// Define a reactive variable for watching
const username = ref("JoeMac");

// Create a watcher to react to changes in the 'username' variable
watch(username, (newValue, oldValue) => {
  // Custom logic to run when 'username' changes
  console.log(`Username changed from "${oldValue}" to "${newValue}"`);
});

// Define the data properties
const parentUser = ref({
  name: 'Joe Mac', 
  age: 25, 
});

// Define the reactive variable to store custom event data
const customEventData = ref('');

// Method to handle the custom event
const handleCustomEvent = (data) => {
// Update the customEventData with the data received from the custom event
customEventData.value = data;
};


</script>

<script>


export default {
  
  data() {
    return {
      username: "Joe",
      htmlContent: "<strong>This is <em>raw</em> HTML content.</strong>",
      buttonId: "my-button",
      message: "Good Morning!",
      numbers: [1, 2, 3],
      result: null,
      items: [
        { text: 'Item 1' },
        { text: 'Item 2' },
        { text: 'Item 3' },
      ],
    };
  },
  computed: {
    computedMessage() {
      return this.message.toUpperCase();
    },
  },
  methods: {
    changeMessage() {
      this.message = "Good Afternoon!";
    },
    calculateSum() {
      // The method calculates the sum of the numbers array
      this.result = this.numbers.reduce((acc, num) => acc + num, 0);
    },
    // Define a method handler for button click
    handleButtonClick() {
      // Click event happens here
      console.log("Button clicked!");
    },
  },
  
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
 
  
  };
</script>

<style>
h3 {
  font-size: larger;
  text-align: center;
  font-family: Arial, Helvetica, sans-serif;
  color: green;
  margin-bottom: 8%;
  margin-top: 3%;
}

.highlight {
  background-color: aqua;
  font-weight: bolder;
}
</style>