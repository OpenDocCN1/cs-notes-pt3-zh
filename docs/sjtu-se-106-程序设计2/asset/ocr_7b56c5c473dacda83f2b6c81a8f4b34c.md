# The familytree.h Interface

```
/*
 * Constructor: PersonNode
 * Usage: PersonNode *person = new PersonNode(name);
 * ------------------------------------------------
 * This function constructs a new PersonNode with the specified
 * name. The newly constructed entry has no children, but clients
 * can add children by calling the addChild method.
 */
PersonNode(std::string name);

/*
 * Method: getName
 * Usage: string name = person->getName();
 * ------------------------------------------------
 * Returns the name of the person.
 */
std::string getName();

/*
 * Method: addChild
 * Usage: person->addChild(child);
 * ------------------------------------------------
 * Adds child to the end of the list of children for person, and
 * makes person the parent of child.
 */
void addChild(PersonNode *child);
```