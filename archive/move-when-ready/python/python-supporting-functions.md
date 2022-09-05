# Python Supporting Functions

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

| Function       | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Anglediff      | Accepts two Shapely line segments and returns the difference in degrees between their angles relative to a single line.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Areainterior   | Given a rectangular detached ADU’s outer width and length in feet, the minimum required interior area in square feet, and the thickness of a wall, this function returns “True” if the proposed ADU would contain adequate interior square footage and “False” otherwise.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Areatest       | Given the square footage available for building on the parcel, the minimum interior area required for an ADU in square feet, and wall thickness of an ADU in square feet, this function returns “True” if there is enough area available on the parcel to contain a detached ADU and “False” otherwise. Does not check for shape issues, so this is a basic check to rule out doing a shape fit check in the case that there is not enough space on the parcel for a detached ADU in any arrangement.                                                                                                                                                                                                                                                                                            |
| Azimuth        | Returns the Azimuth between two shapely points. Accepts point1 and point2 (Shapely points), returns azimuth between them in degrees.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Dir\_hausdorff | Accepts two Shapely line segments and returns the maximum distance between them.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Fitrects       | Given a list of Shapely Polygons (ideally a list of rectangles created through “makerects” and another single Shapely Polygon (ideally a Polygon representing the buildable area on a parcel), returns “True” if any of the polygons in the list are contained by the single polygon.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Fittes         | Given a Shapely polygon representing the buildable area on a parcel, the length, and width of that shape are calculated through “lengthshape”, the minimum area of an ADU in square feet, the minimum width of an ADU in feet, and the wall thickness of a detached ADU in feet, returns “True” if a minimum-size rectangular ADU is found to fit within the buildable area on the parcel.                                                                                                                                                                                                                                                                                                                                                                                                       |
| Lengthshape    | Accepts a polygon and a flag. The function returns either the higher or lower side length of the minimum rotated rectangle which contains the polygon. Returns the higher side length if the flag is set to “length”, the lower side length otherwise. Returns length in units of feet, assuming CRS is in meters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Makerect       | Given two lengths that define the size and shape of a rectangle, a Shapely line segment which is on the boundary of the Polygon available for building within the parcel after excluded areas have been removed, the slope and intercept of the line segment in its native coordinate system, and a user-defined number of rectangles to generate (“nrects”), this function returns a list of nrects Shapely Polygon rectangles with side lengths length1 and length2 which share a side of length1 with the line segment. The rectangles are evenly spaced along the line segment such that the first rectangle is placed to share a corner with the first endpoint of the line segment and the last rectangle is placed to share the far corner with the second endpoint of the line segment.  |
| Makepoint      | This function creates a point that matches specific geometric criteria given two Shapely points on a reference line, the slope and intercept of the line the new point should be on, the ideal distance between the new point and the first reference point, and a flag that indicates whether the new point should be on the reference line or perpendicular to it. Used to find the points which define the rectangle in “makerect.”                                                                                                                                                                                                                                                                                                                                                           |
| Segments       | Accepts a curve (LineString), returns the individual line segments which make up the curve.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Touches        | Accepts two Shapely line segments, returns “True” if they share an endpoint and “False” otherwise. Does not detect whether they cross in the middle. The idea is that we start with a collection of line segments that make up a Polygon boundary and can use this function to determine which of them are adjacent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |