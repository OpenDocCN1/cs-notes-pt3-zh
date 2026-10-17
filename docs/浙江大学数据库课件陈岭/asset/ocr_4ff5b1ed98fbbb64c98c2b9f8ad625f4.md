# # Synthetic examples

Example 1: Consider the following relational schema:
part(id, name, color, weight, sub_part),
transfer the following SQL query into relational algebra expression:
SELECT part2.id FROM part as part1, part as part2
WHERE part1.id=part2.sub_part AND
part1.color='red' AND part2.color='blue' AND
part1.weight - part2.weight >100;
Πp2.id
(σp1.weight-p2.weight >100 (σp1.id=p2.sub_part(
(σp1.color='red'(ρp1(part1))) x (σp2.color='blue'(ρp2(part2))) ) ) )