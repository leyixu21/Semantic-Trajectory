# Semantic Trajectory
This project is a master thesis that discovers visiting behaviors and city perceptions by mining semantic trajectories in London. The data used in this thesis includes Foursquare check-ins and Flickr tags from April 3, 2012 to September 16, 2013.

## Workflow
![image](https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/4328cdd1-3c1f-40e7-906d-c879ea8b044c)

## First Research Question
**Which areas are more popular among locals and tourists at different time spans?**

Four time spans were considered, including daytime, nighttime, weekday, and weekend.

### Hotspots detection
- Kernel density estimation (KDE)

- Calculation of difference ratio, which reveals the mixture degree of locals and tourists within 1x1km rasters, with the bias in significant differences in the number of locals and tourists avoided.

### Example results

- Kernel density estimation of Foursquare check-ins during the daytime.

<img src="https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/f4afb432-2a4e-485c-8578-59d850540731" height="270">

- Difference ratio of rasters during the daytime and nighttime.

<img src="https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/b8791c94-d5cd-4f2b-b54f-7144ac3bf026" height="260">


## Second Research Question
**How do locals and tourists perceive the city along their semantic trajectories at different time spans?**

Four time spans were considered, including daytime, nighttime, weekday, and weekend.

### Place modeling

- Place construction

Utilizing HDBSCAN for clustering Foursquare check-ins into meaningful places. These places are defined by the convex hulls encapsulating each cluster, while the place’s central coordinate is established through the centroid of the convex hull (in practical applications, certain place boundaries might overlap).

<img src="https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/b27e8567-58be-4724-a313-76e0c4435c6d" height="280">


- Place dimension semantic enrichment
  - Location: London borough names
  -  Locale: place category
  -  Sense of place: topics generated based on Flickr tags within place boundaries using topic modeling (LDA model)

<img src="https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/3ef89fab-ee26-4fb7-9285-3f30c04ee99d" height="250">

### Typical semantic trajectories mining
- Semantic trajectory construction

Semantic trajectories were constructed based on the places defined in Section 4.2.1. The semantic trajectories can be defined as a sequence of places T = ⟨p1, p2, ..., pn⟩, with pi = (x, y, D) being the place i at the position (x, y) annotated by the three semantic dimensions of the place D, including location, locale, and sense of place.

- Semantic trajectory similarity measure

The Multidimensional Similarity Measure (MSM) [[1]](#1) was employed in this study to construct the similarity matrix for semantic trajectories. Four dimensions were considered, including the spatial position and three semantic dimensions.

- Semantic trajectory clustering

K-medoids was applied to cluster semantic trajectories.

- Sequential pattern mining

Prefix-projected Sequential pattern mining (PrefixSpan) algorithm was applied to detect frequently visited sequences of places.

### Example results
- Distribution of locals’ trajectories during the daytime (typical trajectories are represented by the dark red color).

<img src="https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/b1ce826e-0df9-4e02-bcb3-da73f8c3c016" height="500">

- Distribution of topics.

![image](https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/2bcfc8f1-4649-4355-b522-6c1fd5a780da)

- Trajectory dimensions of locals during the daytime.

![image](https://github.com/leyixu21/Semantic-Trajectory/assets/96665869/453e2119-3665-4369-a4a5-3efef116610d)


## References
<a id="1">[1]</a> 
Furtado, A. S., Kopanaki, D., Alvares, L. O., & Bogorny, V. (2016). Multidimensional similarity measuring for semantic trajectories. Transactions in GIS, 20(2), 280-298.
