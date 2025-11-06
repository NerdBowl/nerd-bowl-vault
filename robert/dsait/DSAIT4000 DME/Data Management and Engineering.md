
Lecture 1: Introduction
- Relational databases organize data into tables, between which relationships may be defined. 

Lecture 2: Data models
- The domain of discourse is the set of all possible objects, entities, or concepts relevant to a specific argument, discussion, or logical statement.
- Schema design is about going from the domain of discourse through:
	- conceptual design: What do we need to store (Entities), and how are things related (Relationships)? -> Conceptual Schema
	- logical design: Adapt conceptual design to the Data Model (e.g. relational) used by the database. -> Logical Schema.
	- physical design: Implementing the logical design for a particular database.
- Database: Collection of related data represented using a data model and a data schema.
- Database Management System (DBMS): A software system managing and maintaining a database.
- Data Model: A formal definition of how to represent data (in general) and the available data operations. Three components: 
	- Structure (Data Structures used), 
	- Integrity (Constraints on data structures to ensure integrity), 
	- Manipulation (Options for data querying and manipulation).
	- Examples:
		- The Relational Data model. Entities are tables, linked using foreign keys, queried using SQL.
		- Single Table Model. High redundancy. 
		- Document Model. Semi-structured text documents. JSON, or XML. 
- Data Schema: A definition of the specific structure of a database.
- Entity Relationship diagram: conceptual schema describing entities and their relationships. Examples: Chen-ER, ER Crow's Foot Notation, ER Baker Notation, UML. 
- Ontology tries to describe everything which is (exists), and its relation and categorization with respect to other things in existence.
- Functional dependencies: define which (set of) attributes are dependent on which other (set of) other attributes. Candidate keys are the subsets of attributes that fully define all others for a tuple. Primary keys are the chosen candidate keys to unique identify the tuple.
	- Example: Postal code + House number in the Netherlands.
- A weak entity is an entity that is co-identified by another (strong) entity. 
- ER (Entity-Relationship) Diagrams:
	- Entity Types: Classes of objects having common properties and autonomous existence.
	- Relationship Types: Binary (Relates two entities), Ternary (Relates three entities), Recursive (Relates an entity to another of the same entity type).
	- Cardinality: describes the maximum and minimum number of relationship occurrences in which an entity can participate.
		- Maximum (Cardinality Ratio): 1 (at most one), N (any number)
		- Minimum (Participation Constraint): 0 (optional), 1 (mandatory or total)
	- Attributes: describe the elementary properties of entities or relationships. May also have some cardinality. May be composites (combination of attributes), or derived (from other attributes, ex. age from Birth Date).
	- Weak Entities: Sometimes the attributes of an entity are not sufficient to identify its occurrences unambiguously. Other entities are involved in identification. The relationship relating an entity to its owner is the identifying relationship.
	![[Pasted image 20251106140544.png]]
- EER (Enhanced-ER) is an extension of ER that allows for more complex requirements:
	- Specialization (top-down): You define specific subgroups (subclasses) for a general entity.
	- Generalization (bottom-up): You find several entities with common features and create a new more general entity (a superclass). 
	- Disjoint vs Overlapping: An instance of a superclass can be in only one subclass (disjoint) or in multiple (overlapping).
	- Total vs Partial: Every instance of the superclass belongs to at least one subclass (total), or some instances may just belong to the superclass (partial).
	- Category (or union type): A category models an entity (subclass) that is a union of different superclasses. 
- Aggregate Data: Treat a collection of related data as a single unit. This is different from the relational model which encourages to decompose into multiple separate tables. Examples:
	- Key-value models: Treat each of the aggregates as a value, accessible only by a unique key.
	- Document models: Key-value, but the values follow a specified structure allowing queries on data inside the aggregate (e.g. JSON, XML)
	- Column-Family Models: store data in a large, sparse table where a row key identifies an aggregate and "column families" group related data within that aggregate.

Lecture 3: Discovering Data
- SQL: Declarative Language: Describes the desired result without specifying how to compute it.
- Relational Algebra: Procedural Language: Shows step-by-step procedure for computing the result. Components:
	- Basic: Selection $\sigma$, Projection $\pi$, Rename $\rho$, Union $\cup$, Intersection $\cap$, set difference $\setminus$, Cartesian product $\times$.
	- Extended: Theta-join $⋈_{(θ-\text{cond})}$, Equi-join $⋈_{(=-\text{cond})}$, Natural Join $⋈$
	- Advanced: Aggregation $\gamma$, Outer joins.
- Data Lake: flexible, scalable data storage and management system where raw data from different sources can be ingested in their original (structured or unstructured) format.
- Data Warehouses: store data in a structured format. 
- Data lake architectures:
	- Pond: partitions ingested data by their status and usage.
	- Zone architecture: Separates dataset standardization into different stages.
	- Function-based architecture: Big jumble mess
- Data Discovery: Finding relevant or related data. 
	- Data lakes use metadata to store relationships between datasets. 
	- Jaccard Similarity: $s(X,Y) = |X \cap Y| /|X \cup Y|$
	- Set containment: $t(X, Y) = |X \cap Y|/|X|$ size agnostic for $Y$
	- Set overlap: $o(X,Y)=|X\cap Y|$
- Aforementioned methods cannot be feasibly computed for large data lakes. Se we approximate, trading speed less computation for less accuracy. 
	- Local Sensitive Hashing (LSH): Similar objects wind up in the same bucket while other pairs rarely do. Steps:
		- Shingling: k-shingle for a document is a sequence of k characters that appear in the document. Compute multiple such shingles. Then create a set of all shingles that occurred in the document.
		- Min-hashing: 
			- The input matrix has a column for each of the sets, and a row for each of the possible set elements. Each element in the matrix is a zero if the set did not contain the element, and a one if it does. 
			- The min hash function $h(C)$ is the index of the first row in which column $C$ has a one. We apply the min hash function to all columns across several ($b\cdot r$) randomly chosen permutations to create a signature for each column. 
			- Result is a signature matrix where the columns are the sets, rows are the permutations, and the elements are the corresponding min hash values.
		- Locality-sensitive hashing (LSH): 
			- We divide the signature matrix into $b$ bands (of $r$ rows).
			- For each band, hash each of the columns, and divide into $k$ buckets.
		- The approximation of the Jaccard similarity is then the percentage of bands for which two sets end up in the same buckets.
	- Lazo: is an LSH index that uses OPH/MinHash, supporting both set containment and jaccard similarity, and returns similarity scores. 
	- JOSIE: Exact top-k search for finding joinable tables. Given a query column $Q$ find top-$k$ columns ($X_1, \dots X_k$) from the data lake with the highest set overlap size $|Q \cap X_i|$. JOSIE is a drop-in component utilizing inverted index for finding joinable tables.
	- 
	
Lecture 4: Obtaining Data 
Lecture 5: Data Quality and Coding
Lecture 6: Data Integration
Lecture 7: Introduction to Data Mining with Text and Graphs
Lecture 8: Storing/Retrieving Structured Data
Lecture 9: Distributing Structured Data
Lecture 10: Basics of Data Visualization
Lecture 11: Interactive Visual Data Analysis
Lecture 12: Storying/Querying Unstructured Data