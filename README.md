# UncNLPrograms (Currently Under Development)
A testing enviroment containing high-dimensional, nonlinear, and unconstrained optimization problems implemented in native Julia.
The UncNLPrograms is a subset of CUTEst, the latest evolution in the _Constrained and Unconstrained Testing Enviroment_. Each program defines an initial dimension, iterate, an objective function and it's corresponding gradient.

The purpose of this testing enviroment is to facilitate numerical experiements for Optimization schemes utilizing Automatic Differentation.
The UncNLPrograms interface resembles `NLPModels.jl` from the JuliaSmoothOptimizers orginization.

## Interface
Function           | Description
-------------------|------------
`Programs`		   | Lists each selectable program and it's current dimension 
`SelectProgram`	   | Returns a reference to the specified program
`adjdim!`		   | Adjust the specified programs dimensions to the given order
`obj`			   | Evaluate the programs objective function at a point x
`grad`			   | Evaluate the programs gradient function at a point x
`objgrad`		   | Economical evaluation of the programs gradient and objective at a point x
`hessAD`		   | Returns the full Hessian matrix of an objective function at a point x (by Forward AD)

## Installation
Using Pkg.jl:
```julia
julia> using Pkg
julia> Pkg.add(url="https://github.com/danphenderson/UncNLPTestSet.jl")
```  

Or from the REPL:
```julia
julia> ]
pkg> add "https://github.com/danphenderson/UncNLPTestSet.jl"
``` 


## Simple UncNLPrograms Use Case
```julia
# Lists name and dimension in the programs enviroment
Programs() 

# Store a reference to a program, as specified by the name given in Programs()
nlp = SelectProgram("SROSENBR")

adjdim!(nlp, 20)

obj(nlp, nlp.x0)

grad(nlp, nlp.x0)

objgrad(nlp, nlp.x0)
    
hessAD(nlp, nlp.x0)
```

## Development Items
1. Determine a suitable home for UncNLPrograms in the Julia ecosystem and/or utilize an existing structure (e.g. NLPModels.jl, JuMP.jl).
2. Optimize each programs implementation.
3. Check off each item in the Precompile warning list.
4. Overload Base.show(nlp)
