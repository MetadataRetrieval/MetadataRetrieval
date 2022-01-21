# submission176_code

This project provides the code of the experiments for entity-based retrieval with entity expansion and ranking functions that take hierarchical relations of entities into account.

## Overview

* [SML extension](https://github.com/DatasetRetrieval/submission176_code/tree/main/slib-sml/src/main/java/slib/sml/sm/core/engine)(node level computation for HCF-IDF)

* [slibAPI](https://github.com/DatasetRetrieval/submission176_code/tree/main/slibAPI) (Wrapper)

* [GATE Mimír plugins](https://github.com/DatasetRetrieval/submission176_code/tree/main/Mimir6.2)

* [Mimír Search API](https://github.com/DatasetRetrieval/submission176_code/tree/main/MimirSearchAPI) (Wrapper)

* [Mimir Test](https://github.com/DatasetRetrieval/submission176_code/tree/main/MimirTest/mimirTest)


## Installation instructions

prerequisites: The following instructions have been tested with Java 8 and Maven 3.3.9


#### 1.) SML library 0.9.5

Download the [slib](https://github.com/sharispe/slib) project. Further information about semantic similarity measures implemented in slib can be found on the webpage: http://www.semantic-measures-library.org/

In order to compute the node level for the HCF-IDF we adjusted the Semantic Measures Engine in the slib-sml subproject. As there is no plugin API in slib, add the methods given in  ``slib.sml.sm.core.engine.SM_engine`` to the respective file in slib/sml.

Build and install the SML library with Maven.

#### 2.) slibAPI and used ontologies

The slibAPI is wrapper project for the SML library and loads all ontologies as external knowledge sources. Download and install the slibAPI. Create a ``resource/vocabs`` folder under the root folder ``slibAPI``. Download the following ontologies in owl format from [OBO Foundry](http://www.obofoundry.org/) and store it in the ``vocabs`` folder: 

* [bfo](http://www.obofoundry.org/ontology/bfo.html)
* [bto](http://www.obofoundry.org/ontology/bto.html)
* [chebi](http://www.obofoundry.org/ontology/chebi.html)
* [cl](http://www.obofoundry.org/ontology/cl.html)
* [doid](http://www.obofoundry.org/ontology/doid.html)
* [envo](http://www.obofoundry.org/ontology/envo.html)
* [flopo](http://www.obofoundry.org/ontology/flopo.html)
* [go](http://www.obofoundry.org/ontology/go.html)
* [hp](http://www.obofoundry.org/ontology/hp.html)
* [ino](http://www.obofoundry.org/ontology/ino.html) 
* [mod](http://www.obofoundry.org/ontology/mod.html)
* [ncbitaxon](http://www.obofoundry.org/ontology/ncbitaxon.html)
* [ncit](http://www.obofoundry.org/ontology/ncit.html)
* [obi](http://www.obofoundry.org/ontology/obi.html)
* [pato](http://www.obofoundry.org/ontology/pato.html)
* [po](http://www.obofoundry.org/ontology/po.html)
* [ppo](http://www.obofoundry.org/ontology/ppo.html)
* [rex](http://www.obofoundry.org/ontology/rex.html)
* [symp](http://www.obofoundry.org/ontology/symp.html)
* [to](http://www.obofoundry.org/ontology/to.html)
* [uberon](http://www.obofoundry.org/ontology/uberon.html) (core ontology - uberon.owl + Uberon extended - ext.owl)

Build and install the slibAPI project.

#### 3.) GATE Mimír

Download and install [GATE Mimír version 6.2](https://github.com/GateNLP/mimir/releases). Further information on the requirements of GATE Mimír and a user guide can be found on their webpage: https://gate.ac.uk/mimir/.

Install the scorer plugins provided in the ``GATE Mimír/plugins`` folder as described in [Mimír's user guide](https://gate.ac.uk/mimir/doc/mimir-guide.pdf). 

All ontologies needs to be loaded during Mimír's start. Therefore, initialize the  slibAPI/SML class in the MimirScorerService. Have a look at the provided file in the ``Mimir6.2/webapp`` folder 

Now index a corpus with GATE Mimír, e.g., download the [BEFChina](https://bef-china.com/) datasets and annotate them with the [OrganismTagger](http://dx.doi.org/10.1093/bioinformatics/btr452) and the [BiodivTagger](https://aclanthology.org/2020.lrec-1.560.pdf).
For testing purposes one can also use any text files and annotate them with the default [GATE ANNIE](https://gate.ac.uk/ie/annie.html) pipeline (extracts e.g., Location, Person, Date and Time).

#### 4.) Mimír Search API

The Mimír Search API project is a wrapper for Mimír and provides more convenient access for developers to the Mimír's search.
Download and install the Mimír search API project. In the ``MimirSearch.java`` file adjust the index URL (so far no config file available).

#### 5.) Mimír Test

The MimirTest project provides the code we ran to evaluate entity expansion and entity-based ranking functions on two test collections. It can be also used as example code for own search purposes and evaluations. 

## License
The code in this project is distributed under the terms of the [GNU LGPL v3.0.](https://www.gnu.org/licenses/lgpl-3.0.en.html)
