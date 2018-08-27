Spaces
======

Table name: `mf_newspaces`.

This table represents spaces `S_k^{new}(\Gamma_1(N), \chi)`.  We pick one representative `\chi` from each Galois orbit.

Column | Type | Notes
-------|------|------
id | bigint |
label | text | (N.k.i)
level | integer | (N)
weight | smallint | (k)
char_orbit | integer | (i) Index in the list of traces down to Q of the values of all characters of modulus N
minimal_conrey | integer | (n) The minimal Conrey index of any character in this Galois orbit
conductor | integer | Conductor of the Dirichlet character
sturm_bound | integer |
is_twist_minimal | bool |
dim | integer | Dimension of this newspace
hecke_orbit_dims | jsonb | Sorted list of dimensions of Hecke orbits
eis_dim | integer | Dimension of the eisenstein subspace of the corresponding `M_k(\Gamma_1(N), \chi)`
cusp_dim | integer | Dimension of the cuspidal space `S_k(\Gamma_1(N), \chi)`
mf_dim | integer | Dimension of `M_k(\Gamma_1(N), \chi)`

Table name: `mf_oldsubs`.

This table represents embeddings of oldspaces into cusp spaces.

Column | Type | Notes
-------|------|------
id | bigint |
space_label | text | The label for the modular form space `S_k(\Gamma_1(N), \chi)`
new_label | text | The label for the newspace `S_k^{new}(\Gamma_1(M), \psi)` that embeds

Hecke orbits
============

Table name: `mf_newforms`

Column | Type | Notes
-------|------|------
id | bigint |
label |  text | (N.k.i.x)
level | integer | (N)
weight | smallint | (k)
char_orbit | integer | (i) As above
hecke_orbit | integer | (X) The integer that is encoded into x in the label via 0=a, 1=b, 25=z, 26 = ba, 27=bb
dim | integer | the dimension of this Hecke orbit
field_poly | jsonb | list of integers giving defining polynomial for the Hecke field (standard Sage order of coefficients)
is_polredabs | bool | whether the polynomial has been reduced by Pari's `polredabs`
nf_label | text | LMFDB label for the corresponding number field (can be NULL)
analytic_rank | smallint |
is_cm | bool |
cm_disc | smallint | The discriminant of the order by which we have CM (0 if no CM)
cm_hecke_char | text | label for the Hecke character giving the CM
cm_proved | bool | Whether the CM columns are proven correct
has_inner_twist | bool | whether there is an inner twist
inner_twist | jsonb | List of integers giving the Conrey indices for the nontrivial Dirichlet characters that give inner twists
trace_an | jsonb | Traces of the Hecke eigenvalues down to Q
trace_hash | bigint | appropriate linear combination of the a_p between 2^12 and 2^13
an_exact | jsonb | List of lists of integers (to be discussed)
hecke_ring_index | integer | the index of the order generated by the Hecke eigenvalues in the maximal order

Hecke eigenvalues
=================

Table name: `mf_eigsystems`

Column | Type | Notes
-------|------|------
id | bigint |
label |  text | (N.k.i.x)
embedding | integer | index of the embedding of the Hecke field into C or R (exact specification to be discussed)
eigvals | jsonb | list of pairs of doubles