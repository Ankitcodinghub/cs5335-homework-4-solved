# cs5335-homework-4-solved
**TO GET THIS SOLUTION VISIT:** [CS5335 Homework 4 Solved](https://www.ankitcodinghub.com/product/cs5335-please-remember-the-following-policies-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;109466&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS5335 Homework 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
All of the code for this assignment is in Python, and located within ‘hw6.zip’. A guide for how to install necessary libraries is found in ‘README.md’. Please add comments to your code to help the graders understand what you are doing. If you make a mistake, you are much more likely to receive partial credit if the code is understandable.

Q1. Grasp Simulator

Run the command $python simulator.py to view the grasp simulator via the Pybullet graphical user interface. You should see a window pop up that looks like Fig. 1. The simulator contains a Panda Arm and a square workspace where small objects are randomly placed. After every reset, the robot arm attempts a grasp with the gripper aligned along x- or y-axis. An RGB camera (not visible) is positioned to view the workspace from above, and the camera feed is shown in the top left panel. You can zoom in and out with the mouse scroll; hold down the control key and right mouse button to rotate your view of the scene.

Figure 1: Grasp simulator in Pybullet.

(a) Describe the benefits of using a simulator to generate datasets of grasp attempts. Consider the two factorsof speed and safety.

(b) Do you notice any unrealistic physics that occurs on some grasps? Hint: rotate your view to be parallelwith the ground plane.

The simulator from above was used to collect a dataset of 1,000 successful grasps, split into a train and validation set. For each grasp, a 64 × 64 pixel RGB image is captured of the scene and we record the pixel location (px, py) and rotation (0 or 90 degrees) of the gripper. In the following sections, you will build and train a network to predict successful grasps given a top-down RGB image of the scene. We have designed this assignment so that the network can be trained and evaluated entirely on CPU.

Figure 2: Unet with MobileNetV3 backbone. Architecture inspired by Fig. 10 of “Searching for MobileNetV3” (https://arxiv.org/pdf/1905.02244.pdf). Intermediate tensor shapes are labeled without batch dimension.

Q2. Create Grasp Prediction Network (3 points).

You will now create a convolutional network to predict successful grasps given a top-down RGB image of the scene. The network will output an image with the same size as the input image, where each pixel has two channels corresponding to the two different gripper rotations (0 degrees and 90 degrees about the z-axis). In other words, the network outputs a distribution over pixel location and gripper rotation for a successful grasp. At inference time, the argmax over pixels and channels can be used to determine the best gripper location and rotation. The network is trained to minimize a cross entropy loss over the output distribution.

(b) The network is designed with two pathways emerging from the MobileNet backbone. The pathways areintended to carry information with different spatial resolutions. What local information is important for predicting grasp success? Is there any global information that is needed? If not, can you think of a task where global information would be needed?

Q3. Training and Evaluating Network (2 points).

(a) Run the training script with the command $python trainer.py. It should take around 5 minutes to train for 30 epochs on your CPU (if you have a GPU, it will automatically use it). While it is training, you can monitor the loss curves by viewing the image file ‘loss curves.png’ and see predictions by viewing ‘predictions.png’. It is expected that the validation loss curve will be very noisy (+1 Extra Credit point if you can explain why!) so only the best performing weights are saved. The data in Figures 3,4 are approximately what you should see (achieving a validation loss of around 3), but the code is not perfectly repeatable.

Figure 3: Example loss curves. Figure 4: Example predictions.

(b) Explain why the validation loss is not a perfect indicator of how well the network can predict grasps. Hint: could the network predict a valid grasp location that results in a large loss term (e.g. false negative)?

(c) To get a better sense of the model performance, we can evaluate it directly in the simulator wherethe data was generated. Run the command $python evaluate model.py to see the model perform 50 grasp attempts. What success rate is achieved (report the final estimate which is averaged over all 50 attempts)? Do you notice anything different about the object placements here (compared to what you see in ‘predictions.png’)?

Q4. Adding Data Augmentation (3 points).

(a) Implement the method GraspDataset.transform grasp in ‘dataset.py’. For more details, see the method docstring.

(b) Re-train your network with the rotation data augmentations. Run the evaluation script again (it willautomatically use the new network weights). Report the success rate.

(c) Say we also wanted to improve generalization to translations of the objects in the scene. Describe in writingwhat transformations you would apply to the image, gripper rotation, and pixel location to augment the data in this way.
