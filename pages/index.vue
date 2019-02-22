<template>
  <section class="container">
    <div>
      <h1 class="title">
        Pathfinder Itinerary
      </h1>
      <h2 class="subtitle">
        Search the best routes to your destination.
      </h2>
      <div class="columns">
        <div class="column is-one-quarter">
          <div class="field">
            <label class="label is-medium">From</label>
            <div class="control">
              <input id="from" v-model="from" type="text" class="input is-medium">
            </div>
          </div>
        </div>
        <div class="column is-one-quarter">
          <div class="field">
            <label class="label is-medium">To</label>
            <div class="control">
              <input id="to" v-model="to" type="text" class="input is-medium">
            </div>
          </div>
        </div>
        <div class="column">
          <div class="field">
            <label class="label is-medium">Start date</label>
            <div class="control">
              <input id="startDate" v-model="startDate" type="text" class="input is-medium">
            </div>
          </div>
        </div>
        <div class="column">
          <div class="field">
            <label class="label is-medium">End date</label>
            <div class="control">
              <input id="endDate" v-model="endDate" type="text" class="input is-medium">
            </div>
          </div>
        </div>
        <div class="column">
          <div class="field">
            <label class="label is-medium">Guests</label>
            <div class="control">
              <input id="guests" v-model="guests" type="text" class="input is-medium">
            </div>
          </div>
        </div>
      </div>

      <div class="links">
        <a
          class="button--grey"
          @click="search"
        >Search</a>
        <a
          href="https://github.com/capyme/pathfinder-frontend"
          target="_blank"
          class="button--grey"
        >GitHub</a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      from: '',
      to: '',
      startDate: '',
      endDate: '',
      guests: ''
    }
  },
  methods: {
    search: function() {
      // TODO add the axios call to elixir
      body = {
        from: this.from,
        to: this.to,
        startDate: this.startDate,
        endDate: this.endDate,
        guests: this.guests
      }
      return axios.post('http://localhost:4000', body, {
        headers: {
          'accept': 'application/json'
        },
        withCredentials: true
      })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
