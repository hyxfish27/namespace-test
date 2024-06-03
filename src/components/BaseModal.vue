<template>
    <div v-show="isShow" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                {{ title }}
            </div>
        <slot></slot>

        <div class="modal-footer">
            <button class="btn btn--confirm" @click="onConfirm">Confirm</button>
            <button class="btn btn--cancel" @click="onCancel">Cancel</button>
        </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'BaseModal',

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
            this.$emit('confirm');
        },

        onCancel() {
            this.$emit('cancel');
        }
    }
}

</script>

<style scoped>
.modal {
    position: relative;
    width: 400px;
    height: 300px;
    padding: 24px;
    background-color: #c1cad9;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.modal-content {
    position: relative;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

}

.modal-header {
    margin-bottom: 24px;
}

.modal-footer {
    display: flex;
    justify-content: center;
}

.btn {
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    outline: none;
    border: none;
}

.btn:hover {
    opacity: 0.8;
}

.btn--confirm {
    background-color: #737c75;
    color: #fff;
    margin-right: 24px;
}

.btn--cancel {
    background-color: #ceddd8;
    color: #fff;
}
</style>