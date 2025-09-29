<script setup lang="ts">
import { reactive } from 'vue';
import { Head, Link } from '@inertiajs/vue3';
import { dashboard, login, register } from '@/routes';

interface Feature {
  title: string;
  desc: string;
}

const state = reactive({
  features: [
    { title: 'Новости', desc: 'Собираем последние события из открытых источников и аналитических отчетов.' },
    { title: 'Инструменты', desc: 'Набор бесплатных инструментов для анализа и мониторинга данных.' },
    { title: 'Отчеты', desc: 'Ограниченный доступ без регистрации, полные отчеты после входа.' },
  ] as Feature[],
});
</script>

<template>
  <Head title="OSINT Analytics">
    <link rel="preconnect" href="https://rsms.me/" />
    <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
  </Head>

  <div class="min-h-screen flex flex-col bg-gradient-to-b from-[#f5f6fa] to-[#e9ecf1] dark:from-[#0f0f0f] dark:to-[#1a1a1a] text-[#1b1b18] dark:text-[#EDEDEC]">

    <header class="w-full p-6 flex justify-between items-center backdrop-blur-md bg-white/40 dark:bg-black/20 border-b border-white/20 dark:border-[#3E3E3A]/40 fixed top-0 z-50">
      <h1 class="text-2xl font-extrabold tracking-tight">
        OSINT<span class="text-indigo-500">Analytics</span>
      </h1>
      <nav class="flex gap-4">
        <Link
          v-if="$page.props.auth.user"
          :href="dashboard()"
          class="inline-block rounded-full border border-transparent px-5 py-2 font-medium transition hover:bg-indigo-500 hover:text-white dark:hover:bg-indigo-600"
        >
          Dashboard
        </Link>
        <template v-else>
          <Link
            :href="login()"
            class="inline-block rounded-full px-5 py-2 font-medium hover:text-indigo-500 transition"
          >
            Log in
          </Link>
          <Link
            :href="register()"
            class="inline-block rounded-full bg-indigo-500 text-white px-5 py-2 font-medium hover:bg-indigo-600 transition"
          >
            Register
          </Link>
        </template>
      </nav>
    </header>

    <main class="flex-grow pt-40">
      <section class="flex flex-col items-center justify-center text-center pb-24 px-6 lg:px-20 relative">
        <h2 class="text-5xl lg:text-6xl font-extrabold mb-6 leading-tight">
          Аналитика и OSINT <br class="hidden lg:block" /> на кончиках ваших пальцев
        </h2>
        <p class="max-w-2xl text-lg mb-8 text-gray-700 dark:text-gray-300">
          Получайте актуальную информацию, анализируйте данные и следите за событиями — всё в одном месте.
        </p>
        <Link
          v-if="!$page.props.auth.user"
          :href="register()"
          class="bg-indigo-500 text-white px-8 py-4 rounded-full text-lg font-semibold hover:bg-indigo-600 transition shadow-lg shadow-indigo-500/30"
        >
          Начать бесплатно
        </Link>
      </section>

      <section class="grid gap-8 px-6 lg:grid-cols-3 lg:px-20 mb-32">
        <div
          v-for="(item, i) in state.features"
          :key="i"
          class="p-8 rounded-2xl bg-white/60 dark:bg-white/10 border border-white/30 dark:border-[#3E3E3A]/30 backdrop-blur-md hover:scale-[1.03] hover:shadow-2xl transition"
        >
          <h3 class="font-bold text-2xl mb-3">{{ item.title }}</h3>
          <p class="text-gray-700 dark:text-gray-300">{{ item.desc }}</p>
        </div>
      </section>
    </main>

    <footer class="mt-auto w-full p-6 text-center border-t border-white/20 dark:border-[#3E3E3A]/40 text-sm text-gray-600 dark:text-gray-400">
      &copy; 2025 OSINT Analytics. Все права защищены.
    </footer>
  </div>
</template>

