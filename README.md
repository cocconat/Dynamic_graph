# Dynamic_graph

python class which combine Numpy and Networkx for create a graph from a n3_array (suppose n=5)

->Every edge has n (5) attributes, which are defined by the matrix itself. <-

Then a dynamic is applied on the graph trough the method move(plane) which evaluate the weighted probability of each edge, the variable "plane" set on which layer of the 3d matrix your acting the dynamic.

The class Grapher manage both the np.array and the nx.Graph.
it s possible to generate a normalized random 3d-matrix

#class Grapher(object):
    __Matrix=None
    __Graph=None
    __Dim=None
    __Position=0
    def __init__(self):
'''       Constructor'''
        self.__Matrix= np.zeros(shape=dim)
        self.__Graph= nx.DiGraph()
        self.__Dim = dim
        self.__Position=0

'''    dim is a 3-tuple (i,h,j) '''

'''    The methods: '''
    def casualfill(dim) 
    #-- generate a graph from a random matrix
    def setmatrix(MAT) 
    #-- generate a graph from a np.array of dimension 3 (dim is MAT.shape)
    def move (plane) 
    #-- extract a node among neighbors() then change __Position to the new node, the variable "plane" set on which layer of the 3d matrix your acting the dynamic.

