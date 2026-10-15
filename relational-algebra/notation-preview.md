# Temporary rendering test (not for students)

## A. Display math, exercise 9

```math
\begin{array}{l}
\mathrm{LB} = \rho_{\mathrm{LB}}(\mathrm{Listing} \bowtie \mathrm{Booking})\\
J = \mathrm{Host} \mathrel{⟕}_{\mathrm{Host.hid} = \mathrm{LB.hid}} \mathrm{LB}\\
\rho_{\mathrm{HostCounts}(\mathrm{hid},\,\mathrm{hname},\,n)}({}_{\mathrm{Host.hid},\,\mathrm{hname}}\mathfrak{F}_{\mathrm{count}(\mathrm{bid})}(J))
\end{array}
```

## B. Inline math lines, exercise 9

$`\mathrm{LB} = \rho_{\mathrm{LB}}(\mathrm{Listing} \bowtie \mathrm{Booking})`$\
$`J = \mathrm{Host} \mathrel{⟕}_{\mathrm{Host.hid} = \mathrm{LB.hid}} \mathrm{LB}`$\
$`\rho_{\mathrm{HostCounts}(\mathrm{hid},\,\mathrm{hname},\,n)}({}_{\mathrm{Host.hid},\,\mathrm{hname}}\mathfrak{F}_{\mathrm{count}(\mathrm{bid})}(J))`$

## C. Quotes and underscores, exercises 2 and 8

1. text: $`\sigma_{\mathrm{city} = \text{'UTR'} \,\wedge\, \mathrm{price} < 100}(\mathrm{Listing})`$
2. texttt: $`\sigma_{\mathrm{city} = \texttt{'UTR'}}(\mathrm{Listing})`$
3. mathrm: $`\sigma_{\mathrm{city} = \mathrm{'UTR'}}(\mathrm{Listing})`$
4. verb: $`\sigma_{\mathrm{city} = \verb|'UTR'|}(\mathrm{Listing})`$
5. underscore: $`\pi_{\mathrm{Listing.city},\,\mathrm{lid},\,\mathrm{price}}(\mathrm{Listing} \bowtie_{\mathrm{Listing.city} = M.\mathrm{city} \,\wedge\, \mathrm{Listing.price} = M.\mathrm{min\_price}} M)`$

## D. Left outer join

1. mathrel: $`R \mathrel{⟕}_{p} S`$
2. plain: $`R ⟕_{p} S`$
3. unicode: $`R \mathrel{\unicode{x27D5}}_{p} S`$
4. bowtie for comparison: $`R \bowtie_{p} S`$

## E. Table

| Lecture | RelaX |
|---|---|
| $`\sigma_{p}(R)`$ | σ p (R) |
| $`{}_{a}\mathfrak{F}_{\mathrm{count}(b)}(R)`$ | γ a; count(b)→n (R) |
| $`R \mathrel{⟕}_{p} S`$ | R ⟕ p S |

## F. Long formula, exercise 4 with theta joins

```math
\pi_{\mathrm{Guest.gid},\,\mathrm{gname}}(\mathrm{Guest} \bowtie_{\mathrm{Guest.gid} = \mathrm{Booking.gid}} (\mathrm{Booking} \bowtie_{\mathrm{Booking.lid} = \mathrm{Listing.lid}} (\mathrm{Listing} \bowtie_{\mathrm{Listing.hid} = \mathrm{Host.hid}} \sigma_{\mathrm{hname} = \text{'Ada'}}(\mathrm{Host}))))
```

$`\pi_{\mathrm{Guest.gid},\,\mathrm{gname}}(\mathrm{Guest} \bowtie_{\mathrm{Guest.gid} = \mathrm{Booking.gid}} (\mathrm{Booking} \bowtie_{\mathrm{Booking.lid} = \mathrm{Listing.lid}} (\mathrm{Listing} \bowtie_{\mathrm{Listing.hid} = \mathrm{Host.hid}} \sigma_{\mathrm{hname} = \text{'Ada'}}(\mathrm{Host}))))`$

## G. Grouping symbol

$`\mathfrak{F}`$ (fraktur, as on the slides), $`\mathcal{F}`$, $`\mathscr{F}`$, and in a sentence: grouping with $`\mathfrak{F}`$ works inline.

<details><summary>H. Inside a details block</summary>

Lecture notation:

```math
\begin{array}{l}
N = \pi_{\mathrm{hid}}(\mathrm{Listing}) \setminus \pi_{\mathrm{hid}}(\mathrm{Listing} \bowtie \mathrm{Booking})\\
\pi_{\mathrm{hid},\,\mathrm{hname}}(\mathrm{Host} \bowtie N)
\end{array}
```

$`N = \pi_{\mathrm{hid}}(\mathrm{Listing}) \setminus \pi_{\mathrm{hid}}(\mathrm{Listing} \bowtie \mathrm{Booking})`$\
$`\pi_{\mathrm{hid},\,\mathrm{hname}}(\mathrm{Host} \bowtie N)`$

RelaX:

```
N = π hid (Listing) - π hid (Listing ⋈ Booking)
π hid, hname (Host ⋈ N)
```

</details>
