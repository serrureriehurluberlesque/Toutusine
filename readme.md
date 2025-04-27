# Toutusine

The Toutusine is a mall that can craft all. This repos provides a blueprint in Factorio to make the Toutusine. It consists mainly of two parts: A logic part with only decider and signals, that define what need to be produce by comparing logistic requests and stocks, compute intermediate products needed, and decide what need to be crafted and in which order. This logic part communicate with the other part, the factories part. This second part will receive "commands" of products needed to be crafted, set the correct recipes and asks ressources in logistics system. It use directly the logistic network and use a custom made logistic fluid system to request dynamically for fluids.

* Work directly from the logistic network
  * get all requests from the logistic network and from orbital request 
  * get also the stocks of the logistic network so that only what needs to be crafted is crafted
* Compute the products needed to be craft directly from the recipe on the available factories. It works even with mods or if the recipes are modified.
  * It also manages the order of the recipes so that it won't be stuck waiting for ressources. Even if there is multiple step to the end product.
* Handle quality recipes, it differenciates the quality of products
* It is "module aware", and know how to use productive modules when needed

## Why?
It started as a project to maximise the new "set recipe" feature of Factorio 2.0 (For each buildings producing with shema, you can send a signal to set the recipe dynamically). It evolves as a super mall, that can also be used as a factory that craft everything from raw ressources. It's most usefull for ponctual medium productions, for exemple, to craft every items needed for a big blueprint with a lot of items not yet mass produced. It can also adapts to fix temporary failures in the mass production chain.

## How?
The Toutusine is splitted in 2 main parts:
* logics, this part do all the computations to know what needs to be crafted. It consists mainly of decider, poles, circuits and signal.
* factories, this part consists of all the factories that will craft the products. There is some logic in it too, to "communicate" with the logics part, store the current schematics used, keep the number of items that still need to be crafted and so on.
  * this part also includes some logistics parts that could be splitted
    * The part for the items is handled by the logistic network with bot directly. But could be swapped for other things (Maybe for a latter version). Here is a old Proof of concept using belts as logistics: https://youtu.be/zR2bwmR8b_A?si=G-kUd3OInOPQDhH0
    * The part for the fluids is using custom made Sushi-fluids logistics, that allow to requests for a specific fluid in a tank linked to each factory. For now it works with only one fluid for each factory, but could be improved latter to allow multiple fluids recipes
    

## Installation
Get the  toutusine_string.txt file in the latest release, that contains the string to import the blueprint book. (You can also get the string from the repos files using for exemple fatul (https://github.com/nyurik/fatul) to encode from the toutusine.json file). The blueprint contains all the parts of the Toutusine. 
When the blueprint of the Toutusine is constructed, you need to:
* Link the logistic network of the Toutusine to your logistic network. You probably want to build it the closest to your storage chest as it will get a lots of items for craft. 
* Put each available fluids into the fluid tanks (You need to conenct your fluids to the 10 underground pipes at the right of the blueprint. One fluids for each pipe.

## Usage
Just set a request in the logistic network (for exemple by being in the logistic network and add a request in the player logistic request). Your item will be crafted if needed raw ressources are present.

There is multiple parameters to configure the Toutusine (default stocks needed, factories available, ...) that have yet to be documented. Also, there is feedback about which raw ressources is missing with alarms.

## Missing features
As the Toutusine is still a work in progress, there is missing features that will probably come one day:
* better sushi-fluids
  * more than one fluids recipes handling (this is tricky because i didn't find a way to know how to map which fluids go to which entry on the factory)
* Usage of recyclers to craft quality products if asked
* low tech version, using only belts and items you can find on nauvis
