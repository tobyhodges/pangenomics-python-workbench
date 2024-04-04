---
title: "Plotting"
teaching: 10
exercises: 10
questions:
- "How can I plot a graph with vertex and edges"
- "How can I plot histograms"

objectives:
- "Create a graph with NetworkX"
- "Create a graph with matplotlib"

keypoints:
- "NetworkX is a library"
- "matplotlib is a library"
---

Let's create a simple graph with NetworkX and visualize it using Plotly. 
In this example, we'll create a graph with four nodes and four edges.
Nodes are represented as red markers and edges are represented as black lines.

~~~
import networkx as nx
import plotly.graph_objects as go
~~~
:{language-python}

We create a simple undirected graph G.
~~~
# Create a simple graph
G = nx.Graph()
G.add_edges_from([(1, 2), (2, 3), (3, 4), (4, 1)])
~~~
:{language-python}


We define positions for nodes using a spring layout algorithm (spring_layout). This assigns positions to nodes in such a way that minimizes the forces between them, resulting in a visually appealing layout.
~~~
# Define positions for nodes
pos = nx.spring_layout(G)
~~~
:{language-python}


We create traces for edges and nodes. Each edge is represented by a line connecting the positions of its 
two endpoints, and each node is represented by a marker at its position.
~~~
# Create edge traces
edge_traces = []
for edge in G.edges():
    x0, y0 = pos[edge[0]]
    x1, y1 = pos[edge[1]]
    edge_trace = go.Scatter(x=[x0, x1], y=[y0, y1], mode='lines', line=dict(width=3))
    edge_traces.append(edge_trace)
~~~
:{language-python}

We create a Plotly figure with the specified data and layout. We disable the legend for simplicity.


~~~
node_x = []
node_y = []
for node in G.nodes():
    x, y = pos[node]
    node_x.append(x)
    node_y.append(y)

node_trace = go.Scatter(x=node_x, y=node_y, mode='markers', marker=dict(size=14, color='rgb(255,0,0)'))
~~~
:{language-python}

Create the Plotly figure
~~~
fig = go.Figure(data=edge_traces + [node_trace], layout=go.Layout(showlegend=False))
~~~
:{language-python}

We show the figure using Plotly's show() method.
# Show the figure
~~~
fig.show()
~~~
:{language-python}


~~~
def visualize_simplicial_complex(simplex_tree, filtration_value, vertex_names=None, save_filename=None, plot_size=1, dpi=600, pos=None):
    G = nx.Graph()
    triangles = []  # List to store triangles (3-nodes simplices)
    
    for simplex, filt in simplex_tree.get_filtration():
        if filt <= filtration_value:
            if len(simplex) == 2:
                G.add_edge(simplex[0], simplex[1])
            elif len(simplex) == 1:
                G.add_node(simplex[0])
            elif len(simplex) == 3:
                triangles.append(simplex)
    
    # Calculate node positions if not provided
    if pos is None:
        pos = nx.spring_layout(G)
    
    # Node trace
    x_values, y_values = zip(*[pos[node] for node in G.nodes()])
    node_labels = [vertex_names[node] if vertex_names else str(node) for node in G.nodes()]
    node_trace = go.Scatter(x=x_values, y=y_values, mode='markers+text', hoverinfo='text', marker=dict(size=14), text=node_labels, textposition='top center', textfont=dict(size=14))
    
    # Edge traces
    edge_traces = []
    for edge in G.edges():
        x0, y0 = pos[edge[0]]
        x1, y1 = pos[edge[1]]
        edge_trace = go.Scatter(x=[x0, x1, None], y=[y0, y1, None], mode='lines', line=dict(width=3, color='rgba(0,0,0,0.5)'))
        edge_traces.append(edge_trace)
    
    # Triangle traces
    triangle_traces = []
    for triangle in triangles:
        x0, y0 = pos[triangle[0]]
        x1, y1 = pos[triangle[1]]
        x2, y2 = pos[triangle[2]]
        triangle_trace = go.Scatter(x=[x0, x1, x2, x0, None], y=[y0, y1, y2, y0, None], fill='toself', mode='lines+markers', line=dict(width=2), fillcolor='rgba(255,0,0,0.2)')
        triangle_traces.append(triangle_trace)
    
    # Configure the layout of the plot
    layout = go.Layout(showlegend=False, hovermode='closest', xaxis=dict(showgrid=False, zeroline=False, tickfont=dict(size=16, family='Arial, sans-serif')), yaxis=dict(showgrid=False, zeroline=False, tickfont=dict(size=16, family='Arial, sans-serif')))
    
    fig = go.Figure(data=edge_traces + triangle_traces + [node_trace], layout=layout)
    
    # Set the figure size
    fig.update_layout(width=plot_size * dpi, height=plot_size * dpi)
    
    # Save the figure if a filename is provided
    if save_filename:
        pio.write_image(fig, save_filename, width=plot_size * dpi, height=plot_size * dpi, scale=1)
    
    # Show the figure
    fig.show()

    return G
~~~
:{language-python}
