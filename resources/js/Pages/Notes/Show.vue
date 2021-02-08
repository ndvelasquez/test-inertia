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
                            <h3 class="text-lg text-gray-900">Detalle de la nota</h3>
                            <h3 class="text-lg text-gray-900">{{note.title}}</h3>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <p>{{ note.description }}</p>

                            <hr class="my-6">
                            
                            <div class="flex justify-between">
                                <inertia-link :href="route('notes.index')">
                                Volver
                                </inertia-link>
                                <a href="#" @click.prevent="destroy" class="bg-red-500 hover:bg-red-700 text-white font-bold rounded py-2 px-4">
                                Eliminar nota
                                </a>
                            </div>
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
        methods: {
            destroy() {
                if (confirm('¿Desea eliminar la nota?')) {
                    this.$inertia.delete(this.route('notes.destroy', this.note.id))
                }
            }
        }
    }
</script>
