<template>
<p class="last-modified">最后更新于{{buildTime}}</p>
<a class="download-pdf" href="https://mansters.github.io/manny-resume/前端_孟宪邦_17602208145.pdf">下载 PDF</a>
</template>

<script setup>
import dayjs from 'dayjs'
const buildTime = dayjs(VITE_APP_TIME).format('YYYY-MM-DD')
</script>