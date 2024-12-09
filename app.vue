
<script setup>
 import { supabase } from './utils/spabase.ts'

 let { data: tests, error } = await supabase.from('tests').select('*');
          
</script>

<template>
  <ul>
    <li v-for="test in tests" :key="test.id">{{ test.title }}</li>
  </ul>
</template>
<script>


</script>


