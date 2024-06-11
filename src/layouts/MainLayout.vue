<template>
  <q-layout view="hHh lpR fFf">
    <q-header class="bg-black" elevated>
      <q-toolbar>
        <q-toolbar-title class="text-white"> UAS FARHAN AKBAR </q-toolbar-title>
        <q-btn dense flat round icon="menu" @click="toggleRightDrawer" class="text-white" />
      </q-toolbar>
    </q-header>
    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <!-- drawer content -->
      <q-list bordered padding>
        <q-item clickable v-ripple @click="goToTask(1)">Tugas 1</q-item>
        <q-item clickable v-ripple @click="goToTask(2)">Tugas 2</q-item>
        <q-item clickable v-ripple @click="goToTask(3)">Tugas 3</q-item>
        <q-item clickable v-ripple @click="goToTask(4)">Tugas 4</q-item>
        <q-item clickable v-ripple @click="goToTask(5)">Tugas 5</q-item>
        <q-item clickable v-ripple @click="goToTask(6)">Tugas 6</q-item>
        <q-item clickable v-ripple @click="goToTask(7)">Tugas 7</q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <footer>
      <p>Farhan Akbar</p>
      <p>Informatika</p>
      <div class="social">
        <a href="https://www.instagram.com/farhnakbar/"><i class="bx bxl-instagram-alt"></i></a>
        <a href="https://www.youtube.com/channel/UC_Wpqpjhh69cBEqxNTXPM1g"
          ><i class="bx bxl-discord-alt"></i
        ></a>
        <a href="https://x.com/GreedHan12"><i class="bx bxl-twitter"></i></a>
      </div>
      <p class="end">&copy; Copy right by HAN</p>
    </footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const rightDrawerOpen = ref(false)

    const goToTask = (taskNumber) => {
      const taskLinks = {
        1: 'https://farhan-project-cv.vercel.app/',
        2: 'https://prak-pbk-tugas2-mhd-farhan-akbar-alhabi-223510671.vercel.app/',
        3: 'https://tugas3-prak-pbk-mhd-farhan-akbar-223510671.vercel.app/',
        4: 'https://farhanakbar-223510671-t4.vercel.app/',
        5: 'https://mhdfarhanakbaralhasbi223510671tugas5prakpbk.vercel.app/',
        6: 'https://farhanakbar-223510671-t6.vercel.app/',
        7: 'https://farhanakbar-223510671-t7.vercel.app/'
      }
      window.location.href = taskLinks[taskNumber]
    }

    const toggleRightDrawer = () => {
      rightDrawerOpen.value = !rightDrawerOpen.value
    }

    return {
      rightDrawerOpen,
      toggleRightDrawer,
      goToTask
    }
  }
}
</script>

<style>
.bg-black {
  background-color: #000000;
}

footer {
  position: relative;
  width: 100%;
  height: 230px;
  background: #101010;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: 30px;
}
footer p:nth-child(1) {
  font-size: 30px;
  color: white;
  margin-bottom: 5px;
  font-weight: bold;
}
footer p:nth-child(2) {
  color: white;
  font-size: 17px;
  width: 500px;
  text-align: center;
  line-height: 26px;
}

.social {
  display: flex;
}
.social a {
  width: 45px;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: #1a2c50;
  margin: 22px 10px;
  color: white;
  text-decoration: none;
  font-size: 20px;
}
.social a:hover {
  transition: 0.4s;
  transform: scale(1.3);
}
.end {
  position: absolute;
  color: #1a2c50;
  margin-bottom: -6px;
  font-size: 14px;
}
</style>
