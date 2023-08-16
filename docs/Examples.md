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

## Example with Trig Functions 1

Let's represent the function f(x,y,z) = Sin(x) - Cos(y)Tan(z) through a computational graph. We will obtain the result of the function and also the gradient of the variables x,y,z.

First you have to install the package: 

    pip install picalib

Then, you have to import the library:

    import pica

Then we are going to initialize our variable nodes. X will have a value of 3 and will be represented by node v1, Y will have a value of 17 and will be represented by node v2 and Z will have a value of 22 and will be represented by node v3.  

    g = pica.Graph()
    v1 = pica.VariableNode(3)
    v2 = pica.VariableNode(17)
    v3 = pica.VariableNode(22)

Then we will define node v4 as a SinNode, v5 as a CosNode, v6 as a TanNode, node v7 will be a MultNode that will multiply the value of nodes v5 and v6 and finally node v8 will be a SubNode that will subtract the value of nodes v4 and v7.

    v4 = pica.SinNode(v1)
    v5 = pica.CosNode(v2)
    v6 = pica.TanNode(v3)
    v7 = pica.MultNode(v5, v6)
    v8 = pica.SubNode(v4, v7)

Now we are going to initialize our nodes and make the connections between them.

    g.node(v1)
    g.node(v2)
    g.node(v3)
    g.connect(v1, v4)
    g.connect(v2, v5)
    g.connect(v3, v6)
    g.connect(v5, v7)
    g.connect(v6, v7)
    g.connect(v5, v8)
    g.connect(v7, v8)

We will use the forward method to evaluate the result of the function.

    result = g.forward()
    print(f"Result: {result}")
    
The result will be as follows:

    Result:-0.334036245057012

Now we are going to use the backward method to obtain the gradients of the variables.

    g.backward()
    print(f"X Gradient: {v1.gradient}, Y Gradient: {v2.gradient}, Z Gradient: {v3.gradient}")

The result will be as follows:

    X Gradient: 0.9986295347545738, Y Gradient: 0.11812583640011823, Z Gradient: -1.1124092582218779

## Example with Trig Functions 2

Let's represent the function f(x,y) = Csc(x)/xy through a computational graph. We will obtain the result of the function and also the gradient of the variables x,y.

First you have to install the package: 

    pip install picalib

Then, you have to import the library:

    import pica

Then we are going to initialize our variable nodes. X will have a value of 55 and will be represented by node v1, Y will have a value of 60 and will be represented by node v2. 

    g = pica.Graph()
    v1 = pica.VariableNode(55)
    v2 = pica.VariableNode(60)

Then we will define the v3 node which will be a CscNode that will take as parameter X, the v4 node will be a MultNode that will multiply X and Y and finally the v5 node will be a DivNode that will divide the value of v3 by the value of v4.

    v3 = pica.CscNode(v1)
    v4 = pica.MultNode(v1,v2)
    v5 = pica.DivNode(v3,v4)

Now we are going to initialize our nodes and make the connections between them.

    g.node(v1)
    g.node(v2)
    g.connect(v1,v3)
    g.connect(v1,v4)
    g.connect(v2,v4)
    g.connect(v3,v5)
    g.connect(v4,v5)

We will use the forward method to evaluate the result of the function.

    result = g.forward()
    print(f"Result: {result}")
    
The result will be as follows:

    Result:0.0003699316935640776

Now we are going to use the backward method to obtain the gradients of the variables.

    g.backward()
    print(f"X Gradient: {v1.gradient}, Y Gradient: {v2.gradient}")

The result will be as follows:

    X Gradient: -0.0002657549912483257, Y Gradient: -6.16552822606796e-06


## Example with Logarithms

Let's represent the function f(x,y) = Ln(x)Log(y)/Tan(x)Cot(y) through a computational graph. We will obtain the result of the function and also the gradient of the variables x,y.

First you have to install the package: 

    pip install picalib

Then, you have to import the library:

    import pica

Then we are going to initialize our variable nodes. X will have a value of 3 and will be represented by node v1, Y will have a value of 9 and will be represented by node v2. 

    g = pica.Graph()
    v1 = pica.VariableNode(3)
    v2= pica.VariableNode(9)

Now, let's build the graph. Node v3 will be a LnNode that will take the Ln of the value of v1, v4 will be a LogNode that will take the log of the value of v2. Node v5 will multiply the value of nodes v3 and v4. Node v6 will be a TanNode that will take the tangent of the value of v1, while node v7 will be a CotNode that will take the cotangent of the value of node v2. Node v8 will multiply the values of nodes v6 and v7 and finally node v9 will divide the value of node v5 by the value of node v8.

    v3 = pica.LnNode(v1)
    v4 = pica.LogNode(v2)
    v5 = pica.MultNode(v3,v4)
    v6 = pica.TanNode(v1)
    v7 = pica.CotNode(v2)
    v8 = pica.MultNode(v6,v7)
    v9 = pica.DivNode(v5,v8)

Now we are going to initialize our nodes and make the connections between them.

    g.node(v1)
    g.node(v2)
    g.connect(v1,v3)
    g.connect(v2,v4)
    g.connect(v3,v5)
    g.connect(v4,v5)
    g.connect(v1,v6)
    g.connect(v2,v7)
    g.connect(v6,v8)
    g.connect(v7,v8)
    g.connect(v5,v9)
    g.connect(v8,v9)

We will use the forward method to evaluate the result of the function.

    result = g.forward()
    print(f"Result: {result}")
    
The result will be as follows:

    Result:3.1682538333896275

Now we are going to use the backward method to obtain the gradients of the variables.

    g.backward()
    print(f"X Gradient: {v1.gradient}, Y Gradient: {v2.gradient}")

The result will be as follows:

    X Gradient: -59.658635964251935, Y Gradient: 20.66558448959415


## Example with Exponents

Let's represent the function f(x,y) = (sin(x)^2) + (15^y) through a computational graph. We will obtain the result of the function and also the gradient of the variables x,y.

First you have to install the package: 

    pip install picalib

Then, you have to import the library:

    import pica

Node v1 will be a node of type ValueNode with a value of 2, node v2 will be of the same type with a value of 15. Node v3 will represent variable X and will have a value of 3, while node v4 will represent variable Y and will have a value of 5. Node v5 takes the sine of the value of node v3.  Node v6 will raise node v5 to the square (node v1), and node v7 will raise node v2 to y (node v4). Finally, node v8 will add the values of nodes v6 and v7.

    g = pica.Graph()
    v1 = pica.ValueNode(2)
    v2 = pica.ValueNode(15)
    v3 = pica.VariableNode(3)
    v4 = pica.VariableNode(5)
    v5 = pica.SinNode(v3)
    v6 = pica.PowerNode(v5,v1)
    v7 = pica.ExpNode(v4,v2)
    v8 = pica.SumNode(v6,v7)

Now we are going to initialize our nodes and make the connections between them.

    g.node(v1)
    g.node(v2)
    g.node(v3)
    g.node(v4)
    g.connect(v3,v5)
    g.connect(v1,v6)
    g.connect(v5,v6)
    g.connect(v2,v7)
    g.connect(v4,v7)
    g.connect(v6,v8)
    g.connect(v7,v8)

We will use the forward method to evaluate the result of the function.

    result = g.forward()
    print(f"Result: {result}")
    
The result will be as follows:

    Result:759375.0027390523

Now we are going to use the backward method to obtain the gradients of the variables.

    g.backward()
    print(f"X Gradient: {v1.gradient}, Y Gradient: {v2.gradient}")

The result will be as follows:

    X Gradient: 0.10452846326765347, Y Gradient: 2056425.6214619908
