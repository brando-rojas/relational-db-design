# Relation 1

Given the relation below, answer the questions:

## GradeBook

| ID | Name | Major | Quiz 1 | Quiz 2 | Quiz 3 | Quiz 4 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Harry | Magic | 90 | 90 | 80 | 100 |
| 2 | Hermione | Magic | 100 | 100 | 100 | 100 |
| 7 | Ron | Magic | 80 | 100 | 70 | 100 |
| 301 | Dobby | Service | 95 | 95 | 95 | 95 |
| 302 | Severus | Education | 90 | 90 | 99 | 100 |
| 399 | Albus | Management | 100 | 100 | 99 | 100 |

Now you know ID is the primary key, and Major is the foriegn key. Write a Relational Schema to represent the relation.

**Answer**

GradeBook (<u>ID</u>, Name, Major(fk), Quiz1, Quiz2, Quiz3, Quiz4)

---

# Relation 2

For the following relation, answer the questions.

## ProductDetails

| SKU   | Name     | VendorID | Price | Date       | Quantity | Location | Description  |
|:-------|:----------|:----------|:-------|:------------|:----------|:----------|:--------------|
| KB320 | MouseMat | V1230    | 13.32 | 01/01/2019 | 3000     | A3       | Discontinued |
| YZ783 | MouseMat | V3002    | 10.00 | 03/01/2019 | 1000     | A3       | Discontinued |
| IU990 | Mouse    | V3333    | 19.00 | 12/01/2019 | 700      | A1       |              |
| IU370 | Mouse    | V3333    | 15.00 | 01/01/2020 | 500      | A1       |              |
| YZ783 | MouseMat | V3012    | 9.90  | 05/01/2020 | 1000     | A3       |              |
| YZ783 | MouseMat | V3012    | 8.90  | 05/01/2021 | 1000     | A3       |              |

Now you know (SKU, VendorID, Date) is the primary key, and VendorID is the foriegn key.  Write a Relational Schema to represent the relation.

**Answer**

ProductDetails (<u>SKU</u>,<u>VendorID (fk)</u>,<u>Date</u>, Name, Price, Quantity, Location, Description)