# File And Directory Rules

Naming files and directories is CamelCase, except for the names of the files and directories that have the component type of react that is Pascal Case.

Note: Filenames like HOCs also use the general rule and are CamelCase

The style files for a mapped component are also CamelCase

# Types of Rssr Directories

**Entity**  : Holds an entity such as Home within the App

**Wrap** : There are directories that do not have their own entities, but hold a number of entities inside that have a number of features in common or we treat them in some way (sometimes to enhance code readability).

☑ The main difference between the two : Entity has a file with exactly the same directory inside it but Wraps are not like that. In essence, Entities are trees, but Wraps are graphs.

## Specific mode Directories

In some projects (usually the largeScale project) the above directories work, but in the largeScale projects a number of exceptions may occur as follows :

1. *__style*

2. *__action*

3. *__component*

☑ The first two underscores the exceptions and the distinct ones, the second one is higher in the file structure than the rest of the files.

**__style** : We have a series of components for the component that would normally be written by Camel Case and the component name and imported directly into the JavaScript file itself.But at times we may have some common styles among the components of a directory we use at this time.

**__action** : This part is used like style only here are the actions we need to write.

Elsewhere we do this when there is a very large action that if this is the case, the desired folder will be created at the heart of the component itself.

**__component** : The component behaves like style in that the shared components are placed inside a container.

## **Expansion of Entity**

Every entity inside the App, Component and Partial must have a directory

- exception: App.js file inside App folder

Any entity that has more than one file must be defined as an entity directory.

- exception: Css and Js files

Any files and entities that have a specific definition must be written in a wrap directory.

- exception: Modes that fall into the entity directory.
