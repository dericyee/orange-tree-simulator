## Classes: Orange Tree Simulator
Implement the OrangeTree and Orange classes


### OrangeTree
1. The OrangeTree class constructor should have the following properties:
age (number), isDead (boolean), height (number), maxAge (number), orange (array)

2. The OrangeTree class should have the following getters:
- isDead (to return state of orange tree)
- maxAge (to return value of the maxAge)

3. The OrangeTree class should have the following setters:
- isDead (to give the isDead property a new value)

4. The OrangeTree class should have the following methods:

```ageMe(){
  // age the tree by one year
  
  
  // height only increases for the first 10 years (in cm)
  
  
  // if tree is older than 3 years old and it is not dead, grow oranges.
  
  
  // If the tree's age has reached it's maximum limit. Then it should die.
}


hasAnyOranges(){
  // return a boolean value
}


pickAnOrange(){
          if (!this.hasAnyOranges){
            throw new error("No oranges in this tree.")
        }
        return this.oranges.pop()
}
```


### Orange Class
// lets let it start at diameter of 1.

class Orange {
    constructor(){
        this.diameter = 1
    }
}

module.exports = Orange;



### Runner Code
"use strict";

const OrangeTree = require('./tree')

let tree = new OrangeTree()

// ages the tree until it has oranges
while (!tree.hasAnyOranges()) {
    tree.ageMe()
}


let totalOranges = null;
// while the tree is not dead
while (!tree.dead){
    // for every year we have an empty basket
    const basket = []

    // while tree has oranges, pick and place it in our basket
    while (tree.hasAnyOranges()){
        basket.push(tree.pickAnOrange())
    }
    // keep track of how many oranges we have collected until the tree is dead
    totalOranges += basket.length
    let averageDiameter = basket.reduce((sum, orange) => {
        return sum + orange.diameter
    }, 0)

    console.log(`Year ${tree.age} Report`)
    console.log(`Harvest: ${basket.length} oranges with an average diameter of ${averageDiameter} cm`)
    console.log(`Tree height: ${tree.height}`)
    tree.ageMe()
}
console.log(`At last, the tree has died. It produced a total of ${totalOranges} oranges.`)

