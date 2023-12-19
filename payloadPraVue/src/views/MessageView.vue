<template>
    <div>
        <div v-for="message in messages" :key="message.id">
            <p v-if="message.sender === currentUser.id">Me: {{ message.chat }}</p>
            <p v-else>Other user: {{ message.chat }}</p>
        </div>
        <input v-model="newMessage" type="text" />
        <button @click="sendMessage">Send</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            messages: [], // Simpan pesan-pesan di sini
            newMessage: '', // Pesan yang ingin dikirim
            currentUser: {
                id: 'user_id_here', // ID pengguna saat ini (pengirim pesan)
            },
            otherUser: {
                id: 'other_user_id_here', // ID pengguna yang menerima pesan
            },
        };
    },
    methods: {
        async sendMessage() {
            // Lakukan logika untuk mengirim pesan ke database
            // Misalnya, menggunakan Axios untuk mengirim data pesan ke server
            // Setelah itu, tambahkan pesan baru ke array messages
            this.messages.push({
                sender: this.currentUser.id,
                receiver: this.otherUser.id,
                chat: this.newMessage,
                // Tambahkan waktu kirim atau properti lain yang diperlukan
            });

            // Reset input setelah mengirim pesan
            this.newMessage = '';
        },
        // Metode untuk mendapatkan pesan dari database, bisa menggunakan API atau cara lain
        async fetchMessages() {
            // Lakukan permintaan ke server untuk mendapatkan pesan-pesan antara pengguna ini
            // Setelah menerima respons, perbarui array messages
            // this.messages = dataFromServer;
        },
    },
    mounted() {
        // Panggil metode untuk mendapatkan pesan saat komponen dimuat
        this.fetchMessages();
    },
};
</script>
