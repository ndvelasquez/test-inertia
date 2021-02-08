<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Módulo de notas
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="px-4 sm:px-0">
                            <h3 class="text-lg text-gray-900">Editar nota</h3>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form @submit.prevent="submit">
                                <label for="title" class="block font-medium text-sm text-gray-700">
                                    Título
                                </label>
                                <input type="text" class="form-input w-full rounded-md shadow-sm" v-model="form.title">
                                <label for="title" class="block font-medium text-sm text-gray-700">
                                    Descripción
                                </label>
                                <textarea class="form-input w-full rounded-md shadow-sm" rows="8" v-model="form.description"></textarea>
                                <button class="rounded bg-blue-500 hover:bg-700 text-white font-bold py-2 px-4">Guardar Cambios</button>
                            </form>
                                <div class="my-2">&nbsp;</div>
                            <inertia-link :href="route('notes.index')">
                                Volver
                            </inertia-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout'

    export default {
        components: {
            AppLayout,
        },
        props: {
            note: Object,
        },
        data () {
            return {
                form: {
                    title: this.note.title,
                    description: this.note.description
                }
            }
        },
        methods: {
            submit() {
                this.$inertia.put(this.route('notes.update', this.note.id), this.form)
            }
        }
    }
</script>
