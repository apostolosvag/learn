# What is model-dependent analysis?

The previous section on {doc}`../1_the_fourier_transform/fourier_transforms_for_reflectometry_analysis` introduced a **model-independent approach** to reflectometry analysis.
However, as was noted in this section, this approach does not offer a complete interpretation of the system we are investigating. 
Due to the limited $q$-range and the limited $q$-resolution that we can probe experimentally, as well as the ever present phase problem. 
A more common methodology for reflectometry analysis takes a model-dependent approach {cite}`lovell_analysis_1999`. 

Model-dependent is an analytical tool used to tackle a broad range of problems in the physical sciences. 
You may have already encountered model-dependent analysis, without really considering what it is. 
If you have "fit" data to some analytical model, like an equation, then you have applied **model-dependent analysis**.
````{margin}
```{note}
Some examples of model-dependent analysis that might be familiar include modelling **enzyme kinetics** with the Michaelis–Menten equation or finding the **force constant** for a diatomic molecule from the vibrational spectra. 
```
````

The logical process underlying model-dependent analysis is rather simple, we need three things:
- a way to **simulate** something similar to our experimental data; 
- some experimental data to **compare** with; and 
- a **figure of merit** to compare our simulation to our experiment. 

The word **simulation** above is being used broadly, but in the context of neutron reflectometry, we are interested in calculating the reflectivity that some model system would produce. 
We will not cover how to get the experimental data, but we will cover in detail how to simulate our data and how we compare it with the experimental data. 
Additionally, we will look at how we can **improve** our model and some algorithms that are popular in reflectometry analysis to do this. 

A general workflow for model-dependent analysis is shown below. 
First, we propose some **model** that we believe can accurately describe the system that we are studying. 
Then, we use some **functional construct** to calculate what the *experimental* data from such a system would look like. 
We compare this calculated, model data with our measured, experimental data and then **change our model** such as to improve the agreement between the two. 

```{mermaid}
---
align: center
caption: The logical flow of model-dependent analysis, showing the improvement of the model based on the agreement with the data.
---
    flowchart LR
        id1{{Propose a model}}
        id2((Calculate the<br>model reflectometry))
        id3>Compare with<br>experimental data]
        id1-->id2-->id3-- Improve<br>the model-->id2
        style id1 fill:#0173B288
        style id2 fill:#029E7388
        style id3 fill:#D55E0088
```

```{warning}
It is important to be aware, that the process of proposing a model, and therefore the entire model-dependent analysis methodology, leads to an **inherent bias** in the modelling process. 
By defining that the data must be represented by some model there is a clear assumption being made. 
Typically this is a **fair assumption** to make, as we have an understanding of the synthesis or preparation of our sample that offers insight and expectations into the resulting structure. 
However, we must ensure that the known physics and chemistry in our system is represented in our model, where possible, or else the model can lead to "garbage in, garbage out" {cite}`mayer_drawing_2010`.
```
