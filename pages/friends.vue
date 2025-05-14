<script setup lang="ts">
import { friendsList } from '@/site.config'
</script>

<template>
  <div>
    <h1 class="text-title mb-2em font-bold text-center">
      朋友们
    </h1>
    <article v-for="(series, index) in friendsList" :key="index" slide-enter :style="{ '--stagger': index + 1 }">
      <div class="text-center mt-2em mb-1em text-gray-700:60" font-bold text-lg>
        {{ series.name }}
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-1em">
        <a
          v-for="(friend) in series.content"
          :key="friend.path"
          :title="friend.name"
          :href="friend.path"
          target="_blank"
          class="flex items-center py-0.5em px-1em rounded-sm hover:bg-gray-400:10"
        >
          <!-- 头像区域 -->
          <div class="w-10 h-10 rounded-full overflow-hidden mr-1em flex-shrink-0">
            <img
              :src="friend.avatar || 'https://example.com/default-avatar.png'"
              :alt="friend.name"
              class="w-full h-full object-cover"
            >
          </div>

          <!-- 文字区域 -->
          <div class="hover w-full">
            <div class="text-lg flex items-center">
              {{ friend.name }}
              <span class="text-sm op-50 i-icon-park-outline-efferent-three ml-0.5em" />
            </div>
            <div class="text-sm op-70">{{ friend.desc }}</div>
          </div>
        </a>
      </div>
    </article>
  </div>
</template>
