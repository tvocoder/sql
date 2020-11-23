<h2>Subprograms, Stored Procedures, Functions,
  </br>and Packages</h2>
  
  <ul>
  <li>Subprograms
    <ul>
      <li>Named PL/SQL blocks that can take
      </br>parameters and be invoked</li>
      <li>Types
        <ul>
          <li>Stored procedures: No return value</li>
          <li>Functions: Always returns a single value</li>
        </ul>
      </li>
      <li>Parameters
        <ul>
          <li>IN: for input only. Default.</li>
          <li>OUT: for output value only</li>
          <li>IN OUT: for input and output</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

<h2>Procedure (in PL/SQL)</h2>

``` pgsql
CREATE [OR REPLACE] PROCEDURE
proc_name[list of parameters] {IS||AS}
      Declaration section
      
BEGIN
      Execution section
      EXCEPTION
      Exception section
END;
```
