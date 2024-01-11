Class-themed project for university studies...


Task description: 
Design and implement a 'Polygon' class for calculating the perimeter and area of any polygon represented in two-dimensional space. The 'Polygon' class should store the number of polygon nodes, 
dynamically allocate arrays containing the coordinates of the nodes, and their indices. It should also have an appropriate constructor, destructor, and methods for calculating the perimeter and area of the polygon.
The description of the polygon's geometry should be read from a file stream saved in the following format:
[NUMBER OF NODES]
n
[NODES]
k1 x1 y1
k2 x2 y2
... ... ...
... ... ...
kn xn yn
[POLYGON]
k1 k2 ...... kn
where: n - the number of polygon nodes, ki - the node number, xi, yi - the coordinates of the node in the Cartesian system; the order of nodes in the [NODES] section is arbitrary, while in the [POLYGON] section,
it should follow the assumed direction of the nodes in the polygon. Section names may be written in lowercase. The program should display information about the coordinates of the nodes, their order in the polygon, 
as well as the calculated perimeter and area. Utilize exception handling mechanisms to diagnose invalid input data with a description of the polygon's geometry (use try, throw, catch commands to handle exceptions).
You can check the correctness of opening a file,the correctness of section labels in the file, etc. (e.g., display an exception message when there is an error in the label, e.g., [NADES] instead of [NODES]). 
During surface area calculations, use the equation:"



