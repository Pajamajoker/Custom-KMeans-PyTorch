# Image Clustering Project

This repository demonstrates the use of clustering algorithms to process and analyze image data. The project involved several stages of image manipulation, noise cleaning, clustering, and visualization. Below is a summary of the steps and challenges encountered throughout the project.

## Table of Contents

1. [Task 1: Data Preparation and Image Transformation](#task-1-data-preparation-and-image-transformation)
2. [Task 2: Image Visualization and Noise Cleaning](#task-2-image-visualization-and-noise-cleaning)
3. [Task 3: Clustering with KMeans](#task-3-clustering-with-kmeans)
4. [Task 4: Custom Clustering Algorithm with PyTorch](#task-4-custom-clustering-algorithm-with-pytorch)
5. [Comparison](#comparison)
6. [Applications](#applications)
7. [Conclusion](#conclusion)

---

## Task 1: Data Preparation and Image Transformation

In the first step, I prepared the image data for clustering by converting the image to a NumPy array using the Python Imaging Library (PIL). The image was converted to RGB to remove the alpha channel (transparency) and simplify the data structure.

- Extracted pixel (x, y) coordinates and RGB values.
- Used `np.arange()` to create coordinate arrays and reshaped the RGB values.
- Combined data into a DataFrame for easy access and manipulation.

### Challenge Faced
Aligning the pixel coordinates with their corresponding RGB values posed a challenge. The reshaping process required attention to ensure compatibility with clustering algorithms. The solution involved careful validation of array shapes and the proper reshaping of the data.

---

## Task 2: Image Visualization and Noise Cleaning

Next, I visualized the image to identify noise or artifacts that may interfere with clustering. This step helped isolate areas with inconsistent colors or isolated pixels that did not belong to the rainbow pattern.

- Used Matplotlib for visualization.
- Removed unwanted pixels by filtering out extreme RGB values.

### Challenge Faced
Identifying what constitutes "noise" in the image was a complex task. Some pixels that initially appeared as noise were part of the rainbow's gradient. Through trial and error, I fine-tuned the threshold values for filtering unwanted pixels while preserving the essential image details.

---

## Task 3: Clustering with KMeans

In this task, I used KMeans clustering to group the image pixels based on similar color values.

- Applied StandardScaler to normalize the RGB values before clustering.
- Used KMeans from scikit-learn to segment the image into 8 clusters based on color similarity.

### Challenge Faced
Determining the optimal number of clusters for KMeans was a challenging aspect, as the number of clusters greatly impacts the results. Initially, the clustering did not yield expected results. After adjusting parameters and scaling techniques, I achieved meaningful color clusters, which were visualized as bands of color in the segmented image.

---

## Task 4: Custom Clustering Algorithm with PyTorch

In this task, I implemented a custom clustering algorithm using PyTorch to better understand the mechanics of clustering algorithms.

- Manually initialized centroids and iterated to update centroids based on pixel distances.
- Used `torch.cdist()` for distance calculation and updated centroids by averaging the points in each cluster.

### Challenge Faced
Proper initialization of centroids was crucial for effective clustering. Random initialization can lead to poor clustering, so I adjusted the centroid selection strategy to ensure diverse coverage of the data. Performance issues arose when processing large images, but after optimizing the algorithm, the custom clustering produced reasonable results that closely matched KMeans.

---

## Comparison

I compared the clustering results of the custom PyTorch algorithm with those produced by scikit-learn's KMeans. Both algorithms yielded similar color clusters, but the KMeans approach was more efficient and effective for large images.

---

## Applications

- **Image Compression**: Clustering can reduce the number of unique colors in an image, leading to smaller file sizes while maintaining visual quality. This is beneficial for web and mobile applications.
- **Image Segmentation**: It can be used to separate distinct objects in an image, such as segmenting tumors in medical imaging or identifying different terrain types in satellite imagery.
- **Color Palettes**: This technique can generate color palettes automatically from images, which is useful in design, branding, and digital art.
- **Background Removal**: By clustering similar colors, the technique can isolate the foreground from the background, which is valuable in e-commerce product images and photo editing.

---

## Conclusion

The project successfully demonstrated the use of KMeans clustering to segment an image based on color similarity. This technique can be applied in various real-world scenarios, such as image compression, object segmentation, and generating color palettes.

### Did I Overuse PyTorch?

**<span style="color:red;">Yes, PyTorch was likely overkill for this task. While it was an excellent learning opportunity to implement clustering from scratch, the KMeans algorithm in scikit-learn is more efficient and appropriate for this type of image segmentation. Nonetheless, the experience with PyTorch helped solidify my understanding of clustering mechanics and provided valuable insights into custom algorithm development.</span>**
