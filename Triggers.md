## Trigger

<ul>
  <li>Trigger
    <ul>
      <li>Defines an action that the database should take
      </br>when some even occurs in the application</li>
      <li>Format of a trigger</li>
      <li>Types</li>
      <li>TRIGGER Privilege</li>
      <li>Advantages and disadvantages of triggers</li>
    </ul>
  </li>
</ul>

## Trigger Format

``` sql
CREATE TRIGGER TriggerName
    BEFORE | AFTER | INSTEAD OF
    INSERT | DELETE | UPDATE [OF TriggerColumnList]
    
    ON TableName
    [REFERENCING {OLD | NEW| AS {OldName | NewName}
    [FOR EACH {ROW | STATEMENT}]
    [WHEN Condition]
    <trigger action>
```
