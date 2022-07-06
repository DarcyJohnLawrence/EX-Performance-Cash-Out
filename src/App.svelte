<script lang="ts">
    import ClassificationDropdown from './components/ClassificationDropdown.svelte';

    const classifications = {
        'EX-01': {
            '2017': { minpay: 112300, maxpay: 132100 },
            '2018': { minpay: 115444, maxpay: 135799 },
            '2019': { minpay: 117984, maxpay: 138787 },
            '2020': { minpay: 119754, maxpay: 140869 },
            '2021': { minpay: 121550, maxpay: 142982 },
        },
        'EX-02': {
            '2017': { minpay: 125900, maxpay: 148100 },
            '2018': { minpay: 129425, maxpay: 152247 },
            '2019': { minpay: 132272, maxpay: 155596 },
            '2020': { minpay: 134256, maxpay: 157930 },
            '2021': { minpay: 136270, maxpay: 160299 },
        },
        'EX-03': {
            '2017': { minpay: 140900, maxpay: 165700 },
            '2018': { minpay: 144845, maxpay: 170340 },
            '2019': { minpay: 148032, maxpay: 174087 },
            '2020': { minpay: 150252, maxpay: 176698 },
            '2021': { minpay: 152506, maxpay: 179348 },
        },
        'EX-04': {
            '2017': { minpay: 161500, maxpay: 190000 },
            '2018': { minpay: 166022, maxpay: 195320 },
            '2019': { minpay: 169674, maxpay: 199617 },
            '2020': { minpay: 172219, maxpay: 202611 },
            '2021': { minpay: 174802, maxpay: 205650 },
        },
        'EX-05': {
            '2017': { minpay: 181000, maxpay: 212900 },
            '2018': { minpay: 186068, maxpay: 218861 },
            '2019': { minpay: 190161, maxpay: 223676 },
            '2020': { minpay: 193013, maxpay: 227031 },
            '2021': { minpay: 195908, maxpay: 230436 },
        },
    };
</script>

<main>
    <div class="container">
        <h1>EX Performance Calculator</h1>

        <table class="table mrgn-tp-xl">
            <caption class="wb-inv">Caption text</caption>
            <thead>
                <tr>
                    <th scope="col">Fiscal Year</th>
                    <th scope="col">Employment Classification</th>
                    <th scope="col">Salary</th>
                    <th scope="col">In-Range Salary %</th>
                    <th scope="col">Performance pay %</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>
                        <p>2017-2018</p>
                    </td>
                    <td>
                        <ClassificationDropdown />
                    </td>
                    <td>-</td>
                    <td>-</td>
                    <td>-</td>
                </tr>
                <tr>
                    <td>
                        <p>2018-2019</p>
                    </td>
                    <td>
                        <ClassificationDropdown />
                    </td>
                    <td>-</td>
                    <td>-</td>
                    <td>-</td>
                </tr>
                <tr>
                    <td>
                        <p>2019-2020</p>
                    </td>
                    <td>
                        <ClassificationDropdown />
                    </td>
                    <td>-</td>
                    <td>-</td>
                    <td>-</td>
                </tr>
                <tr>
                    <td>
                        <p>2020-2021</p>
                    </td>
                    <td>
                        <ClassificationDropdown />
                    </td>
                    <td>-</td>
                    <td>-</td>
                    <td>-</td>
                </tr>
                <tr>
                    <td>
                        <p>2021-2022</p>
                    </td>
                    <td>
                        <ClassificationDropdown />
                    </td>
                    <td>-</td>
                    <td>-</td>
                    <td>-</td>
                </tr>
            </tbody>
        </table>
    </div>
</main>

<style>
    main {
        height: 100%;
    }

    td {
        vertical-align: middle !important;
    }
</style>
