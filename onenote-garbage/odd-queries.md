# Odd Queries?

```
select
p.output_destination_id,
o.name,
p.printed_dt_tm,
e.name_full_formatted,
p.printed_by_prsnl_id,
p.updt_id,
pa.name_full_formatted,
p.person_id
from pm_doc_print_hist p, prsnl e, output_dest o, person pa
plan p where p.output_destination_id = 33012751.00
join e where p.updt_id = e.person_id
join o where p.output_destination_id = o.output_dest_cd
join pa where p.person_id = pa.person_id
order by p.printed_dt_tm desc
with maxrec=200000, format(date,";;q")
```

