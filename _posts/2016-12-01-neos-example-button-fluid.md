---
layout: post
section-type: post
title: 'Example Neos Content Elements #1 Fluid Button'
category: tech
tags: [ 'neoscms', 'programming', 'tutorial', 'guide' ]
---

Hey guys, if you want to follow this tutorial make sure to read [this Post]({{site.url}}/tech/2016/12/01/neos-conent-elements.html) before.

What will we do this time? We will create a link-button with fluid for NeosCMS.
If you have any problems, questions, suggestions or anything else don't hesitate to contact me via slack or twitter.

So the button will be pretty straight forward. The button only gets two properties: a text and a link.
The text will be inline-editable and the link will be added via an inspector editor.

So we start with the nodetype.

Create a new file:

```
touch /Packages/Sites/MStruebing.ContentElements/Configuration/NodeTypes.Button.yaml
```

In that file add the following content:

```
Mstruebing.ContentElements:ButtonFluid':
  superTypes:
    'TYPO3.Neos:Content': TRUE
    'TYPO3.Neos.NodeTypes:LinkMixin': TRUE
  ui:
    label: 'Button-Fluid'
    icon: 'icon-object-group'
    inspector:
      groups:
        link:
          label: Link
  properties:
    buttonText:
      type: string
      ui:
        inlineEditable: TRUE
        aloha:
          placeholder: 'Enter button text here ...'
    link:
      ui:
        inspector:
          group: link

```

What is this stuff doing?
The first line is just an identifier.  
The supertypes are types from which this content element inherits.  
So this one inherits from `TYPO3.Neos:Content` - it is content right? And from `TYPO3.Neos.NodeTypes:LinkMixin`  
We can go to `/Packages/Application/TYPO3.Neos.NodeTypes/Configuration` and watch the content of the`NodeTypes.Mixins.yaml`.
There we can see that this is an abstract nodetype which is similar to the oop world. That means that no instance can be created of this but it can be used to inherit from it to get default settings for example. We can see that the default settings are mostly self-explanatory. The interesting one here is the editor. This is an editor which is displayed in the right-sidebar. There are some others to but this one is for links, so we don't have to implement one by ourself or define one in our nodetype, because we are inherit from this one. We firstly define an label and icon which is displayed in the 'create new' dialog. Then we define a inspector group called link with the label Link to structure our inspector :). We set two properties buttonText and link, this are also the names which can be accessed via fluid, nothing more is needed for that. So buttonText is of type string and it is an inlineEditable element aloha, which is the current inline editor of neos gets an placeholder.
The link property is only assigned to an inspector group, all other settings are available by he LinkMixin already.

Create a new fluid template

```
touch Packages/Sites/MStruebing.ContentElements/Resources/Private/Templates/NodeTypes/ButtonFluid.html
```

And adjust the content like this:

```
{namespace neos=TYPO3\Neos\ViewHelpers}

<f:if condition="{neos:rendering.inBackend()}">
    <f:then>
        <span class="btn">
            {neos:contentElement.editable(property: 'buttonText', tag: 'span')}
        </span>
    </f:then>
    <f:else>
        <a href="{link}" target="blank" class="btn">
            {buttonText->f:format.raw()}
        </a>
    </f:else>
</f:if>
```

At first we define a namespace neos and set it to the neos viewhelpers. You can see which are available in `Packages/Application/TYPO3.Neos/Classes/TYPO3/Neos/ViewHelpers/`.
The if condition evaluates to true if the page is rendered in the backend like the name already suggests.
The `{neos:contentElement.editable(property: 'buttonText', tag: 'span')}` says that the buttonText is an inline editable property and the surrounding element - in which the magic happens that it can be inline edited - should be a span.  
And that is basically all we have to do.   
To prettify the output we can got to `Packages/Sites/MStruebing.ContentElements/Resources/Public/Styles/Main.css` and add the following small css snippet:

```
.btn {
    display: inline-block;
    background-color: LawnGreen;
    padding: 20px;
}
```

You can take [this commit](https://github.com/mstruebing/neos-content-elements/commit/872822dcda0086ffbdbfd7226b816298eeed8c3f) as an reference to this guide
