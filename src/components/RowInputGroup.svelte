<script>
  import ClassificationDropdown from "./ClassificationDropdown.svelte";
  import Input from "./Input.svelte";

  export let fiscalYear = "";
  export let data = {};
  let salary, inRangeSalaryPercentage, performancePayPercentage, classification, lumpSumPay;

  $: {
    if (salary && inRangeSalaryPercentage && performancePayPercentage && classification) {
      data.salary = salary;
      data.inRangeSalaryPercentage = inRangeSalaryPercentage;
      data.performancePayPercentage = performancePayPercentage;
      data.classification = classification;
    }
  }
</script>

<tr>
  <td>
    <p class="text-center">{fiscalYear}</p>
  </td>
  <td>
    <ClassificationDropdown bind:value={classification} />
  </td>
  <td>
    <Input bind:value={salary} type="number" placeholder="Enter Salary" />
  </td>
  <td>
    <Input bind:value={inRangeSalaryPercentage} type="number" placeholder="Enter In-Range %" />
  </td>
  <td>
    <Input bind:value={performancePayPercentage} type="number" placeholder="Enter Performance Pay %" />
  </td>
  <!-- <td>
    <p class="text-center">{lumpSumPay || "-"}</p>
  </td> -->
</tr>

<style>
  td {
    vertical-align: middle !important;
  }

  p {
    white-space: nowrap;
    font-size: small;
  }
</style>
