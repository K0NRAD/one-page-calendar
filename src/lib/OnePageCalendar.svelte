<script lang="ts">
    const MONTHS: string[] = [
        "JAN", "FEB", "MÄR", "APR", "MAI", "JUN",
        "JUL", "AUG", "SEP", "OKT", "NOV", "DEZ",
    ];

    const DAY_NUMBERS: string[][] = [
        [" 1", " 8", "15", "22", "29"],
        [" 2", " 9", "16", "23", "30"],
        [" 3", "10", "17", "24", "31"],
        [" 4", "11", "18", "25", "  "],
        [" 5", "12", "19", "26", "  "],
        [" 6", "13", "20", "27", "  "],
        [" 7", "14", "21", "28", "  "],
    ];

    const DAY_NAMES: string[][] = [
        ["MO", "DI", "MI", "DO", "FR", "SA", "SO"],
        ["DI", "MI", "DO", "FR", "SA", "SO", "MO"],
        ["MI", "DO", "FR", "SA", "SO", "MO", "DI"],
        ["DO", "FR", "SA", "SO", "MO", "DI", "MI"],
        ["FR", "SA", "SO", "MO", "DI", "MI", "DO"],
        ["SA", "SO", "MO", "DI", "MI", "DO", "FR"],
        ["SO", "MO", "DI", "MI", "DO", "FR", "SA"],
    ];

    let year = new Date().getFullYear();

    const monthNamesByWeekday: string[][] = [
        ["", "", "", "", "", "", ""],
        ["", "", "", "", "", "", ""],
        ["", "", "", "", "", "", ""],
    ];

    $: {
        year;
        populateMonthNamesByWeekday();
    }

    const populateMonthNamesByWeekday = () => {
        resetMonthNamesByWeekday();
        for (let i = 0; i < MONTHS.length; i++) {
            const date = new Date(year, i, 1);
            const dayOfWeek = date.getDay();
            const weekday = dayOfWeek === 0 ? 6 : dayOfWeek - 1;
            for (let y = 0; y < monthNamesByWeekday.length; y++) {
                if (monthNamesByWeekday[y][weekday].length == 0) {
                    monthNamesByWeekday[y][weekday] = MONTHS[i];
                    break;
                }
            }
        }
    };

    const resetMonthNamesByWeekday = () => {
        for (let y = 0; y < monthNamesByWeekday.length; y++) {
            for (let x = 0; x < monthNamesByWeekday[y].length; x++) {
                monthNamesByWeekday[y][x] = "";
            }
        }
    };

</script>

<section>
    <div class="container">
        <div class="box top-left">
            <p class="year-label">{year}</p>
        </div>
        <div class="box top-right">
            <table>
                {#each monthNamesByWeekday as monthNames}
                    <tr>
                        {#each monthNames as monthName}
                            <td>{monthName}</td>
                        {/each}
                    </tr>
                {/each}
            </table>
        </div>
        <div class="box bottom-left">
            <table>
                {#each DAY_NUMBERS as dayNumbers}
                    <tr>
                        {#each dayNumbers as dayNumber}
                            <td>{dayNumber}</td>
                        {/each}
                    </tr>
                {/each}
            </table>
        </div>
        <div class="box bottom-right">
            <table>
                {#each DAY_NAMES as dayNames}
                    <tr>
                        {#each dayNames as dayName}
                            <td>{dayName}</td>
                        {/each}
                    </tr>
                {/each}
            </table>
        </div>
    </div>
</section>
<div class="container">
    <div class="form-group">
        <label for="year-input">Jahr</label>
        <input
            id="year-input"
            type="text"
            placeholder="Year"
            bind:value={year}
        />
    </div>
</div>

<style>
    .container {
        display: flex;
        flex-wrap: wrap;
        width: 100vh;
    }

    .box {
        box-sizing: border-box;
    }

    .top-left {
        flex-basis: 40%;
        border-left: 2px solid black;
        border-top: 2px solid black;
    }

    .bottom-left {
        flex-basis: 40%;
        border-left: 1px solid black;
        border-top: 1px solid black;
        border-bottom: 1px solid black;
    }

    .top-right {
        flex-basis: 60%;
        border-right: 1px solid black;
        border-left: 1px solid black;
        border-top: 1px solid black;
    }

    .bottom-right {
        flex-basis: 60%;
        border-right: 1px solid black;
        border-bottom: 1px solid black;
    }

    .top-left,
    .top-right,
    .bottom-left,
    .bottom-right {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    table {
        border-collapse: collapse;
        width: 100%;
    }

    td {
        border: 1px solid black;
        text-align: center;
        height: 3em;
        width: 2.5rem;
    }

    .form-group {
        display: flex;
        flex-direction: column;
    }

    label,
    input {
        margin-top: 0.5rem;
        font-size: 1.2rem;
        font-weight: 600;
        text-align: left;
    }
</style>
