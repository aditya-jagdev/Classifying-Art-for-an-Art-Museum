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
<br>
* Detailed approach notes can be found [here](https://github.com/aditya-jagdev/Classifying-Art-for-an-Art-Museum/blob/main/Approach%20Notes.md). <br>
* If you would like to view the analysis and results as a PowerPoint presentation, use this download [link](https://github.com/aditya-jagdev/Classifying-Art-for-an-Art-Museum/raw/main/Aditya%20Jagdev%20Tag%20the%20Art.pptx). <br>

## Approach used and results achieved
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

## Model Inference
Shapley explanations were plotted to find out why a certain category was picked over the others to understand what the model was focussing on.
![](https://raw.githubusercontent.com/aditya-jagdev/Classifying-Art-for-an-Art-Museum/main/SHAP%20Images/white%20bg.png)

The following confusion matrix heatmap shows how a significant portion of Drawings were misclassified as engravings.
![](https://raw.githubusercontent.com/aditya-jagdev/Classifying-Art-for-an-Art-Museum/main/Confusion%20Matrix/cm.png)

This may have been due to failure to capture the high level details of the images. To see what kind of low level features were being captured, the first layer filters were plotted in RGB.
![](https://raw.githubusercontent.com/aditya-jagdev/Classifying-Art-for-an-Art-Museum/main/VGG%20Filters/layer%201.png)

