<template>
    <lightbox name="releasenotes" no-fullscreen no-title-hide>
        <h1>LSSM V.4: {{ $t('modules.releasenotes.name') }}</h1>
        <div v-for="note in notes" :key="note.version" class="note">
            <h4>
                <b>{{ note.version }}</b
                >:
                {{ note.title }}
            </h4>
            <div v-html="note.description"></div>
        </div>
    </lightbox>
</template>

<script lang="ts">
import Vue from 'vue';
import {
    DefaultData,
    DefaultMethods,
    DefaultComputed,
} from 'vue/types/options';
import { ReleaseNoteProps } from 'typings/modules/Releasenotes';

export default Vue.extend<
    DefaultData<Vue>,
    DefaultMethods<Vue>,
    DefaultComputed,
    ReleaseNoteProps
>({
    name: 'releasenotes',
    components: {
        Lightbox: () =>
            import(
                /* webpackChunkName: "components/lightbox" */ '../../components/lightbox.vue'
            ),
    },
    props: {
        notes: {
            type: Array,
            required: true,
        },
    },
});
</script>

<style scoped lang="sass">
.note
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2)
    transition: 0.3s
    border-radius: 5px
    padding: 1rem
    &:hover
        box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2)
</style>
