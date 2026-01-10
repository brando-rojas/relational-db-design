## Question 1: Normal Forms

1A: What normal form is the following relation in (key is underlined), and Why? Make sure you provide both Answer and Reasoning:

-   STORE_ITEM (<u>SKU</u>, <u>EventID</u>, Vendor, Style, Price, Warranty)
    
    -   FD1: SKU, EventID → Vendor, Style, Price
        
    -   FD2: SKU → Vendor, Style, Warranty
        
    -   FD3: Vendor → Warranty
        
**1A:**

It is in 1NF because it is a relation.

It is not in 2NF because there is a partial FD: FD2: SKU → Vendor, Style, Warranty and SKU is part of the key (SKU, EventID)

1B: What normal form is the following relation in (key is underlined), and Why? Make sure you provide both Answer and Reasoning:

-   SKU (<u>SKU</u>, Vendor, Style, Warranty)
    
    -   FD1: SKU → Vendor, Style, Warranty
        
    -   FD2: Vendor → Warranty
 
 **1B:**

It is in 1NF because it is a relation.

It is in 2NF because there is no partial FD.

It is not in 3NF because there is a transitive FD: SKU → Vendor and Vendor → Warranty.       

1C: What normal form is the following relation in (key is underlined), and Why? Make sure you provide both Answer and Reasoning:

-   SKU (<u>SKU</u>, Vendor, Style, Warranty)
    
    -   FD1: SKU → Vendor, Style, Warranty
        
    -   FD2: Vendor, Style → Warranty
        
**1C:**

It is in 1NF because it is a relation.

It is in 2NF because there is no partial FD.

It is not in 3NF because there is a transitive SKU → Vendor, Style and Vendor, Style → Warranty.

## Question 2: Normalization Process

We have a relational model represented as a relational schema and its functional dependencies given as below:

-   TRANSCRIPT (<u>ID</u>, fName, lName, major, majorDescription, <u>courseID</u>, courseDescription, courseGrade)
    
    -   FD1: ID, courseID -> fName, lName, major, majorDescription, courseDescription, courseGrade
        
    -   FD2: ID -> fName, lName, major, majorDescription
        
    -   FD3: courseID - > curseDescription
        
    -   FD4: major -> majorDescription
        

2A: Normalize it to 2NF

**2A:**

Relation TRANSCRIPT is not in 2NF because there are partial functional dependencies:

Fd2: ID → fName, 1Name, major, majorDescription and ID is part of the key (ID, courseID)

FD3: courseID - > curseDescription and courseID is part of the key (ID, courseID).

To normalize it to 2NF, we need to create new relations:

Student(<u>ID</u>, fName, 1Name, major, majorDescription)

FD1: ID → fName, 1Name, major, majorDescription

FD2: major → majorDescription

Course(<u>courseID</u>, curseDescription)

FD1: courseID - > curseDescription

And modify the TRANSCRIPT relation to be:

TRANSCRIPT (<u>ID</u>(fk), <u>courseID</u>(fk), courseGrade)

FD1: ID, courseID → courseGrade


2B: Check all the relations you got from 2A. Are they in 3NF? If not, normalize them to 3NF.

**2B:**

Relation Course and TRANSCRIPT are in 3NF since there are no transitive functional dependencies. However, Relation Student is not in 3NF because there is a transitive functional dependency: ID → major, and major → majorDescription.

To normalize it to 3NF, we need to create a new relation:

Major(major, majorDescription)

FD1: major → majorDescription

And modify the Student to be:

Student(<u>ID</u>, fName, 1Name, major(fk))

FD1: ID → fName, 1Name, major

## Question 3: Normalization Process

You are given the following Relational Model represented as a relational schema and its functional dependencies.

Exam1(<u>A</u>, <u>B</u>, <u>C</u>, D, E, F, G, H, I)

fd1: A, B, C -> D, E, F, G, H, I

fd2: B -> E

fd3: C -> F, G, H, I

fd4: F, G -> H, I

3A: Normalize it to 2NF

**3A:**

Relation Exam1 is not in 2NF because there are partial functional dependencies:

Fd2: B → E and B is part of the key (A, B, C)

FD3: C → F, G, H, I and C is part of the key (A, B, C).

To normalize it to 2NF, we need to create new relations:

Relation1(<u>B</u>, E)

Fd1: B → E

Relation2(<u>C</u>, F, G, H, I)

Fd1: C → F, G, H, I

Fd2: F, G → H, I

And modify the Exam1 to be:

Exam1(<u>A</u>, <u>B</u>(fk), <u>C</u>(fk), D)

fd1: A, B, C → D

In summary, we now have a relational model in 2NF as:

Exam1(<u>A</u>, <u>B</u>(fk), <u>C</u>(fk), D)

fd1: A, B, C → D

Relation1(<u>B</u>, E)

Fd1: B → E

Relation2(<u>C</u>, F, G, H, I)

Fd1: C → F, G, H, I

Fd2: F, G → H, I

3B: Check all the relations you got from 3A. Are they in 3NF? If not, normalize them to 3NF.

**3B:**

Relation 1 and Exam 1 are in 3NF. Relation2 is not in 3NF because there is a transitive functional dependency: Fd1: C → F, G and FD2: F, G → H.

To normalize it to 3NF, we need to create a new relation:

Relation3(<u>F</u>, <u>G</u>, H, I)

Fd1: F, G → H, I

And modify the Relation2 to be:

Relation2(<u>C</u>, F(fk), G(fk))

Fd1: C → F, G

Relation2, 3 are in 3NF.

In summary, we now have a relational model in 3NF as:

Exam1(<u>A</u>, <u>B</u>(fk), <u>C</u>(fk), D)

fd1: A, B, C → D

Relation1(<u>B</u>, E)

Fd1: B → E

Relation2(<u>C</u>, F(fk), G(fk))

Fd1: C → F, G

Relation3(<u>F</u>, <u>G</u>, H, I)

Fd1: F, G → H, I