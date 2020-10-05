<template>
    <div>
        <textarea class="textarea" :placeholder="this.$props.placeholder" v-model="text"></textarea>
        <slot></slot>
    </div>
</template>

<script>
    import suggestKit from "@jakemakesstuff/suggestkit";

    export default {
        name: "SuggestKit",
        props: {
            suggestions: Array,
            placeholder: String,
        },
        data() {
            return {
                search: suggestKit(this.$props.suggestions),
                text: "",
            }
        },
        watch: {
            suggestions() {
                this.$data.search = suggestKit(this.$props.suggestions);
            },
            text() {
                this.$emit("on-suggestions-change", this.$data.search(this.$data.text));
                this.$emit("on-text-change", this.$data.text);
            },
        }
    }
</script>
