<template>
    <div>
        <div class="header">Are you ready to take the challenge?</div>
        <div class="sec-text">Download Herlem Wizards App</div>
        <div class="flex-rw btn-container">
            <img src="../assets/google.png" alt="" class="btn" @click="open('android')">
            <img src="../assets/apple.png" alt="" class="btn" @click="open('ios')">
        </div>
        <div class="sec-text ter-text flex-rw">
            <div class="grey-line" />
            <div>or you can sign up right now</div>
            <div class="grey-line" /> 
        </div>
    </div>
</template>
<script>
export default {
    methods: {
        open (value) {
            if (value === 'android') {
                window.open('https://play.google.com/store/apps/details?id=com.goteamup.app.wizfitstudios&hl=en&pli=1', '_blank');
            } else if (value === 'ios') {
                window.open('https://apps.apple.com/in/app/wizfit/id6478859721','_blank')
            }
        }
    }
}
</script>
<style scopp lang="scss">
@import '../styles.scss'; 
.header {
    font-weight: 500;
}
.sec-text {
    font-weight: 600;
    font-size: 0.9rem;
}
.grey-line {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 20%; /* Full width or adjust as needed */
    height: 1px; /* Thin line */
    background-color: grey; /* Grey color for the line */
}
.ter-text {
    justify-content: center;
    align-items: center;
    gap: 20px;
}
.btn-container {
    padding: 5px 20px 24px;
    justify-content: center;
}
.btn {
    width: 20%;
    &:hover {
        cursor: pointer;
    }
}
</style>