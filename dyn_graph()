import networkx as nx
import numpy as np
from random import random
import matplotlib.pyplot as plt
from bisect import bisect

def plotter(G):
    #plotting
    pos=nx.spring_layout(G)
# nodes
    nx.draw_networkx_nodes(G,pos,node_size=700)
#edges
    nx.draw_networkx_edges(G,pos,width=2,alpha=0.6,edge_color='black')
# labels
    nx.draw_networkx_labels(G,pos,font_size=20,font_family='sans-serif')
    nx.draw_networkx_edge_labels(G,pos,nx.get_edge_attributes(G,'weight'))
    plt.show()

def weighted_choice(choices):
    values, weights = zip(*choices)
    total = 0
    cum_weights = []
    for w in weights:
        total += w
        cum_weights.append(total)
    x = random() * total
    i = bisect(cum_weights, x)
    return values[i]
def matrix_graph(b,G,dim):
    for x in range(0,dim[1]):
        for y in range(0,dim[2]):
            G.add_edge(x,y,weight={'weight'+str(i):"%.2f" % b[i].item((x,y)) for i in range(0,len(b)) })

def filler(dim):
    #b=np.zeros(shape=dim)
    a=np.zeros(shape=dim)
    for h in range(0,dim[0]):
        for j in range(0,dim[1]):
            for i in range(0,dim[2]):
                a[h,j,i]=random()
    return normalize(a)

def normalize(a):
    b=a/ a.sum(axis=1)[ :,np.newaxis,:]
    return b

def dynamic(G,pos,plane):
    nexts=[(x,float(nx.get_edge_attributes(G,'weight').get((pos,x)).get('weight'+str(plane)))*100) for x in G.neighbors(pos)]
    return weighted_choice(nexts)

class Grapher(object):
    __Matrix=None
    __Graph=None
    __Dim=None
    __Position=0
    def __init__(self):
#        Constructor
        self.__Matrix= np.zeros(shape=dim)
        self.__Graph= nx.DiGraph()
        self.__Dim = dim
        self.__Position=0

    def grapher(self):
        return self
    def matrix (self):
        return self.__Matrix
    def graph(self):
        return self.__Graph
    def dim(self):
        return self.__Dim
    def position (self):
        return self.__Position
    def casualfill(self, dim):
        self.__Matrix=filler(dim)
        self.__Dim=dim
        G=nx.DiGraph()
        matrix_graph(self.__Matrix,G,self.__Matrix.shape)
        self.__Graph=G
    def setmatrix(self,MATRIX):
        self.__Matrix=MATRIX
        G=nx.DiGraph()
        matrix_graph(self.__Matrix,G,MATRIX.shape)
        self.__Graph=G
    def graph_generator(self):
        G=nx.DiGraph()
        matrix_graph(self.__Matrix,G,self.__Matrix.shape)
        self.__Graph=G
        return self.__Graph
    def move(self,plane):
        self.__Position=dynamic(self.__Graph,self.__Position, plane)
        return self.__Position
        
#main  
dim=(2,5,10)
pos=3

G=Grapher()
G.casualfill(dim)
