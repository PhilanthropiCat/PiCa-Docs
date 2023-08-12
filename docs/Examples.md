# Examples

## Example with Addition and Multiplication

Let's represent the function f(x,y,z) = x + yz through a computational graph. We will obtain the result of the function and also the gradient of the variables x,y,z.

First you have to install the package: 

    pip install picalib

Then, you have to import the library:

    import pica

Then we are going to initialize our variable nodes. X will have a value of 2 and will be represented by node v1, Y will have a value of 5 and will be represented by node v2 and Z will have a value of 20 and will be represented by node v3.  

    g = pica.Graph()
    v1 = pica.VariableNode(2)
    v2 = pica.VariableNode(5)
    v3 = pica.VariableNode(20)

Now we are going to define node v4, which is going to be the node that is going to mutiply Y and Z. Finally, we will define node v5, which will add X to the result of node v4.

    v4 = pica.MultNode(v2,v3)
    v5 = pica.SumNode(v1,v4)

Now we are going to initialize our nodes and make the connections between them.

    g.node(v1)
    g.node(v2)
    g.node(v3)
    g.connect(v2,v4)
    g.connect(v3,v4)
    g.connect(v1,v5)
    g.connect(v4,v5)

We will use the forward method to evaluate the result of the function.

    result = g.forward()
    print(f"Result: {result}")

In this case the result of the function will be 102.

Now we are going to use the backward method to obtain the gradients of the variables.

    g.backward()
    print(f"X Gradient: {v1.gradient}, Y Gradient: {v2.gradient}, Z Gradient: {v3.gradient}")

The result will be as follows:

    X Gradient: 1, Y Gradient: 20, Z Gradient: 5

## Example with Subtraction and Division

Let's represent the function f(x,y,z) = (x-y)/9z through a computational graph. We will obtain the result of the function and also the gradient of the variables x,y,z.

First you have to install the package: 

    pip install picalib

Then, you have to import the library:

    import pica


Then we are going to initialize our variable nodes. X will have a value of 5 and will be represented by node v1, Y will have a value of 6 and will be represented by node v2 and Z will have a value of 7 and will be represented by node v3.  

    g = pica.Graph()
    v1 = pica.VariableNode(5)
    v2 = pica.VariableNode(6)
    v3 = pica.VariableNode(7)

Now we will define the v4 node, which will be a ValueNode type node with the value of 9. The v5 node will be a SubNode that will perform the subtraction between X and Y. Node v6 will be a MultNode type node that will perform the multiplication between 5 and Z. Finally, node v7 will perform the division between node v5 and node v6.
    
    v4 = pica.ValueNode(9)
    v5 = pica.SubNode(v1,v2)
    v6 = pica.MultNode(v4,v3)
    v7 = pica.DivNode(v5,v6)

Now we are going to initialize our nodes and make the connections between them.

    g.node(v1)
    g.node(v2)
    g.node(v3)
    g.node(v4)
    g.connect(v1,v5)
    g.connect(v2,v5)
    g.connect(v3,v6)
    g.connect(v4,v6)
    g.connect(v5,v7)
    g.connect(v6,v7)

We will use the forward method to evaluate the result of the function.

    result = g.forward()
    print(f"Result: {result}")
    
The result will be as follows:

    Result: -0.015873015873015872

Now we are going to use the backward method to obtain the gradients of the variables.

    g.backward()
    print(f"X Gradient: {v1.gradient}, Y Gradient: {v2.gradient}, Z Gradient: {v3.gradient}")

The result will be as follows:

    X Gradient: 0.015873015873015872, Y Gradient: -0.015873015873015872, Z Gradient: 0.0022675736961451248