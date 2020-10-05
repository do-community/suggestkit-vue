<template>
    <div className="container" style="padding-top: 1%;">
        <p>The current value of text is: {{text}}</p>
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
    </div>
</template>

<script>
    import SuggestKit from "./src";

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

    export default {
        name: "Demo",
        components: {
            SuggestKit,
        },
        data() {
            return {
                suggestions,
                suggestionsToRender: [],
                text: "",
            }
        },
    }
</script>
