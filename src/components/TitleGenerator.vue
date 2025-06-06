<template>
  <div class="wrapper uk-container uk-section-large">
    <h2 class="uk-heading-small uk-text-center">Capstone Title Generator</h2>
    <p class="uk-text-center uk-text-normal uk-text-lead">Get a project-worthy title related to your field in one click!</p>

    <div class="generator-layout uk-flex uk-flex-wrap uk-flex-between uk-margin-large-top">
      <!-- Input Section -->
      <div class="uk-card uk-card-body input-section">
        <div class="uk-margin">
          <label class="uk-form-label">Select a topic or scope:</label>
          <select class="uk-select" v-model="topic">
            <option disabled value="">Choose Topic</option>
            <option v-for="(item, key) in titles" :key="key">{{ key }}</option>
          </select>
        </div>

        <div class="uk-margin">
          <label class="uk-form-label">Select complexity level:</label>
          <select class="uk-select" v-model="level">
            <option disabled value="">Select Level</option>
            <option>Beginner</option>
            <option>Average</option>
            <option>Advanced</option>
          </select>
        </div>

        <button class="uk-button uk-margin-top uk-width-1-1 generate-button uk-flex uk-flex-middle uk-flex-center" @click="generateTitle">
          <i class="fas fa-sync-alt uk-margin-small-right" style="font-size: .9rem;"></i>
          {{ generatedTitle ? 'Generate Again' : 'Generate' }}
        </button>
      </div>

      <!-- Output Section -->
      <div class="uk-card uk-card-body output-section">
        <div class="uk-text-center output-wrapper uk-flex uk-flex-middle uk-flex-center">
          <div>
            <h3 v-if="generatedTitle" class="uk-card-title uk-text-bold">{{ generatedTitle }}</h3>
            <p v-else class="uk-text-muted">Your generated title will appear here</p>
            <p v-if="generatedDescription">{{ generatedDescription }}</p>
          </div>
        </div>
      </div>
    </div>

    <div class="uk-text-center uk-padding-large uk-padding-remove-bottom">
      <p>Developed by <strong>Francis Vino</strong></p>
      <div style="margin-top: 10px; font-size: 1.4rem;">
        <a href="https://instagram.com/flvinonovi" target="_blank" class="uk-icon-button" style="margin: 0 8px;" aria-label="Instagram">
          <i class="fab fa-instagram"></i>
        </a>
        <a href="https://facebook.com/flvinonovi" target="_blank" class="uk-icon-button" style="margin: 0 8px;" aria-label="Facebook">
          <i class="fab fa-facebook"></i>
        </a>
        <a href="https://linkedin.com/in/francis-loyd-vino-3b5086305" target="_blank" class="uk-icon-button" style="margin: 0 8px;" aria-label="LinkedIn">
          <i class="fab fa-linkedin"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import titles from '@/data/titles'

export default {
  data() {
    return {
      titles,
      topic: '',
      level: '',
      generatedTitle: '',
      generatedDescription: ''
    }
  },
  methods: {
    generateTitle() {
      if (!this.topic || !this.level) {
        window.alert('Please select a topic and level')
        return
      }

      const selected = this.titles[this.topic][this.level]
      if (selected && selected.length) {
        const random = selected[Math.floor(Math.random() * selected.length)]
        this.generatedTitle = random.title
        this.generatedDescription = random.description
      } else {
        this.generatedTitle = 'No titles available'
        this.generatedDescription = ''
      }
    }
  }
}
</script>


<style scoped lang="scss">
h2 {
  background: linear-gradient(to right, #7c3aed, #10b981);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-family: 'Inter', sans-serif;
  font-weight: 800;
  font-size: 3.4rem;

  @media (max-width: 768px) {
    font-size: 2.8rem;
  }

  @media (max-width: 480px) {
    font-size: 2.3rem;
  }
}

.uk-text-lead {
  font-size: 1.3rem;

  @media (max-width: 480px) {
    font-size: 1.1rem;
  }
}

.generator-layout {
  gap: 2rem;
  flex-wrap: wrap;

  @media screen and (max-width: 1060px) {
    flex-direction: column;
  }

  .input-section,
  .output-section {
    flex: 1 1 45%;
    min-width: 300px;
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.75);
    backdrop-filter: blur(10px);
    border-radius: 16px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.05);
    color: #111827;
  }

  .output-section {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 200px;

    .output-wrapper {
      text-align: center;
    }
  }

  .uk-select {
    background-color: #f3f4f6;
    border: 1px solid #d1d5db;
    color: #6b7280;
    border-radius: 6px;
    font-size: .9rem;

    &:focus {
      border-color: #b990ff;
      outline: none;
    }

    option {
      color: #111827;
      background-color: #fff;
    }
  }

  .uk-button {
     background-color: #7c3aed;
     color: white;
     border-radius: 999px;
     font-weight: 600;
     transition: all 0.3s ease;
     text-transform: capitalize;

    &:hover {
      background-color: #6d28d9;
      box-shadow: 0 6px 18px rgba(124, 58, 237, 0.2);
    }
  }
}
.uk-icon-button {
  text-decoration: none !important;

  i {
    color: #4b5563; /* neutral gray */
    transition: color 0.3s;

    &:hover {
       color: #7c3aed; 
    }
  }
}
</style>
