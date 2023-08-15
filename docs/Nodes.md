# Nodes

PiCa allows you to represent a mathematical function by means of a computational graph, being able to evaluate both the reuse of the function and the derivative of its variables.

These are the nodes that exist in the library:

## Graph

The Graph object is the most important of all, since it is through this object that you are going to build the graph. The graph object has the following methods:

__init__: The constructor of the class.

__node__(node): Used to define nodes VariableNode.

__connect__(node1,node2): Used to connect two nodes.

__print_nodes__: Used to terminally view the nodes of the graph.

__draw_graph__: Used to graphically visualize the computational graph.

__forward__: Used to calculate the result of the function.

__backward__: Used to obtain the derivatives of the variables.



## VariableNode

The VariableNode node is used to define the variables for the function. This node takes as a parameter the value that will be given to it

The attributes of the node are:

__result__: The value of the node

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## ValueNode

The ValueNode is used to define variables whose gradient is not to be calculated. This node takes as a parameter the value that will be given to it

The attributes of the node are:

__result__: The value of the node

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## SumNode

The SumNode node is used to sum the value of two nodes. This node takes as parameters two other nodes.

The attributes of the node are:

__value__: The value of the first node.

__value2__: The value of the second node.

__result__: The result of the sum of the values of nodes.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## SubNode

The SubNode node is used to subtract the value of two nodes. This node takes as parameters two other nodes.

The attributes of the node are:

__value__: The value of the first node.

__value2__: The value of the second node.

__result__: The result of the subtraction of the values of nodes.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## MultNode

The MultNode node is used to multiply the value of two nodes. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the first node.

__value2__: The value of the second node.

__result__: The result of the multiplication of the values of nodes.

__gradient__: Where the gradient of the node is to be stored.

__gradient1__ : The gradient of X

__gradient2__ : The gradient of Y

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## DivNode

The DivNode is used to divide the value of two nodes. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the first node.

__value2__: The value of the second node.

__result__: The result of the division of the values of nodes.

__gradient__: Where the gradient of the node is to be stored.

__gradient1__ : The gradient of X

__gradient2__ : The gradient of Y

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## SinNode

The SinNode node is used to evaluate the sine of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the sine of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## CosNode

The CosNode node is used to evaluate the cosine of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the cosine of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## TanNode

The TanNode node is used to evaluate the tangent of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the tangent of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.


## CscNode

The CscNode node is used to evaluate the cosecant of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the cosecant of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## SecNode

The SecNode node is used to evaluate the secant of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the secant of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.


## CotNode

The CotNode node is used to evaluate the cotangent of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the cotagent of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## LogNode

The LogNode node is used to evaluate the log of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the log of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

## LnNode

The LnNode node is used to evaluate the ln of a node's value. This node takes two other nodes as parameters.

The attributes of the node are:

__value__: The value of the parameter node.

__result__: The result of the ln of the node value.

__gradient__: Where the gradient of the node is to be stored.

__children__: An array where the child nodes are stored.

__parents__: An array where the parent nodes are stored.

