<template>
    <div
        id="app"
        class="container"
    >
        <header class="header">
            <h1>Vue.js Frontend Application</h1>
        </header>
        <div class="row">
            <div class="col-md-8 mx-auto mt-5">
                <div class="card">
                    <div class="card-body">
                        <h2 class="card-title">
                            Response from Java API Server:
                        </h2>
                        <p class="card-text">{{ message }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: "",
        };
    },
    mounted() {
        this.fetchMessage();
    },
    methods: {
        async fetchMessage() {
            const apiUrl = process.env.VUE_APP_API_URL + "/api/message";
            const response = await fetch(apiUrl);
            const data = await response.json();
            this.message = data.message;
        },
    },
};
</script>

<style>
#app {
    text-align: center;
    margin-top: 20px;
}

.header h1 {
    color: #007bff;
    margin-bottom: 40px;
}

.card {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.card-title {
    color: #343a40;
    margin-bottom: 15px;
}

.card-text {
    color: #6c757d;
    font-size: 18px;
}
</style>
