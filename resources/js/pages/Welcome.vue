<script setup lang="ts">
import { dashboard, login, register } from '@/routes';
import { Head, Link } from '@inertiajs/vue3';
</script>

<template>
  <Head title="OSINT Analytics">
    <link rel="preconnect" href="https://rsms.me/" />
    <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
  </Head>

  <div class="min-h-screen flex flex-col bg-[#FDFDFC] dark:bg-[#0a0a0a] text-[#1b1b18] dark:text-[#EDEDEC]">

    <header class="w-full p-6 flex justify-between items-center border-b border-[#19140035] dark:border-[#3E3E3A]">
      <h1 class="text-xl font-bold">OSINT Analytics</h1>
      <nav class="flex gap-4">
        <Link
          v-if="$page.props.auth.user"
          :href="dashboard()"
          class="inline-block rounded-sm border border-[#19140035] px-5 py-2 hover:border-[#1915014a] dark:border-[#3E3E3A] dark:hover:border-[#62605b]"
        >
          Dashboard
        </Link>
        <template v-else>
          <Link
            :href="login()"
            class="inline-block rounded-sm border border-transparent px-5 py-2 hover:border-[#19140035] dark:hover:border-[#3E3E3A]"
          >
            Log in
          </Link>
          <Link
            :href="register()"
            class="inline-block rounded-sm border border-[#19140035] px-5 py-2 hover:border-[#1915014a] dark:border-[#3E3E3A] dark:hover:border-[#62605b]"
          >
            Register
          </Link>
        </template>
      </nav>
    </header>

    <section class="flex flex-col items-center justify-center text-center py-20 px-6 lg:px-20">
      <h2 class="text-4xl lg:text-5xl font-extrabold mb-4">Аналитика и OSINT на кончиках ваших пальцев</h2>
      <p class="max-w-xl text-lg mb-6">
        Получайте актуальную информацию, анализируйте данные и следите за событиями без регистрации.
      </p>
      <Link
        v-if="!$page.props.auth.user"
        :href="register()"
        class="bg-[#1b1b18] text-[#FDFDFC] px-6 py-3 rounded-lg hover:bg-[#333] dark:bg-[#EDEDEC] dark:text-[#0a0a0a] dark:hover:bg-[#ccc]"
      >
        Зарегистрироваться
      </Link>
    </section>

    <section class="grid gap-8 px-6 lg:grid-cols-3 lg:px-20 mb-20">
      <div class="p-6 border rounded-lg hover:shadow-lg transition dark:border-[#3E3E3A]">
        <h3 class="font-bold text-xl mb-2">Новости</h3>
        <p>Собираем последние события из открытых источников и аналитических отчетов.</p>
      </div>
      <div class="p-6 border rounded-lg hover:shadow-lg transition dark:border-[#3E3E3A]">
        <h3 class="font-bold text-xl mb-2">Инструменты</h3>
        <p>Используйте набор бесплатных инструментов для анализа и мониторинга данных.</p>
      </div>
      <div class="p-6 border rounded-lg hover:shadow-lg transition dark:border-[#3E3E3A]">
        <h3 class="font-bold text-xl mb-2">Отчеты</h3>
        <p>Доступ к ограниченным отчетам без регистрации, полные отчеты после входа в систему.</p>
      </div>
    </section>

    <footer class="w-full p-6 text-center border-t border-[#19140035] dark:border-[#3E3E3A]">
      &copy; 2025 OSINT Analytics. Все права защищены.
    </footer>
  </div>
</template>
