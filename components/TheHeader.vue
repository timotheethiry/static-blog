<template>
    <div>
        <nav class="px-4 flex flex-wrap justify-center sm:justify-between bg-white h-16 border-b-2">

            <!-- top bar left -->
            <ul class="flex items-center">
                <!-- add button -->
                <li class="">
                    <h1 class="text-gray-700">Backpack with me!</h1>
                </li>
            </ul>

            <ul class="flex items-center sm:mx-auto transform sm:-translate-x-11">
                <!-- add button -->
                <li class="h-6 mx-6 sm:ml-0 sm:mr-6">
                    <nuxt-link class="" to="/">Accueil</nuxt-link>
                </li>
                <li class="h-6 mr-6 sm:m-0">
                    <nuxt-link class="" to="/about">Who is this guy ?</nuxt-link>
                </li>
            </ul>

            <!-- to bar right  -->
            <ul class="hidden sm:flex items-center ">
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