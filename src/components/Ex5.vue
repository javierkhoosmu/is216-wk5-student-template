<script setup>
import axios from 'axios';
import { ref } from 'vue';
const moods = ref(['Happy', 'Sad', 'Angry']);
const subject = ref('');
const entry = ref('');
const mood = ref('');

// Add Code Here
async function add() {
    const url = "https://localhost:8000/posts"
    const data = {
        subject : subject.value,
        entry : entry.value,
        mood : mood.value
    }
}

try {
    const response = await axios.post(url, data)
    console.log(response.data)

} catch (error) {
    
}

</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->
        <br>
        <select v-model="mood" required>
            <option value="">Select mood</option>
            <option v-for="m in moods" :key="m" :value="m">{{ m }}</option>
        </select>

        <br>
        <button>Submit New Post</button>

        <hr>
        <RouterLink to="/ViewPosts/">Click  here to return to Main Page</RouterLink>  
       
    </div>
</template>

