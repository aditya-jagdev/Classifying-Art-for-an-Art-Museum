# Classifying-Art-for-an-Art-Museum

### Problem Statement
The Louvre museum wants to digitize its complete collection of paintings, scultpures and other art pieces and offer a virtual tour of the museum. This would ensure that art enthusiasts from any part of the world would be able to experience the rich treasures showcased in the museum.

As part of the exercise, the museum also wants to reorganize its collection to offer a customized tour to the visitors. An aspiring painter wishes to visit the painting gallery and skip the rest of the exhibits. Similarly, a sculpture enthusiast would wish to visit only the sculpture section. But currently, the Louvre does not have the tags done properly and only a portion of their exhibits have proper tags. Getting the proper tags/categories of exhibits would enable the Louvre to give a customized journey to virtual visitors.

### Data
Labelled images belonging to 5 categories were given. From the [data source](https://rusmuseumvrm.ru/collections/index.php?lang=en), images belonging to the following 5 categories were provided:
* Drawings: 0
* Engraving: 1
* Iconography: 2
* Painting: 3
* Sculpture:4 

## Approach used and results achieved
Detailed approach notes can be found [here](https://github.com/aditya-jagdev/Classifying-Art-for-an-Art-Museum/blob/main/Approach%20Notes.md). <br>
Using a fine tuned VGG16 model, an F1 score of 0.95 was achieved on the holdout set.

The classification report is as follows:

|               |precision  |recall     |f1-score   |support    |
|---            |---        |---        |---        |---        |
|0 Drawing      |0.80       |0.70       |0.75       |141        |
|1 Engraving    |0.70       |0.94       |0.80       |96         |
|2 Iconography  |0.98       |0.99       |0.98       |264        |
|3 Painting     |0.97       |0.85       |0.91       |102        |
|4 Sculpture    |0.99       |0.97       |0.98       |219        |
|---            |---        |---        |---        |---        |
|accuracy       |           |           |0.91       |822        |
|macro avg      |0.89       |0.89       |0.88       |822        |
|weighted avg   |0.92       |0.91       |0.91       |822        |
