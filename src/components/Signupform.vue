<template>
  <form class="mt-8" @submit.prevent="handleSubmit">
    <div class="">
      <!-- email -->
      <div>
        <label for="email" class="sr-only">Email</label>
        <input
          id="email"
          name="email"
          type="email"
          autocomplete="email"
          required=""
          class="rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-2xl"
          placeholder="Email"
          v-model="email"
        />
      </div>

      <!-- password -->
      <div class="mb-4">
        <label for="password" class="sr-only">Password</label>
        <input
          id="password"
          name="password"
          type="password"
          autocomplete="current-password"
          required
          class="rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-2xl"
          placeholder="Password"
          v-model="password"
        />
        <div v-if='passwordError' class="text-red-500 font-semibold">{{ passwordError }}</div>
      </div>

      <!-- select -->
      <div class="mt-4 mb-8">
        <select
          name="role"
          id="role"
          class="mt-4 rounded relative block px-3 pr-8 mr-8 py-2 border border-gray-300 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-xl"
          v-model="role"
        >
          <option value="designer">W.Designer</option>
          <option value="developer">W.Developer</option>
        </select>
      </div>

      <!-- checkbox -->
      <div class="flex items-center mt-8">
        <input
          id="terms"
          name="terms"
          type="checkbox"
          required
          class="h-6 w-6 text-indigo-600 border-gray-300 rounded focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-2xl"
          v-model="terms"
        />
        <label for="terms" class="ml-2 block text-xl text-gray-900">
          I Accept the terms
        </label>
      </div>

      <!-- array of checkboxes -->
      <div
        class="flex mt-8 flex-wrap flex-col justify-start items-start content-start"
      >
        <div class="mb-1 flex flex-row flex-nowrap items-center">
          <input
            name="preference"
            type="checkbox"
            class="h-4 w-4 bg-indigo-600 text-indigo-600 border-gray-300 rounded focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-lg"
            v-model="preferences"
            value="music"
          />
          <label
            for="preferences"
            class="ml-2 text-md inline-block text-gray-900"
          >
            Music
          </label>
        </div>

        <div class="mb-1 flex flex-row flex-nowrap items-center">
          <input
            name="preference"
            type="checkbox"
            class="h-4 w-4 bg-indigo-600 text-indigo-600 border-gray-300 rounded focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-lg"
            v-model="preferences"
            value="art"
          />
          <label
            for="preferences"
            class="ml-2 text-md inline-block text-gray-900"
          >
            Art
          </label>
        </div>

        <div class="mb-1 flex flex-row flex-nowrap items-center">
          <input
            name="preference"
            type="checkbox"
            class="h-4 w-4 bg-indigo-600 text-indigo-600 border-gray-300 rounded focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-lg"
            v-model="preferences"
            value="dancing"
          />
          <label
            for="preferences"
            class="ml-2 text-md inline-block text-gray-900"
          >
            Dancing
          </label>
        </div>
      </div>

       <!-- skills -->
       <input id="text"
          name="tempSkill"
          type="text"
          autocomplete="text"
          class="mt-8 rounded-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 text-xl"
          placeholder="your skills - press comma to add"
          v-model="tempSkill"
          @keyup="addSkill">

        <!-- list skills -->
        <div class="skills mt-6 text-left">
            <div class="group relative inline-block bg-gray-200 rounded-md m-1 p-2 pr-5 cursor-pointer" v-for="skill in skills" :key="skill" @click="deleteSkill(skill)">
                {{ skill }} <span class="absolute top-1 right-1 text-xs text-gray-400 group-hover:text-gray-600 transition duration-200">✕</span>
            </div>
        </div>
    </div>


    <div>
      <button
        type="submit"
        class="mt-12 group relative w-full flex justify-center py-2 px-4 border border-transparent text-2xl font-bold rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
      >
        Sign up
      </button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      preferences: [],
      tempSkill: "",
      skills: [],
      passwordError: ''
    }
  },
  methods: {
    addSkill(e) {
        if(e.key === ',' && this.tempSkill.length > 0) {
            if(!this.skills.includes(this.tempSkill)) {
                let temp = this.tempSkill.split(',')
                temp = String(temp[0])
                this.skills.push(temp)
            }
            this.tempSkill = ''
        }
    },
    deleteSkill(skill) {
        this.skills = this.skills.filter(item => skill !== item)
    },
    handleSubmit() {
        this.passwordError = this.password.length > 5 ? '' : 'Password must be at least 6 chars long'

        if(!this.passwordError) {
            console.log('form submitted...')
            console.log('Email: ', this.email)
            console.log('Password: ', this.password)
            console.log('Role: ', this.role)
            console.log('Terms accepted: ', this.terms)
            console.log('Preferences: ', this.preferences)
            console.log('Skills: ', this.skills)
        } else {
            console.log('oops! error')
        }
    }
  }
}
</script>

<style></style>
