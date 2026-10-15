# Relational algebra practice

Seventeen exercises on the rental platform from Lecture 6 (Host, Listing, Guest, Booking), in the style of the exam questions. The data is fictional and larger than on the slides, so that typical mistakes show up in the result.

## How to work

Write each answer on paper first, in the notation from the lecture. Then run it in RelaX and compare the result with the expected result under the exercise. On the exam you write the lecture notation by hand; RelaX is only there to check your work. A matching result does not prove that an expression is correct for every database, but a different result always points to a mistake.

Each exercise also has a solution in the lecture notation and in RelaX. Open it only after you have your own answer; other expressions can be correct as well. The RelaX version can be pasted into the editor unchanged.

Every exercise can be solved with the operators from Lecture 6: σ, π, ρ, ×, joins, ∪, ∩, ∖, the left outer join and grouping with $`𝔉`$. None of them needs division. Relations are sets, so a result never contains the same tuple twice.

## Load the data in RelaX

1. Open [RelaX](https://dbis-uibk.github.io/relax/calc).
2. Open the tab **Group Editor**, delete its content and paste the complete content of [`rental-platform.txt`](rental-platform.txt) ([raw file](https://raw.githubusercontent.com/JanKalo/MDB2026/main/relational-algebra/rental-platform.txt)).
3. Click **preview**, then **use Group in editor**. The four relations appear on the left.
4. Write your expression in the tab **Relational Algebra** and click **execute query**.

If the four relations are gone when you come back to RelaX, paste the file again. The buttons above the editor insert the symbols; the last column of the notation table below shows what to type instead.

## Schema

```
Host(hid, hname)
Listing(lid, hid → Host, city, price)
Guest(gid, gname)
Booking(bid, lid → Listing, gid → Guest)
```

The keys are hid, lid, gid and bid. city is AMS (Amsterdam), RTM (Rotterdam) or UTR (Utrecht), and price is in euros per night. A guest can book the same listing more than once; every booking has its own bid. Guest names are not unique. No value is NULL.

## Notation: lecture and RelaX

| Lecture | RelaX | RelaX, typed on a keyboard |
|---|---|---|
| $`\sigma_{p} ( R )`$ | σ p (R) | sigma p (R) |
| $`\pi_{a ,\, b} ( R )`$ | π a, b (R) | pi a, b (R) |
| $`\rho_{S} ( R )`$ | ρ S (R) | rho S (R) |
| $`\rho_{( x ,\, y )} ( R )`$, where R has columns a, b | ρ x←a, y←b (R) | rho x<-a, y<-b (R) |
| $`\rho_{S ( x ,\, y )} ( R )`$ | ρ S (ρ x←a, y←b (R)) | rho S (rho x<-a, y<-b (R)) |
| $`R \times S`$ | R ⨯ S | R cross join S |
| $`R \bowtie S`$ | R ⋈ S | R natural join S |
| $`R \bowtie_{p} S`$ | R ⋈ p S | R join p S |
| $`R \mathrel{⟕}_{p} S`$ | R ⟕ p S | R left join p S |
| $`R \cup S`$, $`R \cap S`$ | R ∪ S, R ∩ S | R union S, R intersect S |
| $`R \setminus S`$ | R - S | R - S |
| $`{}_{a} 𝔉_{\text{count} ( b )} ( R )`$ | γ a; count(b)→n (R) | gamma a; count(b)->n (R) |
| $`𝔉_{\text{max} ( p )} ( R )`$ | γ max(p)→m (R) | gamma max(p)->m (R) |
| ∧, ∨, ¬, ≠, ≤, ≥ | ∧, ∨, ¬, ≠, ≤, ≥ | and, or, not, !=, <=, >= |


RelaX needs a name for every aggregate (the part after →); in the lecture notation you name it with ρ. For intermediate results, write one assignment per line (`A = σ city = 'AMS' (Listing)`) and the final expression on the last line, as in the lecture.

## The data

**Host** (6 tuples)

| hid | hname |
|---|---|
| H1 | Ada |
| H2 | Bram |
| H3 | Cleo |
| H4 | Dirk |
| H5 | Eva |
| H6 | Floor |


**Listing** (14 tuples)

| lid | hid | city | price |
|---|---|---|---|
| L1 | H1 | AMS | 95 |
| L2 | H1 | AMS | 140 |
| L3 | H1 | RTM | 85 |
| L4 | H2 | RTM | 70 |
| L5 | H2 | UTR | 90 |
| L6 | H3 | AMS | 85 |
| L7 | H3 | AMS | 210 |
| L8 | H4 | UTR | 75 |
| L9 | H4 | AMS | 85 |
| L10 | H4 | RTM | 95 |
| L11 | H5 | AMS | 130 |
| L12 | H5 | AMS | 180 |
| L13 | H3 | UTR | 100 |
| L14 | H3 | RTM | 120 |


**Guest** (12 tuples)

| gid | gname |
|---|---|
| G1 | Noor |
| G2 | Luca |
| G3 | Emma |
| G4 | Sam |
| G5 | Daan |
| G6 | Yara |
| G7 | Sam |
| G8 | Mehmet |
| G9 | Fleur |
| G10 | Lotte |
| G11 | Noor |
| G12 | Tim |


**Booking** (29 tuples)

| bid | lid | gid |
|---|---|---|
| B1 | L1 | G1 |
| B2 | L3 | G1 |
| B3 | L1 | G2 |
| B4 | L2 | G2 |
| B5 | L3 | G2 |
| B6 | L1 | G5 |
| B7 | L2 | G5 |
| B8 | L3 | G5 |
| B9 | L2 | G4 |
| B10 | L2 | G4 |
| B11 | L4 | G3 |
| B12 | L6 | G3 |
| B13 | L5 | G6 |
| B14 | L8 | G6 |
| B15 | L9 | G7 |
| B16 | L10 | G7 |
| B17 | L13 | G8 |
| B18 | L14 | G8 |
| B19 | L8 | G12 |
| B20 | L8 | G12 |
| B21 | L6 | G9 |
| B22 | L4 | G9 |
| B23 | L10 | G1 |
| B24 | L5 | G2 |
| B25 | L9 | G6 |
| B26 | L14 | G3 |
| B27 | L9 | G8 |
| B28 | L10 | G6 |
| B29 | L8 | G9 |


## Part 1: warm-up

### Exercise 1. The highest price

What is the highest price per night of any listing? Return one column, max_price.

<details><summary>Expected result (1 tuple)</summary>

| max_price |
|---|
| 210 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\rho_{M ( \text{max\_price} )} ( 𝔉_{\text{max} ( \text{price} )} ( \text{Listing} ) )`$

RelaX:

```
γ max(price)→max_price (Listing)
```

</details>

### Exercise 2. Cheap in Utrecht

Which hosts have a listing in Utrecht that costs less than €100 per night? Return (hid, hname).

<details><summary>Expected result (2 tuples)</summary>

| hid | hname |
|---|---|
| H2 | Bram |
| H4 | Dirk |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\pi_{\text{hid} ,\, \text{hname}} ( \text{Host} \bowtie \sigma_{\text{city} = \verb|'UTR'| \,\wedge\, \text{price} < 100} ( \text{Listing} ) )`$

RelaX:

```
π hid, hname (Host ⋈ σ city = 'UTR' ∧ price < 100 (Listing))
```

</details>

### Exercise 3. No booking at all

Which guests have never made a booking? Return gid.

<details><summary>Expected result (2 tuples)</summary>

| gid |
|---|
| G10 |
| G11 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\pi_{\text{gid}} ( \text{Guest} ) \setminus \pi_{\text{gid}} ( \text{Booking} )`$

RelaX:

```
π gid (Guest) - π gid (Booking)
```

</details>

## Part 2: exam level

### Exercise 4. Guests of Ada

Which guests booked at least one listing hosted by Ada? Return (gid, gname).

<details><summary>Expected result (4 tuples)</summary>

| gid | gname |
|---|---|
| G1 | Noor |
| G2 | Luca |
| G4 | Sam |
| G5 | Daan |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\pi_{\text{gid} ,\, \text{gname}} ( \text{Guest} \bowtie \text{Booking} \bowtie \text{Listing} \bowtie \sigma_{\text{hname} = \verb|'Ada'|} ( \text{Host} ) )`$

RelaX:

```
π gid, gname (Guest ⋈ Booking ⋈ Listing ⋈ σ hname = 'Ada' (Host))
```

The same with theta joins:

Lecture notation:

$`\pi_{\text{Guest.gid} ,\, \text{gname}} ( \text{Guest} \bowtie_{\text{Guest.gid} = \text{Booking.gid}} ( \text{Booking} \bowtie_{\text{Booking.lid} = \text{Listing.lid}}`$\
$`\qquad ( \text{Listing} \bowtie_{\text{Listing.hid} = \text{Host.hid}} \sigma_{\text{hname} = \verb|'Ada'|} ( \text{Host} ) ) ) )`$

RelaX:

```
π Guest.gid, gname (Guest ⋈ Guest.gid = Booking.gid (Booking ⋈ Booking.lid = Listing.lid (Listing ⋈ Listing.hid = Host.hid σ hname = 'Ada' (Host))))
```

</details>

### Exercise 5. Hosts without bookings

Which hosts have at least one listing, but none of their listings has ever been booked? Return (hid, hname).

<details><summary>Expected result (1 tuple)</summary>

| hid | hname |
|---|---|
| H5 | Eva |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`N = \pi_{\text{hid}} ( \text{Listing} ) \setminus \pi_{\text{hid}} ( \text{Listing} \bowtie \text{Booking} )`$\
$`\pi_{\text{hid} ,\, \text{hname}} ( \text{Host} \bowtie N )`$

RelaX:

```
N = π hid (Listing) - π hid (Listing ⋈ Booking)
π hid, hname (Host ⋈ N)
```

</details>

### Exercise 6. Bookings per guest

For every guest with at least one booking, how many bookings did they make? Return (gid, gname, n), where n is the number of bookings.

<details><summary>Expected result (10 tuples)</summary>

| gid | gname | n |
|---|---|---|
| G1 | Noor | 3 |
| G2 | Luca | 4 |
| G3 | Emma | 3 |
| G4 | Sam | 2 |
| G5 | Daan | 3 |
| G6 | Yara | 4 |
| G7 | Sam | 2 |
| G8 | Mehmet | 3 |
| G9 | Fleur | 3 |
| G12 | Tim | 2 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`C = \rho_{C ( \text{gid} ,\, n )} ( {}_{\text{gid}} 𝔉_{\text{count} ( \text{bid} )} ( \text{Booking} ) )`$\
$`\pi_{\text{gid} ,\, \text{gname} ,\, n} ( \text{Guest} \bowtie C )`$

RelaX:

```
C = ρ C (γ gid; count(bid)→n (Booking))
π gid, gname, n (Guest ⋈ C)
```

</details>

### Exercise 7. Amsterdam and Utrecht

Which guests booked a listing in Amsterdam and also a listing in Utrecht? Return (gid, gname).

<details><summary>Expected result (4 tuples)</summary>

| gid | gname |
|---|---|
| G2 | Luca |
| G6 | Yara |
| G8 | Mehmet |
| G9 | Fleur |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`A = \pi_{\text{gid}} ( \text{Booking} \bowtie \sigma_{\text{city} = \verb|'AMS'|} ( \text{Listing} ) )`$\
$`U = \pi_{\text{gid}} ( \text{Booking} \bowtie \sigma_{\text{city} = \verb|'UTR'|} ( \text{Listing} ) )`$\
$`\pi_{\text{gid} ,\, \text{gname}} ( \text{Guest} \bowtie ( A \cap U ) )`$

RelaX:

```
A = π gid (Booking ⋈ σ city = 'AMS' (Listing))
U = π gid (Booking ⋈ σ city = 'UTR' (Listing))
π gid, gname (Guest ⋈ (A ∩ U))
```

</details>

### Exercise 8. The cheapest listing in each city

Which listing is the cheapest in its city? Return (city, lid, price) for every city. If two listings in a city share the lowest price, return both.

<details><summary>Expected result (4 tuples)</summary>

| city | lid | price |
|---|---|---|
| AMS | L6 | 85 |
| AMS | L9 | 85 |
| RTM | L4 | 70 |
| UTR | L8 | 75 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`M = \rho_{M ( \text{city} ,\, \text{min\_price} )} ( {}_{\text{city}} 𝔉_{\text{min} ( \text{price} )} ( \text{Listing} ) )`$\
$`\pi_{\text{Listing.city} ,\, \text{lid} ,\, \text{price}} ( \text{Listing} \bowtie_{\text{Listing.city} = M\text{.city} \,\wedge\, \text{Listing.price} = M\text{.min\_price}} M )`$

RelaX:

```
M = ρ M (γ city; min(price)→min_price (Listing))
π Listing.city, lid, price (Listing ⋈ Listing.city = M.city ∧ Listing.price = M.min_price M)
```

</details>

## Part 3: harder

### Exercise 9. Bookings per host, including zero

For every host, how many bookings were made for their listings? Hosts without any booking appear with 0. Return (hid, hname, n).

<details><summary>Expected result (6 tuples)</summary>

| hid | hname | n |
|---|---|---|
| H1 | Ada | 10 |
| H2 | Bram | 4 |
| H3 | Cleo | 5 |
| H4 | Dirk | 10 |
| H5 | Eva | 0 |
| H6 | Floor | 0 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\text{LB} = \rho_{\text{LB}} ( \text{Listing} \bowtie \text{Booking} )`$\
$`J = \text{Host} \mathrel{⟕}_{\text{Host.hid} = \text{LB.hid}} \text{LB}`$\
$`\rho_{\text{HostCounts} ( \text{hid} ,\, \text{hname} ,\, n )} ( {}_{\text{Host.hid} ,\, \text{hname}} 𝔉_{\text{count} ( \text{bid} )} ( J ) )`$

RelaX:

```
LB = ρ LB (Listing ⋈ Booking)
J = Host ⟕ Host.hid = LB.hid LB
ρ HostCounts (γ Host.hid, hname; count(bid)→n (J))
```

Also correct, with two left outer joins:

Lecture notation:

$`J = ( \text{Host} \mathrel{⟕}_{\text{Host.hid} = \text{Listing.hid}} \text{Listing} ) \mathrel{⟕}_{\text{Listing.lid} = \text{Booking.lid}} \text{Booking}`$\
$`\rho_{\text{HostCounts} ( \text{hid} ,\, \text{hname} ,\, n )} ( {}_{\text{Host.hid} ,\, \text{hname}} 𝔉_{\text{count} ( \text{bid} )} ( J ) )`$

RelaX:

```
J = (Host ⟕ Host.hid = Listing.hid Listing) ⟕ Listing.lid = Booking.lid Booking
ρ HostCounts (γ Host.hid, hname; count(bid)→n (J))
```

</details>

### Exercise 10. Two different listings

Which guests booked at least two different listings? Answer without grouping or counting. Return gid.

<details><summary>Expected result (8 tuples)</summary>

| gid |
|---|
| G1 |
| G2 |
| G3 |
| G5 |
| G6 |
| G7 |
| G8 |
| G9 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\pi_{\text{B1.gid}} ( \sigma_{\text{B1.gid} = \text{B2.gid} \,\wedge\, \text{B1.lid} \neq \text{B2.lid}} ( \rho_{\text{B1}} ( \text{Booking} ) \times \rho_{\text{B2}} ( \text{Booking} ) ) )`$

RelaX:

```
π B1.gid (σ B1.gid = B2.gid ∧ B1.lid ≠ B2.lid (ρ B1 (Booking) ⨯ ρ B2 (Booking)))
```

</details>

### Exercise 11. Pairs in Rotterdam

Which pairs of different guests booked the same listing in Rotterdam? Return each pair once, with the smaller gid first, as (gid1, gid2). The gid values are text, so "smaller" is alphabetical order.

<details><summary>Expected result (8 tuples)</summary>

| gid1 | gid2 |
|---|---|
| G1 | G2 |
| G1 | G5 |
| G1 | G6 |
| G1 | G7 |
| G2 | G5 |
| G3 | G8 |
| G3 | G9 |
| G6 | G7 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`R = \pi_{\text{gid} ,\, \text{lid}} ( \text{Booking} \bowtie \sigma_{\text{city} = \verb|'RTM'|} ( \text{Listing} ) )`$\
$`\rho_{( \text{gid1} ,\, \text{gid2} )} ( \pi_{A\text{.gid} ,\, B\text{.gid}} ( \sigma_{A\text{.lid} = B\text{.lid} \,\wedge\, A\text{.gid} < B\text{.gid}} ( \rho_{A} ( R ) \times \rho_{B} ( R ) ) ) )`$

RelaX:

```
R = π gid, lid (Booking ⋈ σ city = 'RTM' (Listing))
ρ gid1←A.gid, gid2←B.gid (π A.gid, B.gid (σ A.lid = B.lid ∧ A.gid < B.gid (ρ A (R) ⨯ ρ B (R))))
```

</details>

### Exercise 12. Every listing booked

In which cities has every listing been booked at least once? Return city.

<details><summary>Expected result (2 tuples)</summary>

| city |
|---|
| RTM |
| UTR |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`U = \pi_{\text{lid}} ( \text{Listing} ) \setminus \pi_{\text{lid}} ( \text{Booking} )`$\
$`\pi_{\text{city}} ( \text{Listing} ) \setminus \pi_{\text{city}} ( \text{Listing} \bowtie U )`$

RelaX:

```
U = π lid (Listing) - π lid (Booking)
π city (Listing) - π city (Listing ⋈ U)
```

</details>

### Exercise 13. Every listing of Ada

Which guests booked every listing hosted by Ada? Return (gid, gname).

<details><summary>Expected result (2 tuples)</summary>

| gid | gname |
|---|---|
| G2 | Luca |
| G5 | Daan |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`A = \pi_{\text{lid}} ( \text{Listing} \bowtie \sigma_{\text{hname} = \verb|'Ada'|} ( \text{Host} ) )`$\
$`G = \pi_{\text{gid}} ( \text{Booking} )`$\
$`\text{Missing} = ( G \times A ) \setminus \pi_{\text{gid} ,\, \text{lid}} ( \text{Booking} )`$\
$`\pi_{\text{gid} ,\, \text{gname}} ( \text{Guest} \bowtie ( G \setminus \pi_{\text{gid}} ( \text{Missing} ) ) )`$

RelaX:

```
A = π lid (Listing ⋈ σ hname = 'Ada' (Host))
G = π gid (Booking)
Missing = (G ⨯ A) - π gid, lid (Booking)
π gid, gname (Guest ⋈ (G - π gid (Missing)))
```

$`G`$ can also be $`\pi_{\text{gid}} ( \text{Guest} )`$: a guest without any booking misses all of Ada's listings, so the result is the same.

</details>

### Exercise 14. The busiest host

Which host has the most bookings over all of their listings? If several hosts share the highest number, return all of them. Return (hid, hname, n).

<details><summary>Expected result (2 tuples)</summary>

| hid | hname | n |
|---|---|---|
| H1 | Ada | 10 |
| H4 | Dirk | 10 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`C = \rho_{C ( \text{hid} ,\, n )} ( {}_{\text{hid}} 𝔉_{\text{count} ( \text{bid} )} ( \text{Listing} \bowtie \text{Booking} ) )`$\
$`M = \rho_{M ( m )} ( 𝔉_{\text{max} ( n )} ( C ) )`$\
$`\pi_{\text{hid} ,\, \text{hname} ,\, n} ( \text{Host} \bowtie ( C \bowtie_{n = m} M ) )`$

RelaX:

```
C = ρ C (γ hid; count(bid)→n (Listing ⋈ Booking))
M = ρ M (γ max(n)→m (C))
π hid, hname, n (Host ⋈ (C ⋈ n = m M))
```

</details>

## Part 4: read, translate, repair

### Exercise 15. Read an expression

Describe in one sentence what this expression returns, and give its result. Does the result contain every guest who never booked a listing in Amsterdam? If not, which guests are missing, and why?

$`\pi_{\text{gid}} ( \text{Booking} ) \setminus \pi_{\text{gid}} ( \text{Booking} \bowtie \sigma_{\text{city} = \verb|'AMS'|} ( \text{Listing} ) )`$

<details><summary>Expected result (1 tuple)</summary>

| gid |
|---|
| G12 |

</details>

<details><summary>Solution</summary>

The expression returns the gid of every guest who made at least one booking, but none in Amsterdam: G12. G10 and G11 are missing, although they never booked in Amsterdam either. They never made any booking, and the expression starts from $`\pi_{\text{gid}} ( \text{Booking} )`$, not from $`\pi_{\text{gid}} ( \text{Guest} )`$.

RelaX:

```
π gid (Booking) - π gid (Booking ⋈ σ city = 'AMS' (Listing))
```

</details>

### Exercise 16. From SQL to algebra

Write this SQL query in relational algebra, and give its result.

```sql
SELECT l.city, COUNT(b.bid) AS n
FROM Listing AS l
JOIN Booking AS b ON b.lid = l.lid
GROUP BY l.city
HAVING COUNT(b.bid) >= 10;
```

<details><summary>Expected result (2 tuples)</summary>

| city | n |
|---|---|
| AMS | 12 |
| RTM | 10 |

</details>

<details><summary>Solution</summary>

Lecture notation:

$`\sigma_{n \geq 10} ( \rho_{\text{CityCounts} ( \text{city} ,\, n )} ( {}_{\text{city}} 𝔉_{\text{count} ( \text{bid} )} ( \text{Listing} \bowtie \text{Booking} ) ) )`$

RelaX:

```
σ n ≥ 10 (ρ CityCounts (γ city; count(bid)→n (Listing ⋈ Booking)))
```

HAVING becomes the selection $`\sigma_{n \geq 10}`$ above $`𝔉`$. A condition in WHERE would be a selection below it.

</details>

### Exercise 17. Find the mistake

A student answers the question "Which guests have never made a booking? Return their names." with the expression below. Which guest is missing from its result, and why? Write an expression that returns (gid, gname) of all guests without a booking.

$`\pi_{\text{gname}} ( \text{Guest} ) \setminus \pi_{\text{gname}} ( \text{Guest} \bowtie \text{Booking} )`$

<details><summary>Expected result (2 tuples)</summary>

The student's expression returns 1 tuple: (Lotte). The correct answer:

| gid | gname |
|---|---|
| G10 | Lotte |
| G11 | Noor |

</details>

<details><summary>Solution</summary>

G11 (Noor) is missing. The expression subtracts names, and G1, who has bookings, is also called Noor, so the name Noor is removed. Subtract the gid values instead, then join with Guest to get the names:

Lecture notation:

$`\pi_{\text{gid} ,\, \text{gname}} ( \text{Guest} \bowtie ( \pi_{\text{gid}} ( \text{Guest} ) \setminus \pi_{\text{gid}} ( \text{Booking} ) ) )`$

RelaX:

```
π gid, gname (Guest ⋈ (π gid (Guest) - π gid (Booking)))
```

</details>

## When your result differs

- Check the attributes: does your result have exactly the columns the question asks for?
- Check every join: which attributes does each natural join match?
- For "never", "none" and "every": which relation holds all candidates, and what do you subtract from it?
- For counts: what does one tuple represent when you group, and did an earlier projection merge two tuples?
- Keep the IDs until the end: two guests with the same name become one tuple once gid is gone.
