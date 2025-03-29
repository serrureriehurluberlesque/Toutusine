# Toutusine

The Toutusine is a mAll, a mall that can craft all. This project is a set of blueprints in Factorio to make a mAll that can craft automatically anything. Logics in the Toutusine define what need to be produce by comparing logistic requests and logistic stocks, compute intermediate products needed, and set recipes accordingly on factories.

* Work directly from the logistic network
  * get all requests from the logistic network and from orbital request 
  * get aso the stocks of the logistic network so that only what needs to be crafted is crafted
* Compute the products needed to be craft directly from the recipe on the available factories. It works even with mods or other if the recipes are modified.
  * It also manages the order of the recipes so that it won't be block even if there is multiple step to the end product.
* Handle quality recipes, it differenciates the quality of products
* It is "module aware", and know how to use productive modules when needed

## Why?
It started as a project to maximise the new "set recipe" feature of Factorio 2.0. It evolves as a super mall, that can also be used as a factory that craft everything from raw ressources. It's most usefull for ponctual medium productions, for exemple, to craft every items needed for a big blueprint with a lot of items not yet mass produced. It can also adapts to fix temporary failures in the mass production chain.

## How?
The Toutusine is splitted in 3 main parts:
* logics, this part do all the computations to know what needs to be crafted
* factories, this part as the factories that will craft the products and some logic to "communicate" with the logics part
* logistics, this part do all the logistics for the products, items and fluids between the stocks and the factories

## Installation
Get the blueprint_book_string.txt file in the latest release, that contains the string to import the blueprint book. In the blueprint book there is a blueprint with multiple blueprints. toutusine, for a blueprint with all parts already linked. There is also a blueprint for each parts separatly. More infos in the descriptions of the blueprints.
When the blueprint of the toutusine is constructed, you need to:
* Link the logistic network of the toutusine to your logistic network. You probably want to build the closest to your storage chest as it will get a lots of items for craft. 
* Put each available fluids into the tanks of the logistics parts

## Usage
Just set a request in the logistic network (for exemple by being in the logistic network and add a request in the player logistic request. Your item will be crafted if needed ressources are present.

There is multiple paramters to configure the toutsuine (default stocks needed, factories available, ...) that have yet to be documented.

## Missing features
As the toutusine is still a work in progress, there is missing features that will probably come one day:
* better sushi-fluids
  * faster fluids
  * more than one fluids recipes handling
* Usage of the recycle to craft quality products if asked

## Misc
Using fatul (https://github.com/nyurik/fatul) to store blueprint string in convenient json file
