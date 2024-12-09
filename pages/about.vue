<script setup>
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = process.env.SUPABASE_URL;
const supabaseKey = process.env.SUPABASE_KEY;

const supabase = createClient(supabaseUrl, supabaseKey);
const tests = ref([])

async function getTests() {
  const { data } = await supabase.from('tests').select()
  tests.value = data
}
onMounted(() => {
  getTests()
})
</script>

<template>
  <nav>
    <ul v-for="test in tests" :key="test.id">
      <li>{{ test.title }}</li>
      <li>{{ test.text }}</li>
    </ul>
  </nav>
</template>