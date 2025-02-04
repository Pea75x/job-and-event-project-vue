<template>
  <div class='pie-container' v-if="Object.keys(jobData).length > 0">
    <h1 class='title'>{{language}}</h1>
    <div class='insights-container'>
      <div class='insight'>
        <img :src="`data:image/png;base64,${jobData['general_skills']}`" width="400"/>
        <p class='pie-text'>In demand general skills</p>
      </div>
      <div class='insight'>
        <img :src="`data:image/png;base64,${jobData['technical_skills']}`" width="400"/>
        <p class='pie-text'>In demand technical skills</p>
      </div>
    </div>
  </div>
  <div class="results-container">
    <div v-if="!!loading" class="loading">Searching for jobs...</div>
    <h1 class='title' v-if="Object.keys(jobData).length > 0">Jobs</h1>
    <div v-for="job, index in jobData.jobs" :key="index" class='job-container' :class="index < jobData.jobs.length - 1 && 'border-bottom'">
      <h1 class='job-title'><a :href="job.link" target="_blank">{{job['job-title']}}</a></h1>
      <h2 class='company-title'>{{job.company}}</h2>
      <h3 class='level'>Level: {{job.level}}</h3>
      <div class='skills-section'>
        <h4 class='skills-title'>Techinical Skills:</h4>
        <div class='skills-container'>
          <div v-for="skill in job['technical_skills']" :key="skill" class='skill'>
            {{skill}}
          </div>
        </div>
        <h4 class='skills-title'>General Skills:</h4>
        <div class='skills-container'>
          <div v-for="skill in job['general_skills']" :key="skill" class='skill'>
            {{skill}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['jobData', 'language', 'loading']
  }
</script>

<style>
  .results-container {
    width: 90%;
    background-color: #cce2cc;
    margin: auto;
    border-radius: 20px 20px 0 0;
    min-height: calc(100vh - 315px);
    position: relative;
  }

  @media (max-width: 900px) {
    .results-container {
      margin-top: 10px;
      min-height: calc(100vh - 375px);
    }
  }
  .title {
    font-weight: bold;
    padding: 10px;
  }
  .job-container {
    padding: 20px;
    margin: 0 30px;
  }
  .job-title {
    font-size: 22px;
    margin: 0;
    font-weight: 600;
  }
  a:link {
    color: black;
    font-size: 22px;
    margin: 0;
    font-weight: 600;
  }
  .job-title:hover {
    font-size: 23px;
  }
  .company-title {
    margin: 0;
    font-size: 22px;
    font-weight: 500;
  }
  .level {
    margin: 0;
    font-size: 17px;
    border: 2px solid #5a947a;
    display: inline-block;
    padding: 1px 10px;
    border-radius: 5px;
  }
  .skills-title {
    margin: 0;
    font-size: 14px;
  }
  .skills-section {
    margin-top: 10px;
  }
  .skills-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }
  .skill {
    background-color: #5a947a;
    color:#cce2cc;
    border-radius: 15px;
    padding: 1px 15px;
    margin: 2px;
  }
  .border-bottom {
    border-bottom: 1px solid #5a947a;
  }
  .insights-container {
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-wrap: wrap;
  }
  .pie-text {
    position: absolute;
    width: 100%;
    font-weight: 500;
    bottom: 0;
  }
  .insight {
    position: relative;
    margin-bottom: 20px;
  }
  .loading {
    position: absolute;
    top: 20%;
    width: 100%;
    animation-name: loading-spinner;
    animation-duration: 2s;
    animation-iteration-count: infinite;
    animation-direction: alternate-reverse;
}
@keyframes loading-spinner {
  from {
    font-weight:900;
  }
  to {
    font-weight: 400;
    }
}
</style>
