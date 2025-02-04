<template>
  <div class='home-header'>
    <h1>Jobhunter</h1>
    <h2>Finding developer jobs in London based on tech stack</h2>
  </div>
  <div class='home-body'>
    <div>Popular languages and frameworks</div>
    <div class='language-button-container'>
      <Button 
        v-for="language in languages"
        @click-button="pickLanguage"
        :key="language"
        button-class='rounded-button'
        :text="language"
        />
    </div>
    <div class="search-container">
      <div class='search-boxes'>
        <input :v-model="searchText" type='text' class='search-input' placeholder='Search language/framework...'/>
      </div>
      <div class='search-boxes'>
        <Button text='Search' button-class='main-button' @click="pickLanguage"/>
      </div>
    </div>
    <ResultsPage/>
  </div>
</template>

<script>
import Button from './Button.vue';
import ResultsPage from './ResultsPage.vue'

export default {
  components: {
    Button,
    ResultsPage
  },
  data() {
    return {
      languages: ['React', 'Ruby', 'Python', 'Java', 'PHP'],
      searchText: ""
    }
  },
  created() {
    
  },
  methods: {
    pickLanguage(language) {
      console.log(language)
    },

  }
}
</script>

<style scoped>
* {
  text-align: center;
}
.home-header {
  padding: 20px;
  width: 70%;
  margin: auto;
  border-bottom: 1px solid grey;
}
.home-body {
  margin-top: 20px;
  font-size: 17px;
}
h1 {
  font-weight: 500;
  font-size: 40px;
}
.search-input {
  font-weight: bold;
  width: 300px;
  padding: 15px 0;
  outline: 1px solid black;
  font-size: 15px;
  border-radius: 10px;
}
.search-boxes {
  margin: 10px 5px;
}
.language-button-container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  width: 65%;
  margin: 10px auto;
}
.search-container {
  display: flex;
  align-items: center;
  justify-content: center;
}
.search-input {
  border-radius: 5px;
  border: 1px solid black;
}

@media (max-width: 900px) {
  .home-header {
    padding: 20px;
    width: 90%;
    margin: auto;
  }
  .language-button-container {
    width: 90%;
  }
  .search-container {
    flex-direction: column;
  }
  .search-boxes {
    margin: 5px;
  }
}

@media (max-width: 500px) {
  .language-button-container{
    flex-wrap: wrap;
  }
}
</style>
