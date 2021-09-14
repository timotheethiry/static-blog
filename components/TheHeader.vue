<template>
    <div class="flex-1 flex flex-col">
        <nav class="px-4 flex justify-between bg-white h-16 border-b-2">

            <!-- top bar left -->
            <ul class="flex items-center">
                <!-- add button -->
                <li class="h-6 mr-6">
                    <nuxt-link class="" to="/">Accueil</nuxt-link>
                </li>
                <li class="h-6 mr-6">
                    <nuxt-link class="" to="/about">Who is this guy ?</nuxt-link>
                </li>
            </ul>

            <ul class="flex items-center">
                <!-- add button -->
                <li>
                    <h1 class="pl-8 lg:pl-0 text-gray-700">Backpack with me!</h1>
                </li>
            </ul>

            <!-- to bar right  -->
            <ul class="flex items-center">

                <li class="pr-6">
                </li>
                <li class="h-10 w-10">
                    <img
                        class="h-full w-full rounded-full mx-auto"
                        src="https://images.unsplash.com/19/nomad.JPG?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=988&q=80"
                        alt="profile man" />
                </li>

            </ul>
        </nav>
    </div>
</template>