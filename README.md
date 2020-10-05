# suggestkit-vue
An implementation of SuggestKit in Vue.

## How to use
To use this, you will firstly want to import the library from `suggestkit-vue`:
```js
import SuggestKit from "suggestkit-vue";
```

We can then add it as a component:
```js
components: {
    SuggestKit,
    // ...
},
```

From here, we will want to structure our data. Note that `info` is what will be returned in the array which will be updated, and `key` is what will be what is used as the key for the suggestion:
```js
const suggestions = [
    {
        key: "hello",
        info: {
            title: "Hello World",
            description: "Demo",
        },
    },
    {
        key: "sammy",
        info: {
            title: "Sammy Shark!",
            description: "Sammy!",
        },
    },
];
```

From here, we can structure our components data:
```js
data() {
    return {
        suggestions,
        suggestionsToRender: [],
        text: "",
    }
},
```

From here, we simply can setup SuggestKit. The template will be directly under the text area:
```vue
<SuggestKit
    :suggestions="this.$data.suggestions" placeholder="Type here to get suggestions!"
    @on-suggestions-change="suggestionsToRender => this.$data.suggestionsToRender = suggestionsToRender"
    @on-text-change="text => this.$data.text = text"
>
    <template>
        <div v-for="(suggestion, index) in this.$data.suggestionsToRender" v-bind:key="index">
            <hr />
            <h1 class="title">{{suggestion.title}}</h1>
            <h2 class="subtitle">{{suggestion.description}}</h2>
        </div>
    </template>
</SuggestKit>
```

## Demo
There is a demo included (see `demo.vue`) which contains a simple typearea and the keys `hello` and `sammy`. To use the demo, sinply run `npm i` and then `npm run demo`. 
