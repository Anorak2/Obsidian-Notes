
2025-11-16

Tags: [[Software Security Evaluation]] [[Computer Science]]
# Mod-Ref Analysis
The basic idea of Mod/Ref analysis is that we ignore all pointers, parameters, and locals for the time being and instead build a simple call graph which can be repurposed with the dataflow algorithm. This approach allows us to quickly get a very simple initial approximation.

1. Collect the variables immediately modified inside of a function F (ignoring functions it calls)
2. Build the simple call graph
3. Repurpose the call graph for the dataflow algorithm. In practice this means collapsing cycles down into a single node and adding a dummy leave node.
4. Run the call graph to saturation

**IMOD:** Stands for Immediate MODifications
**IREF**: Stands for Immediate REFerences

#### Expanding Our Analysis
The truth is that ignoring callees, locals, and parameters massively restricts our analysis so what if we remove it? The good news is that the GMOD computation is the same, the bad news is that now we can't collapse cycles, we'll need the compound call graph, and more elaborate IMOD calculation is necessary now.

# References
[[Dataflow Frameworks]]

