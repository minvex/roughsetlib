#Rough Set library with an implementation of Temporal Rough Models in Java

# Introduction #

Temporal Rough Logic is a combination of both Normal and Temporal Modal Logics. TRL formulas are interpreted over Dynamic Approximation Spaces. For checking validiy in TRL a Prefixed Tableaux System was proposed by Md.Aquil Khan and Dr.M.Banerjee in http://www.springerlink.com/content/v16134r58kr0j842/. In the following sections we describe various implementations/pseudocodes for Model Checking and Tableaux in TRL as defined by them. We aim to implement TRL-Models as structures in a programming language. For this we first require
implementations of Approximation Spaces, Rough Sets, DAS. As all these require sets of objects, attributes etc. to be defined we begin with an implementation of Sets. Then Information Systems, Approx. Spaces,
DAS, TRL Models, TRL Logic are built respectively.



# Details #
This library was created as a part of my MSc. Mathematics Project at IIT Kanpur. A complete report of the project is accesible at:

# Example #
Let us create a TRL Model where partitions collapse into each other with time. To do so we first declare a set of objects O = {1, 2....K}, set of attributes A = {1, 2, 3....L}. Then we assign random valuation V to
these attributes, and obtain INFS\_0 = InformationSystem(O,A,V); function. Now we remove attributes one by one from INFS\_0 to obtain INFS\_K = INFS\_K+1.removeAttribute(K). As INFS\_L has zero attributes, no objects are distinguishable and there is only one partition. Now we convert this array of Information Systems to Approximation Spaces using APSP[i](i.md) = toApproximationSpace(InformationSystem INFS[i](i.md)). Thus, we have a Dynamic Approximation Space with partitions collapsing into each other as it loses information with time. Any L-wff can be evaluated over this DAS using evaluate(formula); function in code TRLModel.java.