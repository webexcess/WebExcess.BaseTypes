# WebExcess.BaseTypes

Basic NodeTypes for [Neos CMS](https://www.neos.io/).


## Installation

    composer require webexcess/basetypes


## Compatibility and Maintenance

| Neos Version | Package Version | Maintained |
|--------------|-----------------|------------|
| 3.x          | 1.x             | YES        |
| 2.3 LTS      | 0.x             | NO         |


## Ready to use


### Content NodeTypes

* Heading
* Paragraph
* Image (incl. srcset)
* SVG-Image
* Button
* Responsive Iframe
* Grid (two-, three- and four-column)


### Document NodeTypes

* Home
* Page

**Rules:**

* Each first code-line of a file contains a comment with the respective css class, e.g. `# basetype-paragraph`
* Properties are always namespaced with the BaseType Name, e.g. `paragraphText` - not only `text`

**Hint:**

* Import your initial content with `./flow site:import --package-key WebExcess.BaseTypes`


## Usage / Extending

BaseTypes is replacing and extending existing [Neos NodeTypes](https://github.com/neos/neos-nodetypes) and enables you to easily build and extend your own custom NodeTypes.

**Example:**

	'WebExcess.Theme:Home':
		superTypes:
			'WebExcess.BaseTypes:Document': true
			'WebExcess.BaseTypes:Heading.properties.headingText--inplace': true
		ui:
			label: 'Home'


## Think about

1. "Copy-paste is much better than DRY in a lot of cases...
   Bad abstraction is much worse than no abstraction."
   [Dmitri Pisarev](https://twitter.com/dimaip/status/768738351465758720)
2. "Any problem in computer science can be solved with another layer of indirection.
   But that usually will create another problem."
   [David Wheeler](https://de.wikipedia.org/wiki/David_Wheeler)


by [webexcess GmbH](https://webexcess.ch/)
