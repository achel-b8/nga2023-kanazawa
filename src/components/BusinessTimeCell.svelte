<script lang="ts">
    import {
        StructuredListCell,
    } from 'carbon-components-svelte';
    import {format} from 'date-fns';

    export let salesStartTime: Date;
    export let salesEndTime: Date;
    export let salesBreakStartTime: Date|null;
    export let salesBreakEndTime: Date|null;
		export let additionalNotes: string|null = null;

    const formatTime = (time: Date) => {
        return format(time, 'HH:mm');
    }
</script>

{#if (salesBreakStartTime && salesBreakEndTime)}
    <StructuredListCell>{formatTime(salesStartTime)} - {formatTime(salesBreakStartTime)}
        <br>{formatTime(salesBreakEndTime)} - {formatTime(salesEndTime)}
			  {#if additionalNotes}<br>{additionalNotes}{/if}
		</StructuredListCell>
{:else}
    <StructuredListCell>
			{formatTime(salesStartTime)} - {formatTime(salesEndTime)}
			{#if additionalNotes}<br>※{additionalNotes}{/if}
		</StructuredListCell>
{/if}