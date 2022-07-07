<script lang="ts">
    import ClassificationDropdown from './components/ClassificationDropdown.svelte';
    import Input from './components/Input.svelte';

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
        <div class="mrgn-tp-lg">
            <h1 id="title">EX Performance Calculator</h1>
        </div>

        <div class="table-responsive mrgn-tp-xl">
            <table class="table">
                <caption class="wb-inv">Caption text</caption>
                <thead>
                    <tr>
                        <th scope="col" class="col-md-2">Fiscal Year</th>
                        <th scope="col" class="col-md-2">Employment Classification</th>
                        <th scope="col" class="col-md-2">Salary</th>
                        <th scope="col" class="col-md-2">In-Range Salary %</th>
                        <th scope="col" class="col-md-2">Performance Pay %</th>
                        <th scope="col" class="col-md-2">Lump Sum Pay</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>
                            <p class="text-center">2017-2018</p>
                        </td>
                        <td>
                            <ClassificationDropdown />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Salary" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter In-Range %" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Performance Pay %" />
                        </td>
                        <td>
                            <p class="text-center">-</p>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <p class="text-center">2018-2019</p>
                        </td>
                        <td>
                            <ClassificationDropdown />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Salary" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter In-Range %" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Performance Pay %" />
                        </td>
                        <td>
                            <p class="text-center">-</p>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <p class="text-center">2019-2020</p>
                        </td>
                        <td>
                            <ClassificationDropdown />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Salary" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter In-Range %" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Performance Pay %" />
                        </td>
                        <td>
                            <p class="text-center">-</p>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <p class="text-center">2020-2021</p>
                        </td>
                        <td>
                            <ClassificationDropdown />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Salary" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter In-Range %" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Performance Pay %" />
                        </td>
                        <td>
                            <p class="text-center">-</p>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <p class="text-center">2021-2022</p>
                        </td>
                        <td>
                            <ClassificationDropdown />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Salary" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter In-Range %" />
                        </td>
                        <td>
                            <Input type="number" placeholder="Enter Performance Pay %" />
                        </td>
                        <td>
                            <p class="text-center">-</p>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div id="calculate-btn-container">
            <button class="btn btn-default btn-lg">Calculate</button>
        </div>
        <div id="results" class="mrgn-tp-sm">
            <h2 class="mrgn-bttm-md">Results Summary</h2>
            <div class="well">...</div>
        </div>
    </div>
</main>

<style>
    main {
        height: 100%;
    }

    #title {
        border-bottom: 3px solid #af3c43;
        margin-bottom: 0.2em;
        margin-top: 1em;
        padding-bottom: 0.2em;
    }

    td {
        vertical-align: middle !important;
    }

    th {
        text-align: center;
        font-size: small;
    }

    #calculate-btn-container {
        width: 100%;
        display: flex;
        justify-content: center;
    }
</style>
