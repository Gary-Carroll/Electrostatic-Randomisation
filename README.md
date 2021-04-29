# Electrostatic-Randomisation
A Monte Carlo method is employed to minimise the potential energy of charges inside circular and elliptical conductor cross sections, as well as an elliptical cross section with an added external charge.
N charges are randomly placed in the ellipse. A charge is randomly selected and moved a maximum distance of dmax from its initial position, ensuring that its new position is also inside the ellipse.
The potential energy of the charge is calculated and if the potential energy of the charge in this new position is less than the potential energy it had in its initial position, the trial move is accepted. Otherwise, the trial move is rejected and the charge is returned to its initial position.
This procedure of taking a random charge and moving it no more than a certain maximum distance is repeated until most of the trial moves are rejected, for the case of only 20 charges, as is used in the code, the procedure can be repeated until all moves are rejected. 
For the first part a circular cross section is used and N=20. The maximum distance a charge can be moved, dmax, is 0.1. A circle is first plotted using the equation x^2+y^2= 1. For each of the 20 charges, a random number between 0 and 1 is generated, which corresponds to the distance of the charge from the centre point of the circle. When generating this number, the square root of the value generated by the random.uniform() function is used to prevent the charges from being focused nearer to the centre of the circle. This square root ensures that the number of random points grows linearly with r, since the circumference grows linearly with r. If the circumference of one particular value of r is twice as long as another value it must have twice as many points to maintain the same charge density. This method of  ensuring  a  uniform  charge  density  is  known  as  inverse  transform  sampling. 
The polar angle of each charge is obtained by generating a random number between 0 and 2π.  The x and y values of the point are then calculated from the radius and polar angle and the positions of the 20 charges within the circle are plotted. A list is created containing 20 elements, where each element is itself a list of 3 elements; the x and y coordinates of a charge and the potential energy of that charge. A loop is created that chooses a random element in this list and moves the charge a distance less than dmax from its initial position. (The random element is chosen by randomising the order of the list eachtime and choosing the first element in this shuffled list, effectively the same as choosing an element randomly each time). Since dmax is 0.1, this is achieved by choosing a random number for dx and dy of between -sqrt(2)/20 and sqrt(2)/20, utilising the Pythagorean theorem, and adding dx and dy to the x and y coordinate respectively.
The new potential energy of this charge is calculated and if it is less than that of the initial position, the trial move is accepted, otherwise it is rejected. This loop is run 1000 times. 
The above ’for loop’ is itself inside a ’while loop’ that runs as long as a certain condition is true. This condition is that the list of points before 1000 trial moves is different to the list of points after the moves. The ’for loop’ is repeated as long as this condition is true, with the maximum distance that each charge can be moved being lowered by a factor of 10 if less than 50 moves were accepted in the previous 1000 trial moves. The number of trial moves accepted in each loop is printed. The new listo f charges contains the final position of each charge and its final potential energy.
These new final positions are plotted and a histogram showing the final distribution of the charges is created. This should show one peak, as the distribution should be uniform around the circle. A simple test case to demonstrate that the correct results are produced is to use N=2 charges.  In this case the expected result is that the final separation of the charges will be very close to π.
The procedure for the circular cross section is repeated for different ellipses by varying the length of the semi-minor axis. The concentration of the charges in their final position is highest at the two ends of the ellipse with the highest curvature; at the ends of the major axis. The histogram will have a peak at the very left of the plot, with a smaller number of charge to the right of this peak, as the charges will be concentrated in the areas of highest curvature.
The procedure is repeated for the elliptical cross section with the addition of a fixed charge of magnitude N/2 outside of the ellipse. 
