---
title: "SPEC 3 — Accessible Images: Writing Alt-Text for Open-Source-Software"
date: 2022-01-19
draft: true
author:
  - "Mars Lee <mlee@quansight.com>"
  - "Isabela Presedo-Floyd <ipresedo@quansight.com>"
discussion: https://discuss.scientific-python.org/t/discussion-accessible-open-source-projects/63
endorsed-by:
---
# High Level Overview


## How to use this document
This SPEC is divided into two sections: a high-level overview and a reference section.


The high level overview is divided into:
* Motivations and Barriers
* Scope
* Description of deliverables
* Implementation


The [reference section](https://accessibility.scientific-python.org/) is similar to an API reference. Look at the Table of Contents to see if any section pertains to your project or current needs. 


The reference sections is divided into:
* Best practices, main principles and style guide
* Guidelines for writing alt-text by image type (graphs, logos, gifs, etc)
* Guidelines by context (main website, documentation, blog posts, etc)
* Project-specific needs  
* Frequently-Asked-Questions


## Motivations and Barriers
### Summary of Motivations and Barriers
* Accessibility is about making technology accessible to the full range of human experience, which includes disabilities.
* General reasons why open-source software should be more accessible:
   * accessibility benefits everyone
   * access to information and technology as human right
   * enjoyment and creation for disabled people
* Reasons very specific to open-source software:
   * achieve the ethos of open-source
   * solving root problems due to open-source’s scale
   * better represent needs of disabled users
* Open-source software is currently not very accessible due to:
   * decentralized structure
   * uncertainty in implementation
   * different accessibility needs of open-source software
   * under-representation of disabled users
   * insufficient funding 


Accessibility is about making the world accessible to the full range of human experience, which includes disabilities. For example, the physical world can be made more accessible for wheelchair users by having more buildings with ramps. Not only should the physical world be accessible, but the digital world as well.


More and more people are accessing the world digitally. Access to the internet is a human right. [citation for UN]. With access to the internet, people can access vital information, such as education [citation for various country laws to access education] or their banking information.


People with disabilities access the internet as well. Blind users can access text on websites with assistive technology such as a screen-reader, which verbally reads text out loud. Thus assistive technology empower disabled people to live autonomous lives.


An accessible world allows people with disabilities to not only access information, but also communicate and create. Helen Keller’s access to Braille, another form of assistive technology, allowed her to read about the world. She used Braille to communicate with others who were Deaf-Blind. It also allowed her to publish her experiences [citation for Story of My Life] and advocate for the Deaf-Blind community to the general public.


Accessibility benefits everyone. For example, captions for videos benefit not only Deaf viewers with complete hearing loss, but also viewers with partial hearing loss due to age. Captions also benefit viewers who cannot play audio out loud, such as in a quiet environment or if they have broken speakers. [citation to range of disabilities and situational disability]. Thus accessibility benefits not just “a few disabled people”[a] but all people.


These are general reasons why open-source software should be more accessible. However, there are reasons very specific to open-source software as well.


Open-source software should be more accessible to better achieve the aims and ethos of open-source. Open source prides itself as available to all, due to its XYZ license [citation]. Money and licensing should not be a barrier to creating art for self-expression [GIMP vs Photoshop] or creating mathematical graphs for research [matplotlib vs MatLab]. However, available does not necessarily mean accessible.


A project’s community meetings available for all contributors to attend, but inaccessible to some due to time-zone differences. For example, a community meeting held at UTC XYZ. For a contributor in New York City, this meeting would be easily accessible at their local time of 3pm. For a contributor in New Delhi, India, this meeting would be inaccessible at their local time of 1am. In turn, to make their meetings more accessible, some projects alternate their meeting times [citation, NumPy alternate IST-friendly meeting].


In a similar way, disabled developers may not be able to access documentation or navigate the user interface of open-source software. For a visually-disabled developer, an image can still be accessed via screen-reader. The screen-reader reads out-loud the image’s ‘alt-text’, which is a short description of the image. Images in documentation are valuable sources of information. However, images without ‘alt-text’ cannot be accessed this way, and the developer loses valuable information.


For open-source software that uses a graphical interface, a mouse can be used to interact with the elements in the interface, such as clicking a cell or hovering over a button. A developer with motor-disabilities may interact via keyboard instead. The developer can navigate across elements via the Tab key and select to interact with the Enter key. A user interface that is not keyboard-navigable cannot be accessed at all for the developer.


If a developer cannot access open-source software, they are much less likely to join open-source spaces. Contribution and community engagement is the lifeblood of open-source development. Inaccessible open-source software is less diverse, and diverse contributions make open-source stronger [citation].


Thus, to truly make open-source available to all, it needs to be accessible as well.


Accessible open-source affects not only disabled developers, but disabled users as well.


Open-source software should be more accessible due to a matter of scale. Open-source is foundational to modern digital infrastructure [citation… that xkcd comic?]. Problems at the foundational level are magnified at scale, and thus inaccessible open-source projects affect millions of users across the world [citation of chapter in book ‘The Making and Maintenance of Open Source Software’]. 


For example, the open-source software CodeMirror is used as part of the Firefox’s Developer Tools [citation]. CodeMirror provides a code editor in the browser. However, Codemirror 5 and its previous versions were inaccessible to keyboard and screen-reader users. It did not support the use of the Tab key as a navigational input. Instead, the Tab key could only be used for code indentation.


As Firefox is used by millions of users every month [citation on usage], millions of people have inherited this inaccessibility. Thus at scale, many users could not access Firefox’s Developer Tools. It was only years later with the release of Codemirror 6 that an option was provided to use the Tab key as navigational input as well. Rather than having projects built on top of open-source software inherit problems or create their individual patches, open-source projects have the power to solve accessibility problems across the board.


### Barriers
The current state of open-source software is not very accessible, for a variety of reasons.


Open-source software is currently not very accessible due to its decentralized nature. Being decentralized is both open-source software’s greatest strength and weakness. It allows anyone to contribute, and different contributors contribute different things. However, this can also make it difficult to create a cohesive alternative experience for a screen-reader user, keyboard user and more. If an accessibility is not evenly applied, a user journey can be disrupted, such as with a keyboard trap [citation]. Thus to make open-source software more accessible, it must be done deliberately, in stages and in coordination with others[b].


Open-source software is currently not very accessible due to uncertainty in implementing accessibility. The vast majority of contributors in open-source software are software developers [citation on percentage]. While developers may feel comfortable contributing code, they may feel less comfortable contributing outside of the usual wheelhouse, such as accessibility. While there is growing awareness about accessibility in open-source [citation], contributors may still hold back due to a fear of ‘doing it wrong’. By providing guidelines in this document, we hope that this uncertainty can be overcome.


Open-source software is currently not very accessible due to the different accessibility needs of open-source software. Current accessibility guidelines are for general use and focused primarily on web-pages [citation, WCAG]. There are guidelines specific for certain sectors, such as education and the creation of accessible tests for disabled students [citation, Diagram Center and USA education]. However, these guidelines are not suited for open-source’s technical demands and processes. There are much less resources on how to make a command-line interface accessible, best practices in writing accessible documentation or community meeting notes. This document aims to provide guidelines specific for open-source software.


Open-source software is currently not very accessible due to the under-representation of disabled people in open-source spaces. While disabled people make up X [citation of disabled people in general population], in open source the number is Y [citation]. The above cited barriers prevent disabled people from using open-source software and reporting problems with their experiences, such as with Github Issues. These barriers also prevent disabled developers from contributing back. If disabled people are kept out of a space, then disabled people’s voices are not heard within that same space. It creates a chicken-and-egg problem where open-source software is not made with disabled users in mind and in turn disabled users cannot help shape open-source.


Open-source software is currently not very accessible due to insufficient funding for accessibility. Open-source software relies not only on volunteer labor of contributors, but also paid labor through grants [citation]. Grants allow proposed features to be prioritized and created in a sustainable way.  However, out of X dollars spent on funding open-source software, only Y percent, Z dollars is spent on accessibility [citation]. This is related to the above mentioned problem of under-representation. In a grant proposal,it can be difficult to justify funds for making open-source accessible without proof of demand such as with a high number of Github issues about accessibility [citation of grant-proposal process[c]]. Thus this lack of funding perpetuates another cycle where accessibility is not financially supported.


### Overcoming Barriers Together


Open-source software can begin to be more accessible by coordinating with each other. Within the scientific Python ecosystem, there is one such effort: the Scientific Python Ecosystem Coordination (SPEC).


The SPEC process is designed to identify areas of shared concern between projects in the scientific Python ecosystem and to produce collaboratively written, community adopted guidelines for addressing these areas. Such guidelines are known as ‘SPEC documents’ or a ‘SPEC’.


Projects in the ecosystem have an existing, diverse set of proposal processes and development constraints. SPECs complement these: they are a mechanism to encourage shared practices and improve uniformity of experience across projects. This SPEC captures established practices so that new projects can learn from them. As SPECs are living documents, authors may propose a new practice that they believe will benefit the ecosystem as a whole.


Projects decide for themselves whether to adopt any given SPEC—often, this would be through team consensus. A SPEC may not be a good fit for every single project, and thus there is no expectation that all SPECs must be adopted by all projects. That said, SPECs serve their purpose through being adopted by several projects—and their authority stems from the extent to which they are. [citation, SPEC Processes page]


The purpose of this SPEC document is to:
- Make the ecosystem more accessible
- Clarify the broad term accessibility and its various possible implementations
- Provide specific assessment tools and steps
- Direct to existing accessibility standards and modifications for open source specifically
- Provide case studies of how different core projects became more accessible
- Start discussion and develop shared solutions


## Scope
### Summary of Scope
* This SPEC's scope is on making visual media accessible to people with screen-readers.
* This can be done with the implementation of ‘alt-text’ in images.


 'Accessible' is a very broad term, so is ‘accessible open-source’. Open-source projects can be more accessible to people with visual, auditory, physical, speech, and neurological disorders. Disabilities can be permanent, temporary or situational [citation to WCAG page on Diverse Abilities and Barriers)](https://www.w3.org/WAI/people-use-web/abilities-barriers/]. 


This SPEC's scope is on making visual media accessible to people with visual disabilities who use screen-readers. Visual media can be made accessible through the implementation of ‘alternative-text’ (alt-text).


People with visual disabilities include not only people who are blind with complete vision loss, but also people with partial vision loss, blurry vision, low-contrast vision and color-blindness. Some specific visual disabilities include myopia, cataracts and red-green color-blindess.


Some people with visual disabilities use assistive technology such as screen-readers to use the computer, navigate websites and use programs. Screen-readers ‘read out’ text and are used with keyboard commands to do a variety of actions. This is possible because how people with and without visual disabilities navigate web-pages is fundamentally the same. A web-page is built from elements such as headers, text, images and links. A user can navigate between these elements with a mouse, keyboard, screen-reader and more.


Screen-readers can preview and skip information by jumping between page headers, which is similar to visually skimming text. Screen-readers can also read out images with alt-text.


Alt-text is a short summary of an image. When screen-readers can read out images with alt-text, the user can still experience the image and access the valuable information images provide.


Images without alt-text are inaccessible to people using screen-readers. Valuable information is lost. For example, an tourism website may provide an image of a map showing the nearest exits in a museum. If no alt-text is provided, a user with a screen-reader misses this information. An alt-text of ‘A map of the museum. The nearest exits are to the left of the dinosaur exhibit.’ makes this information accessible and allows the user to navigate a physical space with independence.


Alt-text is rendered on web-pages as the HTML alt attribute [citation to MDN]. When uploading images online, the creator can attach alt-text to an image.


There are many excellent resources available for writing alt-text, such as the Web Content Accessibility Guidelines (WCAG). However, there are many concerns specific to scientific Python open-source projects that WCAG does not adequately address. Therefore this SPEC aims to provide guidelines for writing alt-text for scientific Python open-source projects..


There are other worthwhile concerns about how open-source can be more accessible, such as creating CI tests that check if alt-text is included in a contribution with images. However, the implementation of that is beyond the scope of this SPEC. These are worthwhile topics for future SPECs.

## Description of deliverables
The desired outcomes from the adoption of this SPEC is:
* Accessible images with alt-text within various contexts in open-source software:
   * Main website
   * Documentation
   * Blog posts
   * Videos
   * Community Meeting Notes
   * and more


On a broader level, this SPEC also aims to create a cultural shift where people with disabilities feel welcome in open-source spaces. By removing these barriers, people with disabilities can use open-source software and disabled developers can contribute back. Thus open-source can better serve the needs of its disables users and in turn disabled people can shape open-source.

## Implementation
Implementing alt-text for images used in open-source software can seem like a big task. There are probably many existing images without alt-text. In the same way projects can have technical debt, there may also be ‘accessibility debt’ to cover. Accessibility may not be part of the contribution review process, such as requesting alt-text in submissions or in CI tests. There are many options for auditing: manual and automated. This auditing can be done internally by contributors or commissioned to an external auditing company.

However, implementing alt-text can be done: if done deliberately, in stages and in coordination with others.

This section aims to highlight case studies where projects have implemented this SPEC’s guidelines, their unique challenges, solutions and outcomes.

The SPEC process is primarily aimed at ‘SPEC Core Projects’. The Core Projects are a small subset of the Scientific Python ecosystem consisting of mature, community developed projects that are (a) depended upon by most of the other projects and (b) responsible for reviewing, discussing, implementing, and endorsing SPEC documents. The full list of Core Projects can be found at the [SPEC Core Projects page](https://scientific-python.org/specs/core-projects/). 

The SPEC process is primarily aimed at ‘SPEC Core Projects’ due their foundational nature. Rather than having projects built on top of open-source software inherit problems or create their individual patches, SPEC Core Projects have the power to solve accessibility problems across the board.

However, projects that are not SPEC Core Projects are certainly welcome to learn from and adopt this document. We invite discussion of any project’s needs and questions in this [SPEC’s forum](https://discuss.scientific-python.org/t/discussion-accessible-open-source-projects/63). 

Any project is invited to use the Reference section in writing alt-text. The Reference section aims to be a centralized resource for writing alt-text specific for open-source software’s needs.

### Core Project Endorsement
In the SPEC process, a SPEC document has three main stages: accept, endorse and adopt.

The authors of this SPEC are contributors in the SPEC Core Projects. They have also made several contributions specific to accessibility and alt-text. In their discussions with other contributors, they have seen several recurring questions worth documenting. They have also developed guidelines specific for open-source processes that are not answered by general alt-text guidelines. Therefore they have written this SPEC to share this knowledge and open this discussion with others.

The accept decision of the SPEC process is made by the SPEC Steering Committee. The Steering Committee represent the interests of the Core Projects and is composed partially of individuals who are active Core Project contributors. The full description and list of members can be found in the [SPEC Steering Committee page](https://scientific-python.org/specs/steering-committee/)

The endorse decision is made by the Core Projects. The Core Projects and interested community members revise the accepted SPEC in a collaborative and iterative process focused on ensuring the SPEC implementation plan that is broadly applicable and likely to be widely adopted.

The following Core Projects endorse this SPEC.
#### NumPy
#### (Second Core Project)
#### JupyterLab

### Ecosystem Adoption
The final stage in the SPEC process is adoption.

The adopt decision is made by individual projects according to their own decision-making processes. Any project in the ecosystem is welcome to adopt a SPEC at any point. However, it may make sense to wait until a SPEC is endorsed by several Core Projects

Core Projects interested in formally adopting this SPEC can follow the [SPEC Purpose and Process page](https://scientific-python.org/specs/purpose-and-process/).

Formally adopting this SPEC has several advantages. It provides a space to ask questions, provide shared solutions and prevent ‘re-inventing the wheel’. It signals a project’s recognition and investment of accessibility as a core tenant of open-source software. It prepares Scientific Python for the next decade of scientific discovery and user growth.

The following Core Projects have adopted this SPEC. Each section highlights how a project has  implemented this SPEC’s guidelines, their unique challenges, solutions and outcomes.
#### NumPy
#### (Second Core Project)
#### JupyterLab


## Closing
Accessibility comes in various forms beyond alt-text. The authors of this SPEC hope this document answers questions, coordinates across projects, inspires action and the development of future SPECs focused on accessibility. 

This is the end of the high-level overview. The next section is the reference section.


The [reference section](https://accessibility.scientific-python.org/) is similar to an API reference. Look at the Table of Contents to see if any section pertains to your project or current needs. 


The reference sections of this document is divided into:
* Best practices, main principles and style guide
* Guidelines for writing alt-text by image type (graphs, logos, gifs, etc)
* Guidelines by context (main website, documentation, blog posts, etc)
* Project-specific needs  
* Frequently-Asked-Questions

## Notes

# Reference Section

## How to use this document
This SPEC is divided into two sections: a high-level overview and a reference section.


The high level overview is divided into:
* Motivations and Barriers
* Scope
* Description of deliverables
* Implementation


The [reference section](https://accessibility.scientific-python.org/) is similar to an API reference. Look at the Table of Contents to see if any section pertains to your project or current needs. 


The reference sections of this document is divided into:
* Best practices, main principles and style guide
* Guidelines for writing alt-text by image type (graphs, logos, gifs, etc)
* Guidelines by context (main website, documentation, blog posts, etc)
* Project-specific needs  
* Frequently-Asked-Questions

## Main Principles

### Transformable
Understanding the goals behind why we write alt text can be helpful in figuring out how to write appropriate descriptions and to navigate other recommendations in this document.


On the most foundational level, alt text needs to be:
- Transformable
- Complete
- Contextual
- Formatted properly


### Complete
Just as not all images are the same, not all alt text is the same. What types of alt text makes sense for an image depends on the images' content and context.


In terms of content, images can be
- Decorative (does not add meaningful content)
- Functional (adds content with a use, often interactive)
- Informative (adds or illustrates content)
- Complex (adds a large amount of content)


For guidance on determining an image's role as content and writing appropriate alt text, refer to the [W3's alt decision tree](https://www.w3.org/WAI/tutorials/images/decision-tree/).


In terms of context, alt text needs to fit into the content that surrounds it. It can be helpful to ask questions like the following to determine what information needs to be prioritized when describing that image:


* Is the image demonstrating something described in the text preceding it?
* Is the image adding content that hasn't been mentioned previously?
* Does the image have a caption?
* Does the image match one used elsewhere in the same media?
* What information do I need from this image to understand the media as a whole? What information do I not need?

### Contextual
Just as not all images are the same, not all alt-text is the same. What types of alt-text makes sense for an image depends on the images' content and context.

In terms of content, images can be
- Decorative (does not add meaningful content)
- Functional (adds content with a use, often interactive)
- Informative (adds or illustrates content)
- Complex (adds a large amount of content)

For guidance on determining an image's role as content and writing appropriate alt text, refer to the [W3's alt decision tree](https://www.w3.org/WAI/tutorials/images/decision-tree/).

In terms of context, alt-text needs to fit into the content that surrounds it. It can be helpful to ask questions like the following to determine what information needs to be prioritized when describing that image:
- Is the image demonstrating something described in the text preceding it?
- Is the image adding content that hasn't been mentioned previously?
- Does the image have a caption?
- Does the image match one used elsewhere in the same media?
- What information do I need from this image to understand the media as a whole? What information do I not need?
- 
### Formatted Properly
Having an image description won't help if it's formatted in a way that someone can't access it or doesn't know how to find it. There are a few standard methods for web content that are reliable.

#### Alt text
Alt text is the most frequently used style of image descriptions. 

This is the best place to start for describing images or similar visualization content. It derives its name from the HTML `alt` element used to modify images. Because of its prominence, many resources on proper image descriptions may use the term alt text to describe best practices that could benefit other image descriptions as well.

For web-based content, this is the default. All images need alt text even if they employ additional descriptions.

For more information on the `alt` element, refer to [MDN’s alt documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/alt).

For examples of this in use, refer to [list of links to image types or content later in the document] [Logos](), [Images of People](), [Images of Interfaces]().

#### Linking to long content
Linking to long or detailed descriptions is an additional method best suited for complex, info-heavy, or text-heavy images where descriptions must exceed the recommended length for alt text. Linking should not be used in place of alt text, only to supplement it.

Practices for linking to long content may vary based on project. Some examples include:
- Having a webpage that contains all the long descriptions used throughout that website in one place.
- Having a end-of-page list of long descriptions below the images they describe, similar to endnotes.
- Creating a Gist for each image and linking each image to that (not recommended because it relies on a single GitHub user account, but may be a good stopgap until a more permanent solution can be set in place).

For examples of this in use, refer to [list of links to image types or content later in the document] [Sequential Images]() or [Diagrams]().

##### A note on `longdesc`

`longdesc` is a deprecated HTML element meant to provide long descriptions for images. It may still appear in other recommendations, but because there is no longer browser support for it it should not be used. 

The common practice is now to link to long descriptions (more in the prior section).

For more information on the `longdesc` element, refer to [MDN’s longdesc documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/longDesc).
#### Empty attribute

For decorative images, meaning they either aren’t needed to understand content or are represented in full elsewhere, use an empty `alt` element. Having the `alt` element is still necessary.

The only way to know if an image is decorative is based on the context it is used in.

For more information on decorative images, refer to []().

For examples of this in use, refer to [list of links to image types or content later in the document] []().
#### Captions

Captions and image descriptions are not the same, and if both are used they should support one another. Captions do this thing alt text does another

For more information on captions, refer to []().

For examples of this in use, refer to [list of links to image types or content later in the document] []().
#### ARIA Label

{acronym}, ARIA, is an additive accessibility tool for web content. 

ARIA is powerful and often needed, but proper HTML is the preferred method whenever possible. Please don’t use ARIA labels without first ensuring that proper HTML tags cannot suffice.

For more information on ARIA, refer to [](). 

For examples of this in use, refer to [list of links to image types or content later in the document] [Variable visuals]().

## Style Guide
Consistently formatting alt text helps its readability whether or not it is read by assistive technology.

These guidelines supplement the writing style guides a project may already have present, especially in documentation. Defer to a project's style guide before these guidelines.
### Basics

Here are some simple alt text guidelines to start with:

- Avoid beginning descriptions with "an image of" or similar phrases. That is already represented by proper HTML.
- Check your spelling. You can always write alt text somewhere with spellcheck and transfer it to your main workspace.
- Write with [plain language](https://www.plainlanguage.gov/guidelines/)
- Acronyms are the only things that need - all-caps.
- Text in an image needs to be written as text somewhere else. If it is short, it can be in the alt text.

### Punctuation
Write alt text as complete sentences. This means it needs to include a complete thought that can be understood on its own.

Just like other complete sentences, alt text needs punctuation. Appropriate commas and periods are the most important to include for alt text.

### Capitalization
Alt text uses [sentence case](https://en.wikipedia.org/wiki/Letter_case#Sentence_case).

### Character count
These guidelines do not limit alt text to a specific character count even though some other guidelines do.

It is still important to know that alt text should be as brief and direct as possible. If a short sentence or three does not cover all the information, refer to the links in [Main Principles: Formatted Properly]() for different types and methods of describing images.

### Color and directional words
Alt text can be used by people who are anywhere on the spectrum from blind to sighted. Colors and directions (like left or right) are visual-rooted descriptions. While they can be used, do so only when relevant to the context of the image.

Consider if
- The image is using colors with meaning, like color-coding
- The placement of an element contributes to its relationship to other elements (like in documentation, when a screen shot shows where to find a button or menu)
- The colors or directions matter in the scope of the content as a whole (for example, if they are referenced elsewhere)

## Per-Project Guidelines

## Reference
### By Image Type
For reference, the following section has a list of common image types with a guideline and examples for each. These are designed to follow the above principles while providing help with specific applications.

This list is not exhaustive. If you can’t find an image type you are looking for or don’t think the guideline fits your case, refer to the Main Principles section and ensure your solution meets those needs.
- Graphs
- Diagrams 
- Things with people 
- Interactive visuals
- Varying visuals
- Autogenerated visuals
- Logos
- Screenshots
- Image of interfaces
- Gifs

#### Graphs
There are a key principles that apply across all graphs:
- Identify the graph type
- Describe the axis
- Describe the general shape
- Describe any characteristics
- Describe the general changes or pattern

##### Bar Charts
Using the key principles, we can write alt-text for bar charts…

### Images with people
Like all other alt text, context is key to deciding what to write. Writing about people, especially in cases where the people in the photo aren't known, takes care.

The most general guideline is to avoid making assumptions about the people in the photos. Make choices based information in the surrounding content or an external source if relevant.

If the people in a photo are known and it is relevant to the content, put their name in the alt text. Other descriptions aren't usually necessary once the name is used.

It is also best to
* Use gender-neutral language (unless a subject's gender is known)
* Avoid describing physical features unless it is necessary for supporting the content
* Use general terms for a group of people rather than describing each individual

### By Context

#### Main site
Mostly less info dense images. Logo. Some complex images. Maybe people.
#### Documentation site
Info dense images. Diagrams. Charts. Screenshots. Images of interfaces. Images of text.
#### Community Meeting Notes
‘informal ‘ documentation, still valuable
Images of text. Screenshots. Images of interfaces.
#### Blog posts
Blog posts are self-contained, so no matter the type of images aim for consitency and ensuring that no info is missing by breaking your own links.

## Notes
