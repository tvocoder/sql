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

## An After Trigger
``` mysql
CREATE TRIGGER StaffAfterInsert
AFTER INSERT ON Staff
REFERENCING NEW AS newRow
FOR EACH ROW
BEGIN
      INSERT INTO StaffAudit
      VALUES(:newRow.staffNo, :newRow.fName, :newRow.lName, :newRow.position, :newRow.sex, ....);
END;
```

## INSTEAD OF Trigger

<ul>
  <li>Views are not updateable if there are more
    </br>two base tables</li>
  <li>INSTEAD OF Triggers are used to update views</li>
</ul>

## Trigger Privilege

<ul>
  <li>Must be the owner of the table</li>
  <li>Or have been granted the TRIGGER privilege on
    </br>the table</li>
</ul>

## Trigger Advantages and Disadvantages
<ul>
  <li>Reduce redundancy</li>
  <li>Simple modifications</li>
  <li>Increase security</li>
  <li>Improve integrity</li>
  <li>Improve processing power</li>
  <li>...</li>
  <li>Performance overhead</li>
  <li>Cascading effects</li>
</ul>
