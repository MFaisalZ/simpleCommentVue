<template>
    <div>
      <h2>Daftar Komentar</h2>
      <div class="comment-form">
        <input
          v-model="newComment.username"
          type="text"
          placeholder="Masukkan nama Anda"
        />
        <input
          v-model="newComment.comment"
          type="text"
          placeholder="Masukkan komentar Anda"
        />
        <button @click="addComment">Tambah Komentar</button>
      </div>
      <div class="comment-list-container">
        <comment-item
          v-for="(comment, index) in comments"
          :key="index"
          :username="comment.username"
          :comment="comment.comment"
          :date="comment.date"
        />
      </div>
    </div>
  </template>
  
  <script>
  import CommentItem from './CommentItem.vue';
  
  export default {
    name: 'CommentList',
    components: {
      CommentItem
    },
    data() {
      return {
        comments: [
          { username: 'Hasbiee', comment: 'Ini komentar pertama!', date: 'Minggu, 8 Desember 2024, 14:00' },
          { username: 'Rizky', comment: 'Vue.js sangat keren!', date: 'Sabtu, 7 Desember 2024, 18:30' },
          { username: 'Maulidan', comment: 'Saya suka belajar framework ini.', date: 'Jumat, 6 Desember 2024, 21:15' }
        ],
        newComment: {
          username: '',
          comment: ''
        }
      };
    },
    methods: {
      getFormattedDate() {
        const now = new Date();
        const days = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'];
        const months = [
          'Januari', 'Februari', 'Maret', 'April', 'Mei', 'Juni',
          'Juli', 'Agustus', 'September', 'Oktober', 'November', 'Desember'
        ];
        const day = days[now.getDay()];
        const date = now.getDate();
        const month = months[now.getMonth()];
        const year = now.getFullYear();
        const hours = String(now.getHours()).padStart(2, '0');
        const minutes = String(now.getMinutes()).padStart(2, '0');
  
        return `${day}, ${date} ${month} ${year}, ${hours}:${minutes}`;
      },
      addComment() {
        if (this.newComment.username.trim() && this.newComment.comment.trim()) {
          const formattedDate = this.getFormattedDate();
          this.comments.push({
            username: this.newComment.username,
            comment: this.newComment.comment,
            date: formattedDate
          });
          this.newComment.username = '';
          this.newComment.comment = '';
        } else {
          alert('Nama pengguna dan komentar tidak boleh kosong!');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .comment-form {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .comment-form input {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 1rem;
    flex: 1 1 250px;
  }
  
  .comment-form button {
    padding: 10px 15px;
    border: none;
    background-color: #28a745;
    color: white;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1rem;
    flex: 0 1 auto;
  }
  
  .comment-form button:hover {
    background-color: #218838;
  }
  
  .comment-list-container {
    max-height: 300px;
    overflow-y: auto;
    border: 1px solid #ddd;
    padding: 10px;
    border-radius: 4px;
    background-color: #be29ec;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
    
  .comment-list-container::-webkit-scrollbar {
    width: 8px;
  }
  
  .comment-list-container::-webkit-scrollbar-thumb {
    background-color: #ccc;
    border-radius: 4px;
  }
  
  .comment-list-container::-webkit-scrollbar-thumb:hover {
    background-color: #aaa;
  }
  </style>
  