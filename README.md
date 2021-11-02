# Text-Game-Maker
Basic application to allow users to create, play, save and share text based adventure games

Node Types~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Choice nodes that lead to their children/choices.
Stat check nodes that check player class stat fields against a specified number and direct to the appropriate outcome (e.g. if stat<5 do this otherwise do that)(e.g. if health less than 5 then fail game, if health greater than 5 set health to health-5(via stat edit node), this example is for receiving damage). Must have PC creation and character type nodes preceding it in the tree somewhere.
Stat edit nodes that edit the player class stat fields, such as raising health if healed or raising matter if you get a sword. Has field for what to change in player class and field for what value to change it to(e.g. +3 or -1). Must have PC creation and character type nodes preceding it in the tree somewhere.
End state nodes for success or failures, all paths from all nodes must lead to one.
PC creation/Root node, must have 3 children which are character type nodes(e.g. pick wizard{matter-3, mind-6} or fighter{matter-6, mind-3} or etc.). Must be Root node.
Character type node has a name field, a matter field, a mind field, a spirit field and total and remaining health fields. Also has string field for summary. Matter, mind, spirit and health are stats for the stat check node (e.g. Wizard: matter-3, mind-6, spirit-4, health-5/5). When a character type node is picked it sets the player class fields to match it's fields and then points to it's child. The child can be a start scenario dependant on what character type was picked or can be the same start that's pointed to by all character type nodes. Must have PC creation node as parent.
Node interface: String summary field, full string field, Node type field, parent field, children fields


Player Class~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Holds the current stat layout that was originally set by the character type node


Save/Load Function~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Have the node classes have fields for children and parents, (e.g. child1, child2, child3, parent)
When saving save all info for a node into an ordered list then onto a text file. Specify which node is the root.
Also save the 3 PC instances for the game being saved.
Use the ordered data in the text file to recreate each node when a load occurs (e.g [Name, string, child1/2/3, parent, type, etc.] Use that to make a new node)
Then starting from the specified root each node will point to its children and parent and thus you can travel from the root to any node by either going up each parent to the root or down the correct path of children.
