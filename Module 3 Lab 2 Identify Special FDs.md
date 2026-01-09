# Relation 1

Is there a partial functional dependency? Is there a transitive functional dependency?

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

               fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

## Answer 1

There is no partial FD.

There is no transitive FD.

# Relation 2
Is there a partial functional dependency? Is there a transitive functional dependency?

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

               fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

               fd2: D -> L, N, Q

               fd3: L -> N

## Answer 2

There is no partial FD.

There is a transitive FDs: 
- 	A, B, C →  D, and D → L; 
- 	Also, D → L and L → N

# Relation 3
Is there a partial functional dependency? Is there a transitive functional dependency?

Assignments(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I, J, K, L, N, Q)

               fd1: A, B, C -> D, E, F, G, H, I, J, K, L, N, Q

               fd2: A -> D, E, F, L, N, Q

               fd3: B, C -> G, H

               fd4: D -> L, N, Q

               fd5: L -> N

## Answer 3

There are partial FDs: A is part of (A B C) -> D E F L N G; also B C is part of (ABC) -> GH

There are transitive FDs: 
-	A, B, C → D and D → L, N, Q, 
-	D → L and L →N;  
-	A → D  and D → L 


# Relation 4
Is there a partial functional dependency? Is there a transitive functional dependency?

CustomerContact (<u>FirstName</u>, <u>LastName</u>, <u>DoB</u>, Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo)

     fd1: FirstName, LastName, DoB -> Email, Zodiac, Street, County, City, State, Zip, Company, CompanyInfo

     fd2: LastName, DoB → Email

     fd3: DoB → Zodiac

     fd4: Zip → City, State

     fd5: Company → CompanyInfo
	 
## Answer 4

There are partial FDs: DoB is part of (Firstname, LastName, DoB) → Zodiac; Also, (LastName, DoB) is part of (Firstname, LastName, DoB) → Email


There are transitive FDs: FirstName, LastName, DoB → Zip, and Zip → City, State. Also,  FirstName, LastName, DoB → Company, and Company → CompanyInfo