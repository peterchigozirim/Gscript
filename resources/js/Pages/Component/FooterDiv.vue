<template>
    <div class="flex gap-3 text-xs">
        <div>
            <Link>Help</Link>
        </div>
        <div>
            <Link>Privacy</Link>
        </div>
        <div>
            <Link>Terms</Link>
        </div>
    </div>
</template>

<script>
import { Head, Link } from '@inertiajs/inertia-vue3';
export default {
    components:{Link}
}   
</script>

<style>

</style>