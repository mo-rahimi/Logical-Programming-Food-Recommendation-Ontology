
# Food Recommendation Ontology / Logical-Programming

## Table of Contents
- [Overview](#overview)
- [Installation and Usage](#installation-and-usage)
- [Features](#features)
- [Technical Details](#technical-details)
  - [Key Classes](#key-classes)
  - [Applying Disjoint Classes](#applying-disjoint-classes)
  - [Relationships Between Classes](#relationships-between-classes)
  - [Assigning Domain and Range to Object Properties](#assigning-domain-and-range-to-object-properties)
  - [Data Properties and Relations](#data-properties-and-relations)
  - [Property and Value Restrictions](#property-value-restrictions)
  - [Applying Closure Axiom](#applying-closure-axiom)
  - [Changing a Primitive Class to a Defined Class](#changing-a-primitive-class-to-a-defined-class)
  - [Using the Reasoner](#using-the-reasoner)
- [Applications](#applications)
- [Examples](#examples)
- [Conclusion](#conclusion)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)


## Overview
This repository contains a comprehensive food ontology written in OWL (Web Ontology Language). The primary goal of this ontology is to provide a standardized vocabulary and semantic structure for describing food products and ingredients. It aims to facilitate personalized nutritional recommendations that support healthy eating by leveraging a sophisticated framework of related concepts.

<div style="display: flex; justify-content: space-around;">
    <img src="Technical_Details/Details_Pics/metrics_pic1.png" alt="Image 1" width="32%">
    <img src="Technical_Details/Details_Pics/metrics_pic2.png" alt="Image 2" width="33%">
    <img src="Technical_Details/Details_Pics/metrics_pic3.png" alt="Image 3" width="28%">
</div>

<img src="Images/all.png" alt="Overview of the project" width="40%">

## Installation and Usage

To utilize the Food Recommendation Ontology, clone this repository to your local machine using the following command:


git clone https://github.com/mo-rahimi/Logical-Prograamming-Food-Ontology-OWL.git


Once cloned, you can open the ontology files in any OWL-compatible editor, such as Protégé, to explore and manipulate the ontology.


- Written in OWL (Web Ontology Language)
- Developed using Protégé [5.5.0]
- Installation and Usage: (https://protege.stanford.edu)

## Features
Standardized Vocabulary: Provides a common language for describing food-related concepts.
Personalized Recommendations: Facilitates tailored nutritional advice based on individual dietary needs and preferences.
Comprehensive Class Structure: Includes a wide range of classes representing dishes, ingredients, nutrients, and user preferences.
Disjoint Class Definitions: Ensures clarity in categorization by defining disjoint classes within the ontology.
Reasoning Capabilities: Supports reasoning to infer new knowledge from existing data.

## Technical Details
### Key Classes
- **Dish**: Represents a dish made from various ingredients.
- **Ingredient**: Classifies ingredients into animal-based and plant-based categories.
- **Nutrition**: Includes subclasses for carbohydrates, fats, fibers, proteins, minerals, and vitamins.
- **User**: Represents user preferences and dietary restrictions.
- **Disease**: Classifies various diseases that may affect dietary recommendations.
<img src="Images/class_pic1.png" alt="Overview of the project" width="40%">

### Applying Disjoint Classes
- Classes that cannot overlap:
  - Example: Vitamin and carbohydrate are disjoint, meaning an instance cannot be both.
<img src="Technical_Details/Details_Pics/Disjoint_pic.png" alt="Overview of the project" width="40%">


### Assigning Domain and Range to Object Properties
| Row | Object Property       | Domains         | Ranges         | Inverse of       | Characteristics |
|-----|-----------------------|-----------------|-----------------|------------------|------------------|
| 1   | hasIngredient         | Dish            | Ingredient      | isIngredientOf    | -                |
| 2   | isIngredientOf        | Ingredient      | Dish            | hasIngredient     | -                |
| 3   | hasNutrient           | Ingredients     | Nutrition       | -                | Transitive       |
| 4   | hasSpicyLevel         | Dish            | Level_Of_Spicy | -                | Functional       |
| 5   | servedAsMeal          | Dish            | Meal            | -                | -                |
| 6   | servedAsSideDish      | Dish            | Side_Dish       | -                | Functional       |
| 7   | dislikeIngredient      | User            | Ingredient      | -                | Transitive       |
| 8   | likeIngredient         | User            | Ingredient      | isLikedBy        | Transitive       |
| 9   | hasAllergyTo         | User            | Ingredient      | isAllergicTo     | -                |
| 10  | isAllergicTo         | Ingredient      | User            | hasAllergyTo     | -                |
| 11  | affectUserLife       | Disease         | User            | sufferFromDisease | -                |
| 12  | sufferFromDisease     | User            | Disease         | affectUserLife    | -                |
| 13  | helpWithDisease       | Nutrition       | Disease         | -                | -                |

The explanation for each row in the **"Assigning Domain and Range to Object Properties"** table, is provided below:

#### Explanations for Each Row

1. **hasIngredient**
   - **Domains**: Dish
   - **Ranges**: Ingredient
   - **Inverse of**: isIngredientOf
   - **Characteristics**: Inverse relationship
   - **Explanation**: This property indicates that a dish is composed of one or more ingredients. Each dish must have at least one ingredient associated with it, establishing a direct relationship between dishes and their ingredients. The inverse relationship, `isIngredientOf`, indicates that an ingredient can be part of one or more dishes.

2. **isIngredientOf**
   - **Domains**: Ingredient
   - **Ranges**: Dish
   - **Inverse of**: hasIngredient
   - **Characteristics**: Inverse relationship
   - **Explanation**: This property defines the relationship from the perspective of the ingredient, indicating that an ingredient can be part of a dish. It complements the `hasIngredient` property, emphasizing the bidirectional nature of the relationship between dishes and their ingredients.

3. **hasNutrient**
   - **Domains**: Ingredients
   - **Ranges**: Nutrition
   - **Inverse of**: -
   - **Characteristics**: Transitive
   - **Explanation**: This property signifies that ingredients contain various nutrients. The transitive nature means that if a dish has an ingredient, and that ingredient has a nutrient, then the dish also has that nutrient. This allows for a hierarchical understanding of nutritional content.

4. **hasSpicyLevel**
   - **Domains**: Dish
   - **Ranges**: Level_Of_Spicy
   - **Inverse of**: -
   - **Characteristics**: Functional
   - **Explanation**: This property defines the spiciness of a dish, categorizing it as either hot or mild. It is functional because each dish can only have one spiciness level; it cannot be both hot and mild simultaneously.

5. **servedAsMeal**
   - **Domains**: Dish
   - **Ranges**: Meal
   - **Inverse of**: -
   - **Characteristics**: -
   - **Explanation**: This property indicates that a dish can be served as a specific meal type, such as breakfast, lunch, or dinner. Unlike functional properties, a dish can be served in multiple meal contexts, allowing for flexibility in meal planning.

6. **servedAsSideDish**
   - **Domains**: Dish
   - **Ranges**: Side_Dish
   - **Inverse of**: -
   - **Characteristics**: Functional
   - **Explanation**: This property specifies that a dish can serve as a side dish. It is functional because a specific dish can be categorized as a side dish, but it can also fulfill other roles, such as an appetizer or dessert.

7. **dislikeIngredient**
   - **Domains**: User
   - **Ranges**: Ingredient
   - **Inverse of**: -
   - **Characteristics**: Transitive
   - **Explanation**: This property indicates that a user may dislike certain ingredients. The transitive nature implies that if a user dislikes an ingredient, they may also dislike dishes containing that ingredient.

8. **likeIngredient**
   - **Domains**: User
   - **Ranges**: Ingredient
   - **Inverse of**: isLikedBy
   - **Characteristics**: Transitive
   - **Explanation**: This property defines a user's preference for certain ingredients. Similar to the dislike property, it is transitive, meaning that if a user likes an ingredient, they may prefer dishes that include that ingredient.

9. **hasAllergyTo**
   - **Domains**: User
   - **Ranges**: Ingredient
   - **Inverse of**: isAllergicTo
   - **Characteristics**: -
   - **Explanation**: This property indicates that a user may have allergies to specific ingredients. The inverse relationship, `isAllergicTo`, highlights the potential for ingredients to cause allergic reactions in users.

10. **isAllergicTo**
    - **Domains**: Ingredient
    - **Ranges**: User
    - **Inverse of**: hasAllergyTo
    - **Characteristics**: -
    - **Explanation**: This property describes the relationship from the ingredient's perspective, indicating that certain ingredients may cause allergies in users. It complements the `hasAllergyTo` property.

11. **affectUserLife**
    - **Domains**: Disease
    - **Ranges**: User
    - **Inverse of**: sufferFromDisease
    - **Characteristics**: -
    - **Explanation**: This property indicates that certain diseases can impact a user's life. It establishes a direct relationship between diseases and users, highlighting the relevance of health conditions in dietary recommendations.

12. **sufferFromDisease**
    - **Domains**: User
    - **Ranges**: Disease
    - **Inverse of**: affectUserLife
    - **Characteristics**: -
    - **Explanation**: This property defines the relationship from the user's perspective, indicating that users may suffer from specific diseases. It complements the `affectUserLife` property, emphasizing the impact of health on dietary choices.

13. **helpWithDisease**
    - **Domains**: Nutrition
    - **Ranges**: Disease
    - **Inverse of**: -
    - **Characteristics**: -
    - **Explanation**: This property signifies that certain nutritional elements can aid in managing or alleviating specific diseases. It establishes a connection between nutrition and health conditions, emphasizing the importance of dietary considerations in treatment.


### Data Properties and Relations
| Top Data Properties    | Characteristic | Type    |
|------------------------|----------------|---------|
| hasCalorieValue        | Functional     | Integer |
| hasSaltAmountGram      | Functional     | Integer |
| hasSugarAmountGram     | Functional     | Integer |
<img src="Technical_Details/Details_Pics/data_property1.png" alt="Overview of the project" width="50%">
<img src="Technical_Details/Details_Pics/data_property3.png" alt="Overview of the project" width="50%">


### Property and Value Restrictions 
Utilizes property restrictions like existential and universal quantifiers to define complex dishes, vegan dishes, and more.
- **Complex_Dish**: Dish and (hasIngredient min 10 owl:Thing)
- **VeganDish**: Dish and (hasIngredient only PlantBasedIngredient)
- **HighProteinDish**: Dish and ((hasIngredient some Bean) or (hasIngredient some Chickpea) or (hasIngredient some Lentil) or (hasIngredient some Quinoa))
<img src="Technical_Details/Details_Pics/Property%20Restriction.png" alt="Overview of the project" width="70%">

- *Overview of the Universal Restriction in the Food Ontology.*
<img src="Technical_Details/Details_Pics/Universal_Restriction.png" alt="Overview of the project" width="70%">

- *Overview of the Cardinality Restriction in the Food Ontology.*
<img src="Technical_Details/Details_Pics/Cardinality_Restriction.png" alt="Overview of the project" width="70%">

### Applying Closure Axiom
- Example: Hummus can only be made with Chickpea, Olive oil, Pepper, and Salt.
<img src="Technical_Details/Details_Pics/Closure_Axiom.png" alt="Overview of the project" width="70%">

### Changing a Primitive Class to a Defined Class
- By adding sufficient conditions to necessary conditions, a primitive class can be transformed into a defined class.
<img src="Technical_Details/Details_Pics/data_property2.png" alt="Overview of the project" width="70%">
<img src="Technical_Details/Details_Pics/hasValueRestriction.png" alt="Overview of the project" width="70%">

### Using the Reasoner
- The reasoner checks the consistency of statements and definitions in the ontology and helps maintain the hierarchy.
  

<div style="display: flex; justify-content: space-around; align-items: flex-start;">
    <img src="Technical_Details/Details_Pics/Reasoner_pic1.png" alt="Image 1" width="38%">
    <img src="Technical_Details/Details_Pics/Reasoner_pic2.png" alt="Image 2" width="25%">
    <img src="Technical_Details/Details_Pics/Reasoner_pic3.png" alt="Image 3" width="25%">
</div>



### Visual Representations
- Include relevant images or diagrams to illustrate the relationships and class structures.

**Illustrating the subclasses of diseases, minerals that are recommended to use for the specified diseases and then the food that contain those specific minerals.**

<img src="Images/Graph_Pics/graph_pic2.png" alt="Overview of the project" width="70%">


**Representing the Meal and showing Breakfast is a subclass of Meal and BreakfastDish. Moreover, showing the ingredients and nutrients which exist in some type of breakfasts.**

<img src="Images/Graph_Pics/graph_pic3.png" alt="Overview of the project" width="70%">



**Representing the Level_Of_Spicy based on two different ingredients which have some nutrients in common. Moreover, representing the dishes in these two different categories (mild and hot).**

<img src="Images/Graph_Pics/graph_pic4.png" alt="Overview of the project" width="70%">



**Representing that Phosphorous is a mineral, and the ingredients contain Phosphorous. For example, Honey has Phosphorous which is used in some Dishes and showing that Susan has allergy to Honey.**

<img src="Images/Graph_Pics/graph_pic5.png" alt="Overview of the project" width="70%">





## Applications
The ontology can be applied in various domains, including restaurants, the food industry, and domestic settings.

## Examples
Expected queries to be answered, such as:
- Query 1
**Recommend the user dishes with the calorie value between 300 and 420, also contain kale or spinach or tomato but no peanut.**
<img src="Images/Queries_Pics/Query3.png" alt="Overview of the project" width="70%">

- Query 2
**Recommend Sara a mild-spicy dinner without the ingredients which she has allergy to them**
<img src="Images/Queries_Pics/Query5.png" alt="Overview of the project" width="70%">

- Query 3
**Recommend a high protein dinner to Susan and Frank which can help them with their both diseases**
<img src="Images/Queries_Pics/Query7.png" alt="Overview of the project" width="70%">

## Authors and Contributions
This project builds on works by several authors, including Dooley et al., and utilizes methodologies from Horridge et al. and Neuhaus & Brodaric.

## Conclusion
The Food Recommendation Ontology is a versatile tool for suggesting dishes that meet users' nutritional needs and preferences, promoting healthier eating habits.
 
## Contributing
[Guidelines for contributing to the project]

## License
This project is licensed under [specify license].

## Contact
For questions or feedback, please contact [your contact information].














