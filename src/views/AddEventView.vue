<template>
  <div
    style="
      max-width: 75%;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      justify-content: center;
    "
  >
    <h1>Create an event</h1>

    <form @submit.prevent="sendForm">
      <BaseSelect
        :options="categories"
        v-model="event.category"
        label="Select a category"
      />

      <fieldset>
        <legend>Name & describe your event</legend>

        <BaseInput
          v-model="event.title"
          label="Title"
          type="text"
          error="Error!"
        />

        <BaseInput
          v-model="event.description"
          label="Description"
          type="text"
        />
      </fieldset>

      <fieldset>
        <legend>Where is your event?</legend>

        <BaseInput v-model="event.location" label="Location" type="text" />
      </fieldset>

      <fieldset>
        <legend>Pets</legend>
        <p>Are pets allowed?</p>
        <div>
          <BaseRadioGroup
            v-model="event.pets"
            name="pets"
            :options="petOptions"
          />
        </div>
      </fieldset>

      <fieldset>
        <legend>Extras</legend>
        <div>
          <BaseCheckbox v-model="event.extras.catering" label="Catering" />
        </div>

        <div>
          <BaseCheckbox v-model="event.extras.music" label="Live music" />
        </div>
      </fieldset>

      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import EventService from '@/services/EventService'
export default {
  data() {
    return {
      categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community',
      ],
      event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: 1,
        extras: {
          catering: false,
          music: false,
        },
      },
      petOptions: [
        {
          value: 1,
          label: 'Yes',
        },
        {
          value: 0,
          label: 'No',
        },
      ],
    }
  },
  methods: {
    sendForm() {
      EventService.createEvent(this.event)
        .then(() => {
          this.$router.push({
            name: 'EventList',
          })
        })
        .catch((error) => {
          this.$router.push({
            name: 'ErrorDisplay',
            params: { error },
          })
        })
    },
  },
}
</script>

<style scoped>
fieldset {
  border: 0;
  margin: 0;
  padding: 0;
}

legend {
  font-size: 28px;
  font-weight: 700;
  margin-top: 20px;
}
</style>
