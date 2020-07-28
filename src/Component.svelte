<script>
    import { reaction } from 'mobx';

    reaction(()=>{},()=>{console.log('abecadlo')})
</script>

<slot />