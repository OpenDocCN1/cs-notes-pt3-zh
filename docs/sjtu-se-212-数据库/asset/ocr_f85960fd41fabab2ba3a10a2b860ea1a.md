# Trigger

Use triggers on section and time_slot to enforce integrity constraints

Create Trigger timeslot_check1 after insert on section referencing new row as nrow

for each row

when (nrow.time_slot_id not in (select time_slot_id from time_slot))

```
begin
    rollback
end;
```