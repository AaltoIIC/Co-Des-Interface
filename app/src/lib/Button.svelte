<script lang="ts">
    export let icon: string = '';
    export let isActive: boolean = true;
    export let lightMode: boolean = false;
    export let color: string = 'var(--main-color)';
    export let textColor: string = 'rgba(255, 255, 255, 0.9)';
    export let onClick: () => void = () => {};
</script>

<button
    on:click={onClick}
    class={`btn ${lightMode ? "lightmode" : ""} ${isActive ? '' : 'disabled'}`}
    style={`background-color: ${color}; color: ${textColor};`}>
    {#if icon}
        <span class="main-icon">
                {@html icon} 
        </span>             
    {/if}   
    <span class="main-text" style="{icon ? '' : 'padding-left: 14px !important;'}">
        <slot></slot>
    </span>
</button>
<style>
    .btn {
        padding: 0;
        display: inline-flex;
    }
    .lightmode {
        box-shadow: var(--main-shadow);
    }
    .main-text {
        padding: 8.5px 14px 9px 12px;
        font-weight: 500;
    }
    .main-icon {
        width: 18px;
        height: 18px;
        padding: 8px 6px 13px 8px;
        border-right: solid 2px rgba(0, 0, 0, 0.04);
        margin: 0 -2px -5px 0;
    }
    button {
        padding: 10px 12px;
        cursor: pointer;
        transition: .2s;
        overflow: hidden;
        font-family: 'Inter', sans-serif;
        border-radius: 50px;
        border: none;
    }
    button:hover {
        filter: brightness(1.05);
    }
    .disabled {
        pointer-events: none !important;
        background-color: var(--main-color-dark-2) !important;
        opacity: 0.7 !important;
    }
</style>