
# PROJECT REQUIREMENTS: 

An End-to-End Multi Task Learning Framework

- Implement an end to end pipeline from image preprocessing 
- Implement CUDA accelerated code for faster processing 
- Implement a Multi-Task Neural Network for perception with existing labelled datasets
    - Implement Network with Shared Transformer Encoders and different decoder heads for the neural network 
    - Implement Network for mulitple tasks - Depth Completion and Segmentation
    - Possible addition to the tasks would be Deep Optical flow / Detection /Fusion 
    - Finetune the Implemented neural network for faster inference 
        - Inference Requirements: 
            - greater than or equal to 25 fps
            - Sufficient accuracy in Depth/Disparity and Segmentation Error per class
- Develop the model training and inference code independent of each other as standalone repos
    - Develop the Neural Network/ML/DL in a ML/DL container 
    - Develop the Image Processing work in the source code container 
- Establish multi-container communication for handling the end-to-end pipeline 
