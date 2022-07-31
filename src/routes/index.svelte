<h1>{ title }</h1>
<p>
    <select bind:value={selected} name="input-age" id="age">
        {#each ageList as age}
            <option value="{age}">{age}</option>
        {/each}
    </select>
</p>

<p>
    selected is { selected } <br>
    <br>

    {#each generationList as generation}
        <span class="{ isMatched(selected, generation) ? 'matched' : 'unmatched' }">
            { generation.name } <br>
        </span>
    {/each}
</p>

<p>
    ref: https://business-textbooks.com/generation-list/
</p>

<style>
    .matched {
        color: red;
        font-size: larger;
    }

    .unmatched {
        color: gray;
        font-size: smaller;
    }
</style>

<script lang="ts">
    let selected = 1980;
    export const title = 'あなたの世代簡単判定';
    export const ageList = Array.from(Array(100), (_, i) => i + 1920);

    type generation = {
        name: string,
        start: number,
        end: number
    }
    export const generationList: generation[] = [
        {
            name: '大正世代（1912~1926）',
            start: 1912,
            end: 1926,
        },
        {
            name: '昭和一桁世代（1926~1934）',
            start: 1926,
            end: 1934,
        },
        {
            name: '焼け跡世代（1935~1946）',
            start: 1935,
            end: 1946,
        },
        {
            name: '団塊の世代（1947~1949）',
            start: 1947,
            end: 1949,
        },
        {
            name: 'しらけ世代（1950〜1964）',
            start: 1950,
            end: 1964
        },
        {
            name: 'バブル世代（1965〜1970）',
            start: 1965,
            end: 1970
        },
        {
            name: '氷河期世代（1970〜1983）',
            start: 1970,
            end: 1983
        },
        {
            name: 'プレッシャー世代（1982〜1987）',
            start: 1982,
            end: 1987
        },
        {
            name: 'ゆとり世代（1987〜2004）',
            start: 1987,
            end: 2004
        },
        {
            name: 'さとり世代（1990~）',
            start: 1990,
            /* TODO now */
            end: 2022
        },
        {
            name: 'ミレニアル世代（1980～2000）※プレッシャー世代・さとり世代・ゆとり世代を総称',
            start: 1980,
            end: 2000
        },
        {
            name: 'Z世代（1995年〜）',
            start: 1995,
            end: 2022
        },
    ];
    export const isMatched = (target: number, generation: generation) => {
        return generation.start <= target && target <= generation.end;
    }
</script>

<svelte:head>
    <title>
        { title }
    </title>
    <html lang="ja"></html>
</svelte:head>
