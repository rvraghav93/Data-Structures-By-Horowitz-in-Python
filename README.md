#Data Structures By Horowitz - As iPython Notebooks

## About

Python implementation of the examples in the text book [Fundamentals of Data Structures in C++ by E.Horowitz, S.Sahni and Mehta](http://www.amazon.in/dp/8173716064/ref=cm_sw_r_tw_dp_P0I9sb188T11M).
This is a part of my contribution to the textbook companionship project organized by the [FOSSEE](http://python.fossee.in/) initiative of [IIT Bombay](https://www.iitb.ac.in/)

## Sample - Heap Sort

FIGURE 7.7, PAGE 416
--------------------

.. code:: python

    # Array interpreted as binary tree
    
    # Imports to graphically visualize the Heap
    # Requires graphviz and pydot2 libraries to be pre-installed
    import networkx as nx
    import numpy as np
    import matplotlib.pyplot as plt
    import collections # For using OrderedDict with nx.Graph objects
    %matplotlib inline
    plt.axis('off')
    
    # NOT IN TEXTBOOK
    # Function to convert the array representation of tree to networkx edges
    def to_edge_pairs(tree_array):
        """ Convert array representation of tree to edge pair tuples to add to networkx graph """
        edges = []
        size = len(tree_array)
        # NOTE: index starts from 1 for the tree_array.
        for i in range(1,size+1):
            if ( 2*i <= size ): # If Left child exists
                edges.append((tree_array[i], tree_array[2*i]))
            if ( 2*i + 1 ) <= size : # If Right child exists
                edges.append((tree_array[i], tree_array[2*i + 1]))
        return edges
    
    
    print "The input array ( Represented as dictionary ) : "
    print dict_a_cpy
    
    G = nx.DiGraph()
    G.node = collections.OrderedDict() 
    # To preserve the order of edges ( Right / Left subtree will be displayed in the correct order )
    G.add_edges_from(to_edge_pairs(dict_a_cpy))
    nx.draw(G, nx.graphviz_layout(G,prog='dot'), arrows=False, with_labels=True)
    plt.title("Input array")
    plt.show()
    
    print "Heap representation using the MaxHeap data structure ( Chapter 5 ): "
    heap_a = MaxHeap()
    sorted_arr = list()
    [ heap_a.Push(list_a[i]) for i in range(1, n+1) ]
    print heap_a.heap
    
    G.clear()
    G.add_edges_from(to_edge_pairs(heap_a.heap))
    nx.draw(G, nx.graphviz_layout(G,prog='dot'), arrows=False, with_labels=True, node_color='b')
    plt.title("Initial Heap")
    plt.show()
    
    sorted_arr.append(heap_a.Pop())
    
    while ( not heap_a.IsEmpty()):
        G.clear()
        G.add_nodes_from( list(heap_a.heap.itervalues()) )
        G.add_edges_from(to_edge_pairs(heap_a.heap))
        nx.draw(G, nx.graphviz_layout(G,prog='dot'), arrows=False, with_labels=True, node_color='b')
        plt.title("Heap Size = " + str(heap_a.heapSize))
        plt.show()
        print "Sorted : ", sorted_arr
        sorted_arr.append(heap_a.Pop())
        
    print "The final sorted array is : ", sorted_arr

.. parsed-literal::

    The input array ( Represented as dictionary ) : 
    {1: 26, 2: 5, 3: 77, 4: 1, 5: 61, 6: 11, 7: 59, 8: 15, 9: 48, 10: 19}



.. image:: Chapter\ 7/output_42_1.png


.. parsed-literal::

    Heap representation using the MaxHeap data structure ( Chapter 5 ): 
    {1: 77, 2: 61, 3: 59, 4: 48, 5: 19, 6: 11, 7: 26, 8: 1, 9: 15, 10: 5}



.. image:: Chapter\ 7/output_42_3.png



.. image:: Chapter\ 7/output_42_4.png


.. parsed-literal::

    Sorted :  [77]



.. image:: Chapter\ 7/output_42_6.png


.. parsed-literal::

    Sorted :  [77, 61]



.. image:: Chapter\ 7/output_42_8.png


.. parsed-literal::

    Sorted :  [77, 61, 59]



.. image:: Chapter\ 7/output_42_10.png


.. parsed-literal::

    Sorted :  [77, 61, 59, 48]



.. image:: Chapter\ 7/output_42_12.png


.. parsed-literal::

    Sorted :  [77, 61, 59, 48, 26]



.. image:: Chapter\ 7/output_42_14.png


.. parsed-literal::

    Sorted :  [77, 61, 59, 48, 26, 19]



.. image:: Chapter\ 7/output_42_16.png


.. parsed-literal::

    Sorted :  [77, 61, 59, 48, 26, 19, 15]



.. image:: Chapter\ 7/output_42_18.png


.. parsed-literal::

    Sorted :  [77, 61, 59, 48, 26, 19, 15, 11]



.. image:: Chapter\ 7/output_42_20.png


.. parsed-literal::

    Sorted :  [77, 61, 59, 48, 26, 19, 15, 11, 5]
    The final sorted array is :  [77, 61, 59, 48, 26, 19, 15, 11, 5, 1]

## Installation and Dependencies

The python codes are written in [IPython Notebooks](http://ipython.org/notebook.html) Version 2.0 - Development Build as on Jan 2014:

To install ipython in debian based systems like Debian:
    
    sudo apt-get install ipython-notebook

To install ipython in Fedora 18 and Newer:
    
    sudo yum install python-ipython-notebook

To check version:
    
    ipython --version

If the version is not 2.0, [use the development build](https://github.com/ipython/ipython)

Clone the repo:

    git clone --recursive https://github.com/ipython/ipython.git

Move into the directory

    cd ipython

Do a system wide install :

    sudo python setup.py install

Matrix Operations are carried out via Numpy libraries.
To get the Scipy libraries (which include numpy):

    sudo apt-get install python-scipy

or 

    sudo yum install python-scipy

Once all the packages and dependencies are installed.

Clone the repository and move into it:

    git clone https://github.com/rvraghav93/Data-Structures-By-Horowitz-in-Python.git DataStructPy
    cd DataStructPy

Move into the required chapter (Replace N by chapter number):

    cd Chapter\ N

Run IPython Notebook

    sudo ipython notebook
    
    
For more help on IPython notebook try [this official documentation](http://ipython.org/ipython-doc/stable/interactive/notebook.html).

## Contribute

If you wish to contribute too, visit [FOSSEE](http://fossee.in/) and see if you can find anything matching your interests.

## Copyright

The copyrights for all the codes belong to the FOSSEE Department of IIT Bombay.

## Contact

For any queries or help feel free to contact me at:

IRC:      rvraghav93

GMail:    rvraghav93@gmail.com

## About Me:

I am Raghav RV, an Undergrad student of Anna University interested in FOSS, python, C++, computer vision, big data etc...
