The algorithms for performing operations with integers using their binary expansions are extremely important in computer arithmetic. We will describe algorithms for the addition and the multiplication of two integers expressed in binary notation. We will also analyze the computational complexity of these algorithms, in terms of the actual number of bit operations used. Throughout this discussion, suppose that the binary expansions of a and b are

$$a=(a_{n-1}\ a_{n-2}\ \cdots\ a_1a_0)_2,\quad b=(b_{n-1}\ b_{n-2}\ \cdots\ b_1b_0)_2,$$

So that a and b each have n bits (putting bits equal to 0 at the beginning of one of these expansions if necessary).