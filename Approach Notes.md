# Aditya Jagdev
---
### Approach Notes
* This was an image classification problem. 
* Received images were verified to be image files and saved in the RGB format.

* First Attempt
  * Image files were resized to target dimensions and saved to a new directory tree.
  * They were supposed to be loaded into numpy objects and fed to the algorithm from RAM for faster training.
  * Due to memory constraints, the numpy object was not loading into memory. Progress was stopped.

* Second Attempt
  * Image file formats were changed to minimize file size.
  * Instead of np.float64, np.float16 was used. This significantly reduced numpy object sizes which were then loaded into RAM easily.
  * When training began, similar crashes as the first attempt occurred due to running out of memory.
  * The reason was found out. Files were converted to np.float64 while processing because python maintains a 64bit data structure across its environment. Hence crashes occurred when training because files were getting converted to np.float64 again.

* Third Attempt
  * Data generator was used to feed the files and performing resize and normalize operations.
  * This allowed flexible use of data with other models.
  * A CNN [3x(conv-conv-pool)-FC-FC-Softmax ] was used.
    * The CNN was trained which got stuck at 54% accuracy and wouldn't learn any more features, even after 70 epochs.
  * A VGG16 model with pretrained weights was used as a feature extractor.
    * It attained an accuracy of 74% before plateauing.
  * VGG16 was fine-tuned by freezing the first 3 conv blocks and training the subsequent layers.
    * It attained an accuracy of 92% on the validation set and an F1 score of 0.91 on the holdout set.
    * It was further improved using cross validation and hyper-parameter tuning to attain F1 score of 0.95 on the holdout set.
  * A fine-tuned ResNet50 model was used.
    * It reached an accuracy of 85% after 40 epochs after which it plateaued.
    * The model took significantly longer to train than VGG16 and required more resources to train.

### Final Model
* The submission was made using VGG16 predictions.
