<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ danger: theme === 'danger'}">
            <slot>Default content</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['theme'],   
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>

<style>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }
    .modal h1 {
        color: green;
        border: 0;
    }
    .notglobal p {
        font-style: normal;
    }
    .modal.danger {
        background: red;
        color: white;
    }
    .modal.danger h1 {
        color: white;
    }
</style>