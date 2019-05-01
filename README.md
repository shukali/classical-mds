# (Classical) Metric Multidimensional Scaling
This repository contains a C# implementation of the **Classical Multidimensional Scaling (CMDS)** algorithm. CMDS is a Metric MDS, distance preserving dimensionality reduction algorithm. It allows mapping a high-dimensional dataset into a lower-dimensional dataset, preserving most of the datapoint's pairwise distances. A use case is, for example, to recover the location of objects in a 2D plane, knowing only the object's pairwise distances.

A real-example: Given only the pairwise distances between five German cities, CMDS has been used to recover their location in a 2D map.

<p align="center">
<img src="https://user-images.githubusercontent.com/15327691/57011859-f6a1a080-6c03-11e9-84d1-b8c3a29e7b6f.PNG" data-canonical-src="https://user-images.githubusercontent.com/15327691/57011859-f6a1a080-6c03-11e9-84d1-b8c3a29e7b6f.PNG" height="350" />
</p>

As I once needed a C# Metric MDS implementation and couldn't find any proper code for .NET, I decided to implement it myself. This is the result! The code has been tested against the MATLAB [cmdscale](https://www.mathworks.com/help/stats/cmdscale.html) implementation.

## How to start it?

The code is given as a .NET Class Library, so there is no executable component involved. After building the package once, the `.dll` file can be used as a reference in any other projects. Alternatively, you can copy the ClassicalMDS.cs file by hand and paste it into your project.

The algorithm can be used the following:

```csharp
// load any multidimensional dataset with the datapoints as rowvectors
var X_highdim = LoadHighdimDatasetAsMatrix();

ClassicalMDS cmds = new ClassicalMDS(2);
var X_lowdim = cmds.FitTransform(X_highdim, "euclidean");
```

Supported distance metrics are 'euclidean' and 'precomputed', which requires a distance matrix as input. The numerical parameter in the constructor determines the size of the low-dimenional embedding, so in this case, the low-dimenional embedding will be 2D.

## Prerequisites

The CMDS implementation requires only the **[Math.NET Numerics](https://numerics.mathdotnet.com/)** package. This package can be easily installed with the NuGet package manager, or can be obtained from their website.

## Authors
* **Marcus Rottschäfer** - [GitHub profile](https://github.com/shukali)

## License
This project is licensed under the GNU General Public License v3.0 License. See the [LICENSE.md](LICENSE) file for details.

