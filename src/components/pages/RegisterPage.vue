<script setup lang="ts">
  const timeline = [
    {
      title: 'Registration Deadline',
      // date: new Date('2023-10-22'),
      date: null,
      config: {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      }
    },
    {
      title: 'Selection Phase 1',
      // date: new Date('2023-10-28'),
      date: null,
      config: {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      }
    },
    {
      title: 'Selection Phase 2',
      // date: new Date('2023-12-10'),
      date: null,
      config: {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      }
    },
    {
      title: 'Announcement',
      // date: new Date('2024-1-1'),
      date: null,
      config: {
        year: 'numeric',
        month: 'long',
      }
    },
    {
      title: 'Start of Basic Training',
      // date: new Date('2024-2-1'),
      date: null,
      config: {
        year: 'numeric',
        month: 'long',
      }
    },
  ]

  const parseDate = (date : Date | null, config : Object) => {
    if(date == null) return "TBA"
    else return date.toLocaleDateString('en-US', config)
  }
</script>

<template>
  <section class="pb-9">
    <h1>Hello, candidate!</h1>
    <h2>Interested in challenging yourself with fascinating problems? Join us!</h2>
  </section>

  <section class="pb-9">
    <center>
      <a href=""><button class="register-btn" disabled>Register</button></a>
      <p class="mt-2">Deadline: {{ parseDate(timeline[0].date, timeline[0].config) }}</p>
    </center>
  </section>

  <section class="pb-9">
    <p>Please join our <a href="https://discord.gg/5wwjr7xUhJ">Discord server</a> after registration. All announcements will be shared on the server.</p>
    <p>PS.</p>
    <ul>
      <li>Don't hesitate to register if you don't have any coding experience! Use your time to <span class="span-link" @click="$emit('changePage', 1)">learn to code</span> before the first phase.</li>
      <li>Non-registrants are welcome too in our <a href="https://discord.gg/5wwjr7xUhJ">Discord server</a>. Go ahead and join in to learn more about us.</li>
    </ul>
  </section>

  <section class="py-4 px-2 highlight-box">
    <p>If you have any <b>high school CP experience (IOI contestant, OSN medalist, winner of BNPCHS, NPC, JCPC, etc.)</b> or achievements with other OI or OSN fields, please reach out to us as soon as possible via our social media channels, so that we can prepare you for the nearest competition.</p>
  </section>

  <section class="pb-9 mt-9">
    <h1>Timeline</h1>
    <div class="timeline">
      <div class="timeline-item" v-for="tl in timeline">
        <div class="timeline-content">
          <div class="timeline-title">
            <h2>{{ tl.title }}</h2>
          </div>
          <div class="timeline-date">
            <p>{{ parseDate(tl.date, tl.config) }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <section class="pb-9">
    If you still have any questions, feel free to reach out to us on <a href="http://instagram.com/binusjollybee">Instagram</a>, or for a quicker response, join our recruitment <a href="https://discord.gg/5wwjr7xUhJ">Discord server</a>.
  </section>

</template>

<style>
.timeline {
  position: relative;
  width: 100%;
  margin: 0 auto;
}

.timeline::after {
  content: '';
  position: absolute;
  width: 2px;
  background-color: white;
  top: 0;
  bottom: 0;
  left: 1rem;
  margin-left: -1px;
}

.timeline-item {
  position: relative;
  padding-left: 2rem;
  padding-top: 1rem;
  padding-bottom: 1rem;
}

.timeline-content::after {
  content: '';
  position: absolute;
  width: 1rem;
  height: 1rem;
  left: 0.5rem;
  background-color: #434343;
  border: 2px solid white;
  top: 2rem;
  border-radius: 50%;
  z-index: 1;
}

</style>
