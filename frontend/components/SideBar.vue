<template>
  <div>

    <button data-drawer-target="default-sidebar" data-drawer-toggle="default-sidebar" aria-controls="default-sidebar"
      type="button"
      class="inline-flex items-center p-2 mt-2 ms-3 text-sm text-gray-500 rounded-lg sm:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600">
      <span class="sr-only">Abrir Menu</span>
      <Icon name="mi:menu" class="text-4xl" />
    </button>
    <aside id="default-sidebar"
      class="fixed top-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full sm:translate-x-0"
      aria-label="Sidebar">
      <div class="h-full px-3 py-4 overflow-y-auto bg-gray-50 dark:bg-gray-800">
        <ul class="space-y-2 font-medium">
          <li>
            <a href="/"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group">
              <Icon name="octicon:checklist-24" class="text-2xl" />
              <span class="flex-1 ms-3 whitespace-nowrap">Tarefas</span>
            </a>
          </li>
          <li>
            <a href="/finishedTask"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group">
              <Icon name="material-symbols:check-box-outline" class="text-2xl" />
              <span class="flex-1 ms-3 whitespace-nowrap">Concluidas</span>
            </a>
          </li>
        </ul>
      </div>
    </aside>
  </div>
</template>



