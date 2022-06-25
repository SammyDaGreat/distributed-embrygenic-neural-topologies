# Distributed Embryogenesis of Neural Topologies

Last updated 2021/06/21

## Introduction

This project generates neural network architectures through a cell-based, bottom-up approach. Instructions are given to individual neurons on how to connect to each other and produce new neurons. Starting from a minimal network strucutre, more complicated topologies emerge through the distributed, spontaneous developments of individual neurons. The cell-based instructions are gradually optimized through evolutionary algorithm.

__To see example topologies generated by this project, go to the "evolved_topologies" directory.__

To try it yourself, run __Evolution.py__

Dataset.py generates a toy dataset which imitates visual stimulations to two retinas (see discussion on "modularity" below).

## Motivation

There is abundant research on automatic generation of more efficient neural network architectures. One fundamental question for those attempts is how neural architecture should be represented in code.

Stochastic methods such as NEAT (Neural Evolution of Augmenting Topologies) adopt the "blueprint" approach, in which the object to be optimized is an explicit statement of the nodes and connections in a neural topology.
On the other hand, gradient-based approaches, notably represented by NAS (Neural Architecture Search), uses an RNN to iteratiely construct the desired neural network. Yet arguably they still adopt a "top-down" approach, where the RNN masterminds the entire network topology.

This approach has many shortcomings. One notable example is __modularity__. When a successful local topology is produced, it is unclear how we can replicate that local success to other parts where it would also be helpful, without explicitly coding replication of modules.
It is helpful to think about how modularity emerges in biological organisms. For example, why do mutations create babies with 6 fingers on a hand, but not 5.5 fingers? This is because the human body (and its brain) is created not through a top-down approach, but a bottom-up one. In an embryogenic state (and also after birth), cells interact, change, and split (create new cells) according to instructions given by genes, and structures emerge therefrom. For cells in similar conditions, they follow similar developmental paths, creating similar structures that are seemingly "modular".

## Implementation

This project is an attempt to make use of that biological inspiration. In this project, every neural network goes through an embryogenic state where the topology is grown interatively. Each neuron takes up a place in a two-dimensional space. They look for nearby neurons with certain attributes to establish neural connections. Those attributes include the neuron's in and out degrees (number of i/o neurons connected to it), its path of historical development in embryogeny, and its distance from the target neuron. If two neurons already have a connection weight in between them, they would also consider spawning a new neuron half-way on that connection. These two basic operations (addConnection and InsertNode) are inspired by NEAT, and should theoretically allow the construction of any feedforward neural network architecture.

(More detailed descriptions to come)

See __log.txt__ for historical developments on the project, concerns, and possible paths for future improvement.
