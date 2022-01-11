<section class="loader position-relative p-2 w-100 h-100 z-index-1 m-5">

</section>

<style>
    .loader::before {
        content: "";
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 50px;
        height: 50px;
        border: 2px solid #111;
        border-left: 2px solid transparent;
        animation: loading 500ms linear infinite;
    }

    @keyframes loading {
        100% {
            transform: translate(-50%, -50%) rotate(360deg);
        }
    }
</style>