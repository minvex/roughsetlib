A Java implementation of Rough Sets (a new set theory as proposed by Pawlak). Library contains object forms of Infomation Systems, Approximation Spaces , Rough Sets , Rough Temporal Model and a Logic to express rough sets. Also graphics modules are present to visualize rough sets and dynamic models in approximation spaces with varying partitions.

![http://roughsetlib.googlecode.com/files/Screenshote.png](http://roughsetlib.googlecode.com/files/Screenshote.png)

# Introduction #
Temporal Rough Logic is a combination of both Normal and Temporal Modal Logics. TRL formulas are interpreted over Dynamic Approximation Spaces. For checking validiy in TRL a Prefixed Tableaux System was proposed by Md.Aquil Khan and Dr.M.Banerjee in http://www.springerlink.com/content/v16134r58kr0j842/. We aim to implement TRL-Models as structures in a programming language. For this we first require implementations of Approximation Spaces, Rough Sets, DAS. As all these require sets of objects, attributes etc. to be defined we begin with an implementation of Sets. Then Information Systems, Approx. Spaces, DAS, TRL Models, TRL Logic are built respectively.

# Details #
This library was created as a part of my MSc. Mathematics Project at IIT Kanpur. A complete report of the project is accesible at:

To start working, download and extract http://roughsetlib.googlecode.com/files/Rough%20Set_1.1.zip. Java codes are kept in /src folder. Also you need graphViz installed to use the visualization modules.

# Theory #
In classical set theory either an element belongs to a set or it doesn’t. In rough set theory a set is approximated by its lower and upper approximations which denote the degree of overlap among set and partitions in underlying Approximation Space. In a dynamic approximation space(DAS) the underlying partitions change with time as more information arrives, changing approximations of rough sets. To express information, Attribute-Value systems are used. A formal description of Information Systems, Approximation Spaces, Rough Sets, DAS and a logic for DAS is given in the following sections.

## Information Systems ##
http://en.wikipedia.org/wiki/Attribute-value_system
![http://roughsetlib.googlecode.com/files/Screenshot-1.png](http://roughsetlib.googlecode.com/files/Screenshot-1.png)
## Approximation Space and Rough Sets ##
http://en.wikipedia.org/wiki/Rough_set
![http://roughsetlib.googlecode.com/files/Screenshot-2.png](http://roughsetlib.googlecode.com/files/Screenshot-2.png)

# Example #
Let us create a TRL Model where partitions collapse into each other with time. To do so we first declare a set of objects O = {1, 2....K}, set of attributes A = {1, 2, 3....L}. Then we assign random valuation V to these attributes, and obtain INFS\_0 = InformationSystem?(O,A,V); function. Now we remove attributes one by one from INFS\_0 to obtain INFS\_K = INFS\_K+1.removeAttribute(K). As INFS\_L has zero attributes, no objects are distinguishable and there is only one partition. Now we convert this array of Information Systems to Approximation Spaces using APSPi? = toApproximationSpace(InformationSystem? INFSi?). Thus, we have a Dynamic Approximation Space with partitions collapsing into each other as it loses information with time. Any L-wff can be evaluated over this DAS using evaluate(formula); function in code TRLModel.java.

```
	screen scr = new screen();

		InfoSystem infs = new InfoSystem();
		infs = infs.randomInfoSystem(100,30,2);
		scr.show(infs.getApproxSpace());

		for(int i=0;i<30;i++){
			infs = infs.removeAttribute(i+1);
			ApproxSpace apsp = infs.getApproxSpace();
                        scr.show(apsp);
		}

                RTLModel rtml = new RTLModel();
		rtml = rtml.randomRTLModel(2,100);
		
		Formula f1 = new Formula("g i i b 1 2 i n 2 n p b 1");
		System.out.println("FORMULA ---  "+f1.toNormal());
		System.out.println(rtml.isValid(f1));
		
		screen scr = new screen();
	        scr.show(rtml);

```

![http://roughsetlib.googlecode.com/files/DAS2.png](http://roughsetlib.googlecode.com/files/DAS2.png)