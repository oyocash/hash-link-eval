# Hash, link, eval protocol

**Hash, link, eval** is a way to represent data structures.  Below you will see how to create hashes, link hashes, and evaluate hashes.


## Create hash

To create a *hash*, use the following format:

*OP_FALSE OP_RETURN hash [SHA256(string)] [string]*

### Examples

`OP_FALSE OP_RETURN hash 0xb4056df6691f8dc72e56302ddad345d65fead3ead9299609a826e2344eb63aa4 Bitcoin`
`OP_FALSE OP_RETURN hash 0x6d85bc0dd47219b5e674459d8fd392b672752474a6204a20fa85c27ab8389f80 Created by Satishi Nakamoto`
`OP_FALSE OP_RETURN hash 0x251622657b440e90a92dda4411d73117f3b279ab42529d43e8d69cc2cf7fc5c1 Just a dummy comment`


## Linking, Commenting, Custom actions

To link 2 hashes, use the following format:

*OP_FALSE OP_RETURN link [point] [destination] [relation]*

*Point* and *destination* are SHA256 hashes.  See "Create hash" for more info or you can use transaction hashes as well.
Imagine *point* as the starting point vector and *destination* as its direction.
*Relation* is the relation type.  You can use your own relations, or use some of the default ones. 

### Default relations: ###
* 0 - point extends destination
* 1 - point comments destination

### Examples

`OP_FALSE OP_RETURN link 0x6d85bc0dd47219b5e674459d8fd392b672752474a6204a20fa85c27ab8389f80 0xb4056df6691f8dc72e56302ddad345d65fead3ead9299609a826e2344eb63aa4 0`
`OP_FALSE OP_RETURN link 0x251622657b440e90a92dda4411d73117f3b279ab42529d43e8d69cc2cf7fc5c1 0xb4056df6691f8dc72e56302ddad345d65fead3ead9299609a826e2344eb63aa4 1`


## Evaluating

To evaluate a hash or a link, use the following format:

*OP_FALSE OP_RETURN eval [hash] [evaluation]*

Default relations:
* 0 - false
* 1 - true

The user can change evaluation by pushing another evaluation. Only the last evaluation should count as real.

### Examples

`OP_FALSE OP_RETURN eval 0x6d85bc0dd47219b5e674459d8fd392b672752474a6204a20fa85c27ab8389f80 0`
`OP_FALSE OP_RETURN eval 0x251622657b440e90a92dda4411d73117f3b279ab42529d43e8d69cc2cf7fc5c1 1`
