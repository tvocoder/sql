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

## A BEFORE Trigger
``` mysql
CREATE TRIGGER StaffNotHandlingTooMuch
BEFORE INSERT ON PropertyForRent
REFERENCING NEW AS newRow
FOR EACH ROW
DECLARE
      vpCount NUMBER;
BEGIN
      SELECT COUNT(*) INTO vpCount
      FROM PropertyForRent
      WHERE staffNo = :newRow.staffNo;
      IF vpCount = 100
            raise_application_error(-20000, ('Member' || :newRow.staffNo || 'already managing 100 properties');
      END IF;
END;
```
