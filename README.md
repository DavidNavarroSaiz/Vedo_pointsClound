<h1 align="center">Gas Tank Point Cloud with Vedo Python</h1>

<p>Here, various procedures are presented that can be done with a point cloud in ply format. The provided point cloud corresponds to a gas tank, for which we aim to find its diameter and height.</p>

## Open Point Cloud

First, we will visualize the point cloud as captured by the Time-of-Flight (ToF) Helios2 camera (see Figure 1). This point cloud returns coordinates in millimeter units.

<div align="center">
    <img src="public\images\nubePuntosSinModificaciones.png" width="600"><img>
    <p align="center"><b>Figure 1.</b> Initial point cloud without modifications.</p>
</div>

## Transformation of Point Cloud to Depth Image

It's common to have a depth image and transform it into a 3D point cloud. In this case, we want to go the other way around: from a 3D point cloud to a depth image. The result is shown in Figure 2.

<div align="center">
    <img src="public\images\pointCloud2image.png" width="500"><img>
    <p align="center"><b>Figure 2.</b> Depth image derived from the 3D point cloud.</p>
</div>

## Gas Tank Segmentation in the Depth Image

Once we obtain the depth image, we want to segment the gas tank in the image. For this, we detect a circumference and create a mask that eliminates everything outside the circle (see Figure 3).

<div align="center">
    <img src="public\images\segmentacionTanque2D.png" width="500"><img>
    <p align="center"><b>Figure 3.</b> Gas tank segmentation in the depth image.</p>
</div>

## Drawing Radius on the 2D Image

Once the circle is detected, we draw its radius and length on the depth image, and assign a false color (magma) for visualization purposes (see Figure 4).

<div align="center">
    <img src="public\images\radionTanqueEnImagen2D.png" width="500"><img>
    <p align="center"><b>Figure 4.</b> Radius of the gas tank on the depth image.</p>
</div>

## Gas Tank Segmentation in the 3D Point Cloud

Using the mask found in the gas tank segmentation in the depth image, we will segment the gas tank in the 3D point cloud shown in <b>Figure 1</b>. The result of point cloud segmentation is shown in Figure 5.

<div align="center">
    <img src="public\images\segmentacionTanque3D.png"><img>
    <p align="center"><b>Figure 5.</b> Segmentation of the tank in the 3D point cloud. On the left, points not corresponding to the tank. On the right, tank points.</p>
</div>

## Calculating the Minimum and Maximum Points of the Point Cloud

Now that we have the segmented gas tank, we want to find and draw the minimum and maximum values of the point cloud. Additionally, we draw the distance between these two points and the previously calculated radius on the point cloud. This is shown in Figure 6.

<div align="center">
    <img src="public\images\nubePuntosMinMax.png" width="400"><img>
    <p align="center"><b>Figure 6.</b> Gas tank point cloud with the distance between the minimum and maximum points of the cloud.</p>
</div>

## Projection of the Point Cloud on the X-axis

To calculate the width and height of the gas tank, we project the point cloud onto the x-axis, obtaining a profile of the cloud (see Figure 7).

<div align="center">
    <img src="public\images\proyeccionNubePuntos.png" width="400"><img>
    <p align="center"><b>Figure 7. </b>Height and width of the projection of the gas tank point cloud on the X-axis.</p>
</div>

## Visualization of Point Clouds of Multiple Tanks

For visualization purposes, copies of the segmented gas tank point cloud are created. Each copy is then offset and merged to display a point cloud with multiple tanks (see Figure 8).

<div align="center">
    <img src="public\images\nubePuntosVariosTanques.png" width="450"><img>
    <p align="center"><b>Figure 8.</b> Point cloud showing 6 gas tanks.</p>
</div>

## Installation of Dependencies

```
pip install -r requirements.txt
```