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

<h2>Example</h2>

``` pgsql
CREATE PROCEDURE Get_emp_names(Dept_num IN NUMBER) IS
      Emp_name VARCHAR(10);
      CURSOR c1(DepNo NUMBER) IS
            SELECT Ename FROM Emp_tab
            WHERE deptNo = DepNo; -- deptNo is an attribute
BEGIN
      OPEN c1(Dept_num);
      LOOP
            FETCH c1 INTO Emp_name;
            EXIT WHEN c1%NOTFOUND;
            dbms_output.put_line(Emp_name);
      END LOOP;
      CLOSE c1;
END;
```

<h2>Executing</h2>
<ul>
  <li>In standalone statement:
  </br><code>EXECUTE procedure(parameter list);</code></li>
  <li>Called from another PL/SQL block:
  </br><code>...</code>
  </br><code>procedure(parameter list);</code>
  </br><code>...</code></li>
</ul>

<h2>Deleting</h2>
<code>DROP PROCEDURE procedure-name;</code>

<h2>Function</h2>

``` pgsql
CREATE [OR REPLACE] FUNCTION
      function_name[(parameter [,parameter])]
      RETURN return_datatype
IS | AS
      [declaration_section]
BEGIN
      executable_section
      [EXCEPTION exception_section]
END [function_name];
```
## Function Example
``` pgsql
CREATE [OR REPLACE] FUNCTION FindCourse(name_in IN VARCHAR(2))
      RETURN NUMBER
IS
      cNumber NUMBER;
      CURSOR c1 IS
            SELECT course_number FROM courses_tbl
            WHERE course_name = name_in;
BEGIN
      OPEN c1;
      FETCH c1 INTO cNumber;
      ...
      CLOSE c1;
      RETURN cNumber;
END;

SELECT course_name, FindCourse(course_name) AS course_id
FROM courses
WHERE subject = 'Mathematics';
```

## Executing
<ul>
  <li>Similar to stored procedures</li>
  <li>Pass the required parameters along with function
  </br>name; If function returns a value, you can store
  </br>returned value</li>
  <li>Program control is transferred to the called
  </br>function</li>
  <li>A called function performs defined task and when
  </br>its returned statement is executed or when it last end
  </br>statement is reached, it returns program control
  </br>back to the main program.</li>
</ul>
