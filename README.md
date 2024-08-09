
# Food Recommendation Ontology / Logical-Programming

## Table of Contents
- [Overview](#overview)
- [Installation and Usage](#installation-and-usage)
- [Features](#features)
- [Technical Details](#technical-details)
- Key Classes, Applying Disjoint, Relationship between different classes, Assigning domain and range to object properties, Data properties and relation, Property Restriction, Applying Closure Axiom, Change a Primitive class to a Defined class, Using the reasoner.

- [Applications](#applications)
- [Examples](#examples)
- [Conclusion](#conclusion)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)


## Technical Details
The ontology can answer various queries, including:
- Written in OWL (Web Ontology Language)
- Developed using Protégé [5.5.0]
- Installation and Usage: (https://protege.stanford.edu)

## ## Overview and ontology metrics
This repository contains a comprehensive food ontology written in OWL (Web Ontology Language). It aims to provide a standardized vocabulary and semantic structure for describing food products, ingredients, personalized nutritional recommendations to support healthy eating through a comprehensive food ontology and related concepts.
<div style="display: flex; justify-content: space-around;">
    <img src="Technical_Details/Details_Pics/metrics_pic1.png" alt="Image 1" width="32%">
    <img src="Technical_Details/Details_Pics/metrics_pic2.png" alt="Image 2" width="33%">
    <img src="Technical_Details/Details_Pics/metrics_pic3.png" alt="Image 3" width="28%">
</div>


## Key Classes
- **Dish**: Includes subclasses like Named_Dish and various defined classes based on features such as calorie content and dietary restrictions.
- **Nutrition**: Covers carbohydrates, fats, fibers, proteins, minerals, and vitamins.
- **Ingredient**: Divided into animal-based and plant-based ingredients, with further subclasses like fruits, grains, and vegetables.
- **User**: Represents user preferences and dietary restrictions.
- **Disease**: Consider the health conditions of users before make any recomendation.
- 
<img src="Images/all.png" alt="Overview of the project" width="40%">

## Relationships
- **hasIngredient**: Connects dishes to their ingredients.
- **hasNutrient**: Links ingredients to their nutritional content.
- **servedAsMeal**: Specifies when a dish can be served (e.g., breakfast, lunch, dinner).

## Property Restrictions
- Utilizes property restrictions like existential and universal quantifiers to define complex dishes, vegan dishes, and more.

## Applications
The ontology can be applied in various domains, including restaurants, the food industry, and domestic settings.

## Examples
Expected queries to be answered, such as:
- Recommend the user dishes based on the ingredients
- Recommend the user dishes based on the nutrition.
- Recommend the user dishes based on amount of calorie.
- Recommend the user dishes based on different categories such as, high protein dishes, vegan dishes, complex dishes, and different meals.
- Recommend the user dishes based on their allergy.
- Recommend the user dishes based on their disease.

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














