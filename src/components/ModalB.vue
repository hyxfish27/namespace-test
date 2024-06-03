<template>
    <base-modal :isShow="isShow" :title="title" @confirm="onConfirm" @cancel="onCancel">
        <slot/>
    </base-modal>
</template>

<script>
import BaseModal from './BaseModal.vue'

export default {
    name: 'ModalB',

    components: {
        BaseModal
    },

    props: {
        isShow: {
            type: Boolean,
            default: false
        },

        title: {
            type: String,
            default: ''
        }
    },

    methods: {
        onConfirm() {
            this.$emit('confirm')
        },

        onCancel() {
            this.$emit('cancel')
        }
    }
}

</script>