<script lang="ts">
  import RowInputGroup from "./components/RowInputGroup.svelte";

  const classifications = {
    "EX-01": {
      "2017": { minpay: 112300, maxpay: 132100 },
      "2018": { minpay: 115444, maxpay: 135799 },
      "2019": { minpay: 117984, maxpay: 138787 },
      "2020": { minpay: 119754, maxpay: 140869 },
      "2021": { minpay: 121550, maxpay: 142982 },
    },
    "EX-02": {
      "2017": { minpay: 125900, maxpay: 148100 },
      "2018": { minpay: 129425, maxpay: 152247 },
      "2019": { minpay: 132272, maxpay: 155596 },
      "2020": { minpay: 134256, maxpay: 157930 },
      "2021": { minpay: 136270, maxpay: 160299 },
    },
    "EX-03": {
      "2017": { minpay: 140900, maxpay: 165700 },
      "2018": { minpay: 144845, maxpay: 170340 },
      "2019": { minpay: 148032, maxpay: 174087 },
      "2020": { minpay: 150252, maxpay: 176698 },
      "2021": { minpay: 152506, maxpay: 179348 },
    },
    "EX-04": {
      "2017": { minpay: 161500, maxpay: 190000 },
      "2018": { minpay: 166022, maxpay: 195320 },
      "2019": { minpay: 169674, maxpay: 199617 },
      "2020": { minpay: 172219, maxpay: 202611 },
      "2021": { minpay: 174802, maxpay: 205650 },
    },
    "EX-05": {
      "2017": { minpay: 181000, maxpay: 212900 },
      "2018": { minpay: 186068, maxpay: 218861 },
      "2019": { minpay: 190161, maxpay: 223676 },
      "2020": { minpay: 193013, maxpay: 227031 },
      "2021": { minpay: 195908, maxpay: 230436 },
    },
  };

  const economicIncreases = {
    "2018": 0.028,
    "2019": 0.022,
    "2020": 0.015,
    "2021": 0.015,
  };

  const inputs = { "2017": {}, "2018": {}, "2019": {}, "2020": {}, "2021": {} };

  const results: any = { "2017": {}, "2018": {}, "2019": {}, "2020": {}, "2021": {} };

  const currencyFormatter = new Intl.NumberFormat(`en-CA`, {
    currency: `CAD`,
    style: "currency",
  });

  const getLumpSumPay = (classification: string, year: string, salary: number, inRangePercentage: number, performancePayPercentage: number) => {
    const { minpay, maxpay } = classifications[classification][year];
    const economicIncreaseRate = economicIncreases[year] || 0;

    // to return
    const beforeRevision = { finalSalary: 0, atRiskPay: 0, bonus: 0 };
    const afterRevision = { finalSalary: 0, atRiskPay: 0, bonus: 0 };

    // salary increase by in range percentage
    const salaryIncrease = salary * (inRangePercentage / 100);

    // checking for maxpay cap
    beforeRevision.finalSalary = salary + salaryIncrease > maxpay ? maxpay : Math.round((salary + salaryIncrease) / 100) * 100;

    const revisedSalary = salary + salaryIncrease + (salary + salaryIncrease) * economicIncreaseRate;

    afterRevision.finalSalary = revisedSalary > maxpay ? maxpay : Math.round(revisedSalary / 100) * 100;

    // Performance Pay

    beforeRevision.atRiskPay = Math.round(salary * (performancePayPercentage / 100));
    beforeRevision.bonus = Math.round(salary * 0.03);

    afterRevision.atRiskPay = Math.round(revisedSalary * (performancePayPercentage / 100));
    afterRevision.bonus = Math.round(revisedSalary * 0.03);

    return { beforeRevision, afterRevision };
  };

  const calculateResults = () => {
    // TODO - types
    Object.entries(inputs).forEach(([year, data]: any) => {
      if (Object.keys(data).length !== 0) {
        results[year] = getLumpSumPay(data.classification, year, parseFloat(data.salary), parseFloat(data.inRangeSalaryPercentage), parseFloat(data.performancePayPercentage));
      }
    });
  };
</script>

<main>
  <div class="container">
    <div class="mrgn-tp-lg">
      <h1 id="title">EX Performance Calculator</h1>
    </div>

    <div class="table-responsive mrgn-tp-xl">
      <table id="input-table" class="table">
        <thead>
          <tr>
            <th scope="col" class="col-md-2">Fiscal Year</th>
            <th scope="col" class="col-md-2">Employment Classification</th>
            <th scope="col" class="col-md-2">Salary</th>
            <th scope="col" class="col-md-2">In-Range Salary %</th>
            <th scope="col" class="col-md-2">Performance Pay %</th>
            <!-- <th scope="col" class="col-md-2">Lump Sum Pay</th> -->
          </tr>
        </thead>
        <tbody>
          <RowInputGroup fiscalYear="2017-2018" bind:data={inputs[2017]} />
          <RowInputGroup fiscalYear="2018-2019" bind:data={inputs[2018]} />
          <RowInputGroup fiscalYear="2019-2020" bind:data={inputs[2019]} />
          <RowInputGroup fiscalYear="2020-2021" bind:data={inputs[2020]} />
          <RowInputGroup fiscalYear="2021-2022" bind:data={inputs[2021]} />
        </tbody>
      </table>
    </div>
    <div id="calculate-btn-container" class="mrgn-tp-md">
      <button on:click={calculateResults} class="btn btn-default btn-lg">Calculate</button>
    </div>
    <div id="results" class="mrgn-tp-sm">
      <h2 class="mrgn-bttm-md">Results Summary</h2>
      <div class="well">
        {#each Object.keys(results) as year}
          {#if Object.keys(results[year]).length !== 0}
            <h3>{year}-{parseInt(year) + 1}</h3>
            <table class="table">
              <thead>
                <tr>
                  <th scope="col" />
                  <th scope="col">Before Revision</th>
                  <th scope="col">After Revision</th>
                  <th scope="col">Difference</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <th scope="row">Salary</th>
                  <td>{currencyFormatter.format(results[year].beforeRevision.finalSalary)}</td>
                  <td>{currencyFormatter.format(results[year].afterRevision.finalSalary)}</td>
                  <td>{currencyFormatter.format(results[year].afterRevision.finalSalary - results[year].beforeRevision.finalSalary)}</td>
                </tr>
                <tr>
                  <th scope="row">At Risk Pay</th>
                  <td>{currencyFormatter.format(results[year].beforeRevision.atRiskPay)}</td>
                  <td>{currencyFormatter.format(results[year].afterRevision.atRiskPay)}</td>
                  <td>{currencyFormatter.format(results[year].afterRevision.atRiskPay - results[year].beforeRevision.atRiskPay)}</td>
                </tr>
                <tr>
                  <th scope="row">Bonus</th>
                  <td>{currencyFormatter.format(results[year].beforeRevision.bonus)}</td>
                  <td>{currencyFormatter.format(results[year].afterRevision.bonus)}</td>
                  <td>{currencyFormatter.format(results[year].afterRevision.bonus - results[year].beforeRevision.bonus)}</td>
                </tr>
              </tbody>
            </table>

            <br />
          {/if}
        {/each}
      </div>
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

  #input-table th {
    text-align: center;
    font-size: small;
    white-space: nowrap;
  }

  th {
    font-size: small;
    white-space: nowrap;
  }

  #calculate-btn-container {
    width: 100%;
    display: flex;
    justify-content: center;
  }
</style>
