# Collected notes relating BFO 1.1 to BFO 2

### Scattered versus connected ###

spatiotemporal region generalizes BFO 1.O by allowing both connected and non-connected spatiotemporal regions

similarly for temporal and spatial region

See http://code.google.com/p/bfo/issues/detail?id=44

### Reciprocal dependence ###

Multiple entities can be reciprocally dependent on each other, for example between color hue, saturation and brightness; such cases can also involve reciprocal generic dependence as in the case of a disposition of a key to open a lock or some equivalent lock, and of the lock to be opened by this or some equivalent key.

### Boundaries and regions ###

In BFO 1.1 the assumption was made that the external surface of a material entity such as a cell could be treated as if it were a boundary in the mathematical sense. The new document propounds the view that when we talk about external surfaces of material objects in this way then we are talking about something fiat. More generally, the focus in discussion of boundaries in BFO 2.0 is now on fiat boundaries, which means: boundaries for which there is no assumption that they coincide with physical discontinuities. The ontology of boundaries becomes more closely allied with the ontology of regions.

### Revision of treatment of spatial location ###

We generalize the treatment of ‘located\_in’ and remove the relation ‘contained\_in’.

### exists\_at ###

New relation exists\_at(e,t) added

### Relations of parthood disambiguated ###

BFO 1. distinguished between parthood among continuants and occurrents by means of the "at t" suffix used for the former; BFO2 has distinct relations: continuant\_part\_of and occurrent\_part\_of (still using the at t suffix for the former).

part\_of is no longer in BFO2,  rather we have continuant\_part\_of, occurrent\_part\_of, and temporal\_part\_of (the last is a child of occurrent\_part\_of)

See http://code.google.com/p/bfo/issues/detail?id=46