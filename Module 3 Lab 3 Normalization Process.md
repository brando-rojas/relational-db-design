# Identify Normalization Form:

You have identified the special functional dependencies in Lab2. Now you learned how to determine the normalization form of a relation based on the presense of the special functional dependencies. Revist the following relations in Lab 2 and determine the Normal Form they are in:

# Relation 1

Which normal form is the relational model below?

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

## Answer

It is in 1NF, since it is a relation.
It is in 2NF too, since there is no partial FD.
It is in 3NF, since there is no transitive FD.

# Relation 2

Which normal form is the relational model below?

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

fd2: D -> L, N, Q

fd3: L -> N

## Answer


It is in 1NF, since it is a relation.

It is in 2NF too, since there is no partial FD.

It is not in 3NF, since there is a transitive FD: A, B, C -> D, and D -> L.

# Relation 3

Which normal form is the relational model below?

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

fd2: A -> D, E, F, L, N, Q

fd3: B, C -> G, H

fd4: D -> L, N, Q

fd5: L -> N

## Answer

It is in 1NF, since it is a relation.

It is not in 2NF, since there are partial FDs: A is part of (A B C) -> D E F L N G, also B C is part of (ABC) -> GH

# Relation 4

Which normal form is the relational model below?

CustomerContact (FirstName, LastName, DoB, Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo)

fd1: FirstName, LastName, DoB -> Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo

fd2: LastName, DoB → Email

fd3: DoB → Zodiac

fd4: Zip → City, State

fd5: Company → CompanyInfo

## Answer 

It is in 1NF, since it is a relation.

It is in not 2NF, since there is a partial FD: DoB is part of (Firstname, LastName, DoB) -> Zodiac.

# Normalization Process:

# Relational Model 1

Given the relational model below, normalize it to 3NF. Make sure you list the Functional Dependencies along with each relation, and include all relations (each relation with its functional dependencies) in the summary.

Customers (<u>CID</u>, FirstName, LastName, Email, Address, Company, CompanyInfo)

FD1: CID → FirstName, LastName, Email, Address, Company, CompanyInfo

FD2: Company → CompanyInfo

## Answer

Customers relation is in 1NF since it is a relation.

It is in 2NF, since there is no partial functional dependency.

However, it is NOT in 3NF, since from FD1, we know CID → Company, and from FD2, we know Company → CompanyInfo, this is a transitive functional dependency.

To normalize it to 3NF, we need to:

Create a new relation:

CompanyInfo(<u>Company</u>, CompanyInfo)

FD1: Company → CompanyInfo

Modify the Customers relation by removing CompanyInfo:

Customers (<u>CID</u>, FirstName, LastName, Email, Address, Company (fk))

FD1: CID → FirstName, LastName, Email, Address, Company

Now we have two relations, and they are all in 3NF.

# Relational Model 2

Given the relational model below, normalize it to 3NF. Make sure you list the Functional Dependencies along with each relation, and include all relations (each relation with its functional dependencies) in the summary.

CustomerContact (<u>FirstName</u>, <u>LastName</u>, <u>DoB</u>, Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo)

fd1: FirstName, LastName, DoB → Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo

fd2: LastName, DoB → Email

fd3: DoB → Zodiac

fd4: Zip → City, State

fd5: Company → CompanyInfo

## Answer

1NF:

It is in 1NF because it is a relation

2NF:

It is not in 2NF because there are partial dependencies:

fd2: LastName, DoB -> Email and (LastName, DoB) is part of the key (FirstName, LastName, DoB)

fd3: DoB -> Zodiac and DoB is part of the key (FirstName, LastName, DoB).

To normalize it to 2NF, we should:

Create new relations:

Email(<u>LastName</u>, <u>DoB</u>, Email)

fd1: LastName, DoB -> Email

Zodiac(<u>DoB</u>, Zodiac)

fd1: DoB -> Zodiac

And modify the CustomerContact relation to be:

CustomerContact (<u>FirstName</u>, <u>LastName</u>(fk), <u>DoB</u>(fk), Street, County, City, State, Zip, Company, CompanyInfo)

fd1: FirstName, LastName, DoB -> Street, County, City, State, Zip, Company, CompanyInfo

fd2: Zip -> City, State

fd3: Company -> CompanyInfo

In summary, we have a relational model in 2NF as below:

CustomerContact (<u>FirstName</u>, <u>LastName</u>(fk), <u>DoB</u>(fk), Street, County, City, State, Zip, Company, CompanyInfo)

fd1: FirstName, LastName, DoB -> Street, County, City, State, Zip, Company, CompanyInfo

fd2: Zip -> City, State

fd3: Company -> CompanyInfo

Email(<u>LastName</u>, <u>DoB</u>, Email)

fd1: LastName, DoB -> Email

Zodiac(<u>DoB</u>, Zodiac)

fd1: DoB -> Zodiac

3NF:

It is not in 3NF because there are transitive dependencies:

fd1: FirstName, LastName, DoB -> Zip and fd2: Zip -> City, State

fd1: FirstName, LastName, DoB -> Company fd3: Company -> CompanyInfo

To normalize it to 3NF, we should create new relations:

Zip (<u>Zip</u>, City, State)

fd1: Zip -> City, State

Company (<u>Company</u>, CompanyInfo)

fd1: Company -> CompanyInfo

And modify the CustomerContact relation to be:

CustomerContact (<u>FirstName</u>, <u>LastName</u>(fk), <u>DoB</u>(fk), Street, County, Zip(fk), Company(fk))

fd1: FirstName, LastName, DoB -> Street, County, Zip, Company

In summary, we have a relational model in 3NF as below:

CustomerContact (<u>FirstName</u>, <u>LastName</u>(fk), <u>DoB</u>(fk), Street, County, Zip(fk), Company(fk))

fd1: FirstName, LastName, DoB -> Street, County, Zip, Company

Zip (<u>Zip</u>, City, State)

fd1: Zip -> City, State

Company (<u>Company</u>, CompanyInfo)

fd1: Company -> CompanyInfo

Email(<u>LastName</u>, <u>DoB</u>, Email)

fd1: LastName, DoB -> Email

Zodiac(<u>DoB</u>, Zodiac)

fd1: DoB -> Zodiac

# Relational Model 3

Given the relational model below, normalize it to 3NF. Make sure you list the Functional Dependencies along with each relation, and include all relations (each relation with its functional dependencies) in the summary.

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

fd1: A, B, C → D, E, F, G, H, I, J, K, L, N, Q

fd2: A → D, E, F, L, N, Q

fd3: B, C → G, H

fd4: D → L, N, Q

fd5: L → N

fd6: G → H

## Answer

1NF:

It is in 1NF because it is a relation

2NF:

It is not in 2NF because there are partial functional dependencies:

fd2: A-> D, E, F, L, N, Q and A is part of the key (A, B, C)

fd3: B, C -> G, H and (B, C) is part of the key (A, B, C)

To normalize it to 2NF, we should create new relations:

Relation1(<u>A</u>, D, E, F, L, N, Q)

fd1: A -> D, E, F, L, N, Q

fd2: D -> L, N, Q

fd3: L -> N

Relation2(<u>B</u>, <u>C</u>, G, H)

fd1: B, C -> G, H

fd2: G -> H

and modify the Assignments to be:

Assignments(<u>A</u>(fk), <u>B</u>(fk), <u>C</u>(fk), I, J, K)

fd1: A, B, C -> I, J, K

In summary, we have a relational model in 2NF as below:

Assignments(<u>A</u>(fk), <u>B</u>(fk), <u>C</u>(fk), I, J, K)

fd1: A, B, C -> I, J, K

Relation1(<u>A</u>, D, E, F, L, N, Q)

fd1: A -> D, E, F, L, N, Q

fd2: D -> L, N, Q

fd3: L -> N

Relation2(<u>B</u>, <u>C</u>, G, H)

fd1: B, C -> G, H

fd2: G -> H

3NF:

Relation1 is not in 3NF. Because there is a transitive functional dependency:

fd1: A -> D and fd2: D->L, N, Q.

To normalize it to 3NF, we should create a new relation

Relation3(<u>D</u>, L, N, Q)

fd1: D->L, N, Q

fd2: L -> N

And modify Relation1 to be:

Relation1(<u>A</u>, D(fk), E, F)

fd1: A -> D, E, F

However, Relation3 is still not in 3NF, because there is a transitive functional dependency:

fd1: D->L and fd2: L -> N

To normalize it to 3NF, we should create new relation:

Relation4(<u>L</u>, N)

fd1: L -> N

and modify Relation3 to be:

Relation3(<u>D</u>, L(fk), Q)

fd1: D->L, Q

Relation 2 is not in 3NF, because there is a transitive functional dependency:

fd1: B, C -> G and fd2: G -> H

To normalize it to 3NF, we should create a new relation:

Relation5(<u>G</u>, H)

fd1: G -> H

and modify Relation 2 to be:

Relation2(<u>B</u>, <u>C</u>, G(fk))

fd1: B, C -> G

In summary, we have a relational model in 3NF as below:

Assignments(<u>A</u>(fk), <u>B</u>(fk), <u>C</u>(fk), I, J, K)

fd1: A, B, C -> I, J, K

Relation1(<u>A</u>, D(fk), E, F)

fd1: A -> D, E, F

Relation2(<u>B</u>, <u>C</u>, G(fk))

fd1: B, C -> G

Relation3(<u>D</u>, L(fk), Q)

fd1: D->L, Q

Relation4(<u>L</u>, N)

fd1: L -> N

Relation5(<u>G</u>, H)

fd1: G -> H