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
* Responsive Image (srcset)
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

**Structure:**

* Each NodeType is composed out of Mixin parts. For the Paragraph these are:
  * `WebExcess.BaseTypes:Content` defines the NodeType as a Content-Element
  * `WebExcess.BaseTypes:Paragraph.ui` makes the NodeType an needed Inspector Groups visible
  * `WebExcess.BaseTypes:Paragraph.properties.paragraphText--inplace` enables the Property paragraphText with inplace settings
* Each Property is available in three modes:
  * `WebExcess.BaseTypes:Paragraph.properties.paragraphText` the basic property settings
  * `WebExcess.BaseTypes:Paragraph.properties.paragraphText--inspector` .. including the inspector settings
  * `WebExcess.BaseTypes:Paragraph.properties.paragraphText--inplace` .. including the inplace settings

**Hint:**

* Import your initial content with `./flow site:import --package-key WebExcess.BaseTypes`

## Usage / Extending

BaseTypes is replacing and extending existing [Neos NodeTypes](https://github.com/neos/neos-nodetypes) and enables you to easily build and extend your own custom NodeTypes.

**Example:**

Create in your Theme Package a Teaser-NodeType which includes an image, an inplace editable heading and text..

_NodeTypes.Teaser.yaml_

	'WebExcess.Theme:Teaser':
		superTypes:
			'WebExcess.BaseTypes:Content': true
			'WebExcess.BaseTypes:Heading.ui': true
			'WebExcess.BaseTypes:Heading.properties.headingText--inplace': true
			'WebExcess.BaseTypes:Heading.properties.headingTagName--inspector': true
			'WebExcess.BaseTypes:Paragraph.ui': true
			'WebExcess.BaseTypes:Paragraph.properties.paragraphText--inplace': true
			'WebExcess.BaseTypes:Image.ui': true
			'WebExcess.BaseTypes:Image.properties.imageAsset--inspector': true
			'WebExcess.BaseTypes:Button.properties.buttonUrl--inspector': true
			'WebExcess.BaseTypes:Button.properties.buttonStyle': true
		ui:
			label: 'Teaser'
			icon: icon-file-text-o

_NodeTypes.Teaser.fusion_

	prototype(WebExcess.Theme:Teaser) >
	prototype(WebExcess.Theme:Teaser) < prototype(WebExcess.BaseTypes:Image) {
		content = Neos.Fusion:Array {
			heading = WebExcess.BaseTypes:HeadingObject
			heading.@position = 'after image'
			
			text = WebExcess.BaseTypes:ParagraphObject
			text.@position = 'after heading'
		}
	}

That's all


## Think about

1. "Copy-paste is much better than DRY in a lot of cases...
   Bad abstraction is much worse than no abstraction."
   [Dmitri Pisarev](https://twitter.com/dimaip/status/768738351465758720)
2. "Any problem in computer science can be solved with another layer of indirection.
   But that usually will create another problem."
   [David Wheeler](https://de.wikipedia.org/wiki/David_Wheeler)


by [webexcess GmbH](https://webexcess.ch/)
