# Union Find
This is a UnionFind module that use TypeScript

## Installation
`$ npm install --save unionfind-typescript`

## Getting started


```
//import UnionFind
const UnionFind = require( "../dist/union-find").UnionFind;
//import enums
const enumUnionMode = require( "../dist/union-find").unionMode;
const enumRepeatExistNode = require( "../dist/union-find").repeatExistNode;

//Initialize
let nodes= ["a","b",123,{"name":"d"},"e"];
let unionFind = new UnionFind(
    //nodes
    nodes,
    //paths
    [["a","b"]],
    //configs
    {
        unionMode:enumUnionMode.normal,
        repeatExistNode:enumRepeatExistNode.ignore,
        customToString:function(node){
            return "<" + node + ">";
        }
    }
);

//union two node
unionFind.union("b","e");

//find root node
unionFind.findRoot("e") // =>"a"


unionFind.compress(); // All paths are compressed

//get UnionNode with "e"
let e = unionFind.getUnionNode("e");

console.log(e.node) // =>"e"
console.log(e.parent.node) // =>"a"

```

## Configs


option | value | description |
---|---|---
unionMode | **default : normal**  | How to union
| |  normal | Union two subtrees
| |  height | Balance the height of the tree
| |  compress | Union two subtrees,the second tree should link to the first nodes'root
|repeatExistNode | **default : ignore** | How to deal with when there are duplicate nodes detected
| |   ignore | Ignore
| |   warning | Console a waring message
| |  error | Throw an error



## APIs
### Build documents
`$ npm run doc`