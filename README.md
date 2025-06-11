# cs6476-project-1-convolution-and-hybrid-images-solved
**TO GET THIS SOLUTION VISIT:** [CS6476 Project 1-Convolution and Hybrid Images Solved](https://mantutor.com/product/cs6476-project-1-convolution-and-hybrid-images-solved-2/)


---

**For Custom/Order Solutions:** **Email:** mantutorcodes@gmail.com  

*We deliver quick, professional, and affordable assignment help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;111378&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS6476  Project 1-Convolution and Hybrid Images Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

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
CS 6476

Brief

• Project materials including report template: proj1.zip

• Hand-in: through Gradescope

• Required files: &lt;your_gt_username&gt;.zip, &lt;your_gt_username&gt;_proj1.pdf

Figure 1: Look at the image from very close, then from far away.

Overview

The goal of this assignment is to write an image filtering function and use it to create hybrid images using a simplified version of the SIGGRAPH 2006 paper by Oliva, Torralba, and Schyns. Hybrid images are static images that change in interpretation as a function of the viewing distance. The basic idea is that high frequency tends to dominate perception when it is available but, at a distance, only the low frequency (smooth) part of the signal can be seen. By blending the high frequency portion of one image with the low-frequency portion of another, you get a hybrid image that leads to different interpretations at different distances.

Setup

1. Install Miniconda. It doesn’t matter whether you use Python 2 or 3 because we will create our own environment that uses python3 anyways.

2. Download and extract the project starter code.

3. Create a conda environment using the appropriate command. On Windows, open the installed “Conda prompt” to run the command. On MacOS and Linux, you can just use a terminal window to run the command, Modify the command based on your OS (linux, mac, or win): conda env create -f

proj1_env_&lt;OS&gt;.yml

4. This will create an environment named “cs6476 proj1”. Activate it using the Windows command, activate cs6476_proj1 or the MacOS / Linux command, conda activate cs6476_proj1 or source activate cs6476_proj1

6. Run the notebook using jupyter notebook ./proj1_code/proj1.ipynb

7. After implementing all functions, ensure that all sanity checks are passing by running pytest proj1_unit_tests inside the repo folder.

8. Generate the zip folder for the code portion of your submission once you’ve finished the project using python zip_submission.py –gt_username &lt;your_gt_username&gt;

1 Part 1: NumPy

1.1 Gaussian kernels

Gaussian filters are used for blurring images. You will first implement create_Gaussian_kernel_1D(), a function that creates a 1D Gaussian vector according to two parameters: the kernel size (length of the 1D vector) and σ, the standard deviation of the Gaussian. The vector should have values populated from evaluating the 1D Gaussian pdf at each coordinate. The 1D Gaussian is defined as:

Next, you will implement create_Gaussian_kernel_2D(), which creates a 2-dimensional Gaussian kernel according to a free parameter, cutoff frequency, which controls how much low frequency to leave in the image. Choosing an appropriate cutoff frequency value is an important step for later in the project when you create hybrid images. We recommend that you implement create_Gaussian_kernel_2D() by creating a 2D Gaussian kernel as the outer product of two 1D Gaussians, which you have now already implemented in create_Gaussian_kernel_1D(). This is possible because the 2D Gaussian filter is separable (think about how e(x+y) = ex · ey). The multivariate Gaussian function is defined as:

where n is equal to the dimension of x, µ is the mean coordinate (where the Gaussian has peak value), and Σ is the covariance matrix.

You will use the value of cutoff frequency to define the size, mean, and variance of the Gaussian kernel. Specifically, the kernel G should be size (k,k) where k = 4·cutoff frequency+1, have peak value at , standard deviation σ = cutoff frequency, and values that sum to 1, i.e., Pij Gij = 1. If your kernel doesn’t sum to 1, you can normalize it as a postprocess by dividing each value by the sum of the kernel.

1.2 Image Filtering

1.3 Hybrid Images

A hybrid image is the sum of a low-pass filtered version of one image and a high-pass filtered version of another image. As mentioned above, cutoff frequency controls how much high frequency to leave in one image and how much low frequency to leave in the other image. In cutoff_frequencies.txt, we provide a default value of 7 for each pair of images (the value of line i corresponds to the cutoff frequency value for the i-th image pair). You should replace these values with the ones you find work best for each image pair. In the paper it is suggested to use two cutoff frequencies (one tuned for each image), and you are free to try that as well. In the starter code, the cutoff frequency is controlled by changing the standard deviation of the Gaussian filter used in constructing the hybrid images. You will first implement create_hybrid_image () according to the starter code in part1.py. Your function will call my_conv2d_numpy() using the kernel generated from create_Gaussian_kernel() to create low and high frequency images, and then combine them into a hybrid image.

2 Part 2: PyTorch

2.1 Dataloader

You will now implement creating hybrid images again but using PyTorch. The HybridImageDataset class in part2_datasets.py will create tuples using pairs of images with a corresponding cutoff frequency (which you should have found from experimenting in Part 1). The image paths will be loaded from data/ using make_dataset() and the cutoff frequencies from cutoff_frequencies.txt using get_cutoff_frequencies(). Additionally, you will implement __len__(), which returns the number of image pairs, and __getitem__(), which returns the i-th tuple. Refer to this tutorial for additional information on data loading &amp; processing.

2.2 Model

Next, you will implement the HybridImageModel class in part2_models.py. Instead of using your implementation of my_conv2d_numpy() to get the low and high frequencies from a pair of images, low_pass() should use the 2D convolution operator from torch.nn.functional to apply a low pass filter to a given image. You will have to implement get_kernel() which calls your create_Gaussian_kernel() function from part1.py for each pair of images using the cutoff frequencies as specified in cutoff_frequencies.txt, and reshape it to the appropriate dimensions for PyTorch. Then, similar to create_hybrid_image() from part1.py, forward() will call get_kernel() and low_pass() to create the low and high frequency images, and combine them into a hybrid image. Refer to this tutorial for additional information on defining neural networks using PyTorch.

You will compare the runtimes of your hybrid image implementations from Parts 1 &amp; 2.

3 Part 3: Understanding input/output shapes in PyTorch

You will now implement my_conv2d_pytorch() in part3.py using the same 2D convolution operator from torch.nn.functional used in low_pass().

Before we proceed, here are two quick definitions of terms we’ll use often when describing convolution:

• Stride: When the stride is 1 then we move the filters one pixel at a time. When the stride is 2 (or uncommonly 3 or more, though this is rare in practice) then the filters jump 2 pixels at a time as we slide them around.

• Padding: The amount of pixels added to an image when it is being convolved with a the kernel. Padding can help prevent an image from shrinking during the convolution operation.

Unlike my_conv2d_numpy() from part1.py, the shape of your output does not necessarily have to be the same as the input image. Instead, given an input image of shape (1,d1,h1,w1) and kernel of shape ( ), your output will be of shape (1,d2,h2,w2) where g is the number of groups, + 1, and + 1, and p and s are padding and stride, respectively.

Think about why the equations for output width w2 and output height h2 are true – try sketching out a 5 × 5 grid, and seeing how many places you can place a 3 × 3 square within the grid with stride 1. What about with stride 2? Does your finding match what the equation states?

We demonstrate the effect of the value of the groups parameter on a simple example with an input image of shape (1,2,3,3) and a kernel of shape (4,1,3,3):

Figure 2: Visualization of a simple example using groups=2.

4 Writeup

For this project (and all other projects), you must do a project report using the template slides provided to you. Do not change the order of the slides or remove any slides, as this will affect the grading process on Gradescope and you will be deducted points. In the report you will describe your algorithm and any decisions you made to write your algorithm a particular way. Then you will show and discuss the results of your algorithm. The template slides provide guidance for what you should include in your report. A good writeup doesn’t just show results–it tries to draw some conclusions from the experiments. You must convert the slide deck into a PDF for your submission.

If you choose to do anything extra, add slides after the slides given in the template deck to describe your implementation, results, and analysis. Adding slides in between the report template will cause issues with Gradescope, and you will be deducted points. You will not receive full credit for your extra credit implementations if they are not described adequately in your writeup.

Data

We provide you with 5 pairs of aligned images which can be merged reasonably well into hybrid images. The alignment is super important because it affects the perceptual grouping (read the paper for details). We encourage you to create additional examples (e.g., change of expression, morph between different objects, change over time, etc.).

For the example shown in Figure 1, the two original images look like this:

(a) Dog (b) Cat

Figure 3

The low-pass (blurred) and high-pass version of these images look like this:

(a) Low frequencies of dog image. (b) High frequencies of cat image.

Figure 4

The high frequency image in Figure 4b is actually zero-mean with negative values, so it is visualized by adding 0.5. In the resulting visualization, bright values are positive and dark values are negative.

Adding the high and low frequencies together (Figures 4b and 4a, respectively) gives you the image in Figure 1. If you’re having trouble seeing the multiple interpretations of the image, a useful way to visualize the effect is by progressively downsampling the hybrid image, as done in Figure 5. The starter code provides a function, vis_image_scales_numpy() in utils.py, which can be used to save and display such visualizations.

Figure 5

Potentially useful NumPy (Python library) functions

np.pad(), which does many kinds of image padding for you, np.clip(), which “clips” out any values in an array outside of a specified range, np.sum() and np.multiply(), which makes it efficient to do the convolution (dot product) between the filter and windows of the image. Documentation for NumPy can be found here or by Googling the function in question.

Forbidden functions

Editing code

Testing

We have provided a set of tests for you to evaluate your implementation. We have included tests inside proj1.ipynb so you can check your progress as you implement each section. When you’re done with the entire project, you can call additional tests by running pytest proj1_unit_tests inside the root directory of the project, as well as checking against the tests on Gradescope. Your grade on the coding portion of the project will be further evaluated with a set of tests not provided to you.

Bells &amp; whistles (extra points)

Rubric

• +5 pts: create_Gaussian_kernel_1D() in part1.py

• +5 pts: create_Gaussian_kernel_2D() in part1.py

• +15 pts: my_conv2d_numpy() in part1.py

• +10 pts: create_hybrid_image() in part1.py

• +5 pts: make_dataset() in part2_datasets.py

• +5 pts: get_cutoff_frequencies() in part2_datasets.py

• +5 pts: __len__() in part2_datasets.py

• +5 pts: __getitem__() in part2_datasets.py

• +5 pts: get_kernel() in part2_models.py

• +5 pts: low_pass() in part2_models.py

• +10 pts: forward() in part2_models.py

• +5 pts: my_conv2d_pytorch() in part3.py

• +20 pts: Report

• -5*n pts: Lose 5 points for every time you do not follow the instructions for the hand-in format

Submission format

This is very important as you will lose 5 points for every time you do not follow the instructions. You will submit two items to Gradescope:

1. &lt;your_gt_username&gt;.zip containing:

(a) proj1_code/ – directory containing all your code for this assignment

(b) cutoff_frequencies.txt – .txt file containing the best cutoff frequency values you found for each pair of images in data/

(c) additional_data/ – (optional) if you use any data other than the images we provide, please include them here

(d) README.txt – (optional) if you implement any new functions other than the ones we define in the skeleton code (e.g., any extra credit implementations), please describe what you did and how we can run the code. We will not award any extra credit if we can’t run your code and verify the results.

2. &lt;your_gt_usernamme&gt;_proj1.pdf – your report

Credits

Assignment developed by Cusuh Ham, John Lambert, Vijay Upadhya, Samarth Brahmbhatt, Frank Dellaert, and James Hays based on a similar project by Derek Hoiem.
