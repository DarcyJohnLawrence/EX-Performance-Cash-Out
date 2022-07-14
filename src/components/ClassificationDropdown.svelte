<script>
  export let value = "";
</script>

<fieldset>
  <div class="form-group">
    <select class="form-control" {...$$restProps} bind:value>
      <option label="Select a classification" />
      <option value="EX-01">EX-01</option>
      <option value="EX-02">EX-02</option>
      <option value="EX-03">EX-03</option>
      <option value="EX-04">EX-04</option>
      <option value="EX-05">EX-05</option>
    </select>
  </div>
</fieldset>

<style>
  option,
  select {
    font-size: small;
  }
</style>
