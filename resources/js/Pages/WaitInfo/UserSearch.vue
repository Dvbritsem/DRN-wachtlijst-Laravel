<template>
    <div class="py-6">
        <div class="max-w-7xl mx-auto">
            <div class="bg-white overflow-hidden shadow sm:rounded-lg border-b">
                <jet-form-section2 @submitted="searchUser">
                    <template #title>
                        Zoek een lid
                    </template>

                    <template #description>
                        Zoek hier op de naam van het lid.
                    </template>

                    <template #form>
                        <div class="col-span-6 sm:col-span-4">
                            <jet-label for="name" value="Naam" />
                            <jet-input id="name" name="name" type="text" v-model="form.name" class="mt-1 block w-full"/>
                        </div>
                    </template>

                    <template #actions>
                        <jet-button :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Zoeken
                        </jet-button>
                    </template>
                </jet-form-section2>
            </div>
        </div>
    </div>
</template>

<script>
    import JetActionMessage from './../../Jetstream/ActionMessage'
    import JetButton from './../../Jetstream/Button'
    import JetFormSection2 from './../../Jetstream/FormSection2'
    import JetInput from './../../Jetstream/Input'
    import JetInputError from './../../Jetstream/InputError'
    import JetLabel from './../../Jetstream/Label'

    export default {
        components: {
            JetActionMessage,
            JetButton,
            JetFormSection2,
            JetInput,
            JetInputError,
            JetLabel,
        },

        props: ['users'],

        methods: {
            searchUser() {
                this.form.post('/user/wachtlijst', {
                    preserveScroll: true
                })
            },
        },

        data() {
            return {
                form: this.$inertia.form({
                    name: this.name,
                })
            }
        },
    }
</script>
