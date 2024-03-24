---
layout: post
title: REST API Design Methodology
description: >

---

# REST APIs Design Methodology

The REST architectural style is commonly applied to the design of APIs for modern web services.
A Web API conforming to the REST architectural style is a REST API. Having a REST API makes a web service “RESTful.” 
A REST API consists of an assembly of interlinked resources. This set of resources is known as the REST API’s resource model.

Well-designed REST APIs can attract client developers to use web services. In today’s open market where rival web services are competing for attention, an aesthetically pleasing REST API design is a must-have feature.

## REST API Design

For many of us, designing a REST API can sometimes feel more like an art than a science.
Some best practices for REST API design are implicit in the HTTP standard, while other
pseudo-standard approaches have emerged over the past few years. Yet today, we must
continue to seek out answers to a slew of questions, such as:

- When should URL path segments be named with plural nouns?
- Which request method should be used to update resource state?
- How do I map non-CRUD operations to my URIs?
- What is the appropriate HTTP response status code for a given scenario?
- How can I manage the versions of a resource's state representations?
- How should I structure a hyperlink in JSON?

A conceptual framework called the Web Resource Modeling Language (WRML) to assist with the design and implementation of 
REST APIs.

> Vocabulary review


| Term | Description |
|------|-------------|
|   **Application Programming Interface (API)**    |       Exposes a set of data and functions to facilitate interactions between computer programs.       |
| **Architectural constraint** | Limits the behavior of a system’s components to enforce uniformity and achieve some desired property. |
| **Architectural style** | Roy Fielding used this term to describe a set of constraints that restrict the behavior of a system’s interconnected components |
| **Cache** | REST constraints that enable network-based intermediaries to hold on to resource state representations which helps web servers meet the demands of their clients. |
| **Representational State Transfer (REST)** | Roy Fielding’s derivation of the Web’s architectural style. |
| **Stateless** | A REST constraint that restricts a web server from holding on to any client-specific state information,which helps it support more clients |

## Identifier Design with URIs

### URIs

REST APIs use Uniform Resource Identifiers (URIs) to address resources. On today’s Web, URI designs range from masterpieces that clearly communicate the API’s resource model like:

`http://api.example.restapi.org/france/paris/louvre/leonardo-da-vinci/mona-lisa`

to those that are much harder for people to understand, such as:

`http://api.example.restapi.org/68dd0-a9d3-11e0-9f1c-0800200c9a66`

_Tim Berners-Lee_ included a note about the opacity of URIs in his “Axioms of Web
Architecture” list:

_**The only thing you can use an identifier for is to refer to an object. When you are not dereferencing, you should not look at the contents of the URI string to gain other information.**_

_—Tim Berners-Lee [http://www.w3.org/DesignIssues/Axioms.html](http://www.w3.org/DesignIssues/Axioms.html)_

> Rule: Forward slash separator (`/`) must be used to indicate a hierarchical relationship

The forward slash (/) character is used in the path portion of the URI to indicate a
hierarchical relationship between resources. For example:

`http://api.canvas.restapi.org/shapes/polygons/quadrilaterals/squares`

> Rule: A trailing forward slash (/) should not be included in URIs

As the last character within a URI’s path, a forward slash (/) adds no semantic value
and may cause confusion. REST APIs should not expect a trailing slash and should not
include them in the links that they provide to clients.
Many web components and frameworks will treat the following two URIs equally:

`http://api.canvas.restapi.org/shapes/`

`http://api.canvas.restapi.org/shapes`

> Rule: Hyphens (-) should be used to improve the readability of URIs

To make your URIs easy for people to scan and interpret, use the hyphen (-) character
to improve the readability of names in long path segments. Anywhere you would use
a space or hyphen in English, you should use a hyphen in a URI. For example:

`http://api.example.restapi.org/blogs/mark-masse/entries/this-is-my-first-post`

> Rule: Underscores (_) should not be used in URIs

> Rule: Lowercase letters should be preferred in URI paths

When convenient, lowercase letters are preferred in URI paths since capital letters can
sometimes cause problems. RFC 3986 defines URIs as case-sensitive except for the
scheme and host components. For example:

`http://api.example.restapi.org/my-folder/my-doc`

> Rule: File extensions should not be included in URIs.
> Rule: Consistent subdomain names should be used for your APIs.
The top-level domain and first subdomain names (e.g., soccer.restapi.org) of an API
should identify its service owner. The full domain name of an API should add a subdomain named api. For example:

`http://api.soccer.restapi.org`

> Rule: Consistent subdomain names should be used for your client developer portal

Many REST APIs have an associated website, known as a developer portal, to help onboard new clients with documentation, forums, and self-service provisioning of secure API access keys. If an API provides a developer portal, by convention it should have a subdomain labeled developer. For example:

`http://developer.soccer.restapi.org`

### Resource Modeling

#### Document

A document resource is a singular concept that is akin to an object instance or database
record. A document’s state representation typically includes both fields with values and
links to other related resources. With its fundamental field and link-based structure,
the document type is the conceptual base archetype of the other resource archetypes.

Each URI below identifies a document resource:
`http://api.soccer.restapi.org/leagues/seattle`
`http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet`
`http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet/players/mike`

#### Collection

A collection resource is a server-managed directory of resources. Clients may propose
new resources to be added to a collection. However, it is up to the collection to choose
to create a new resource, or not. A collection resource chooses what it wants to contain
and also decides the URIs of each contained resource.

Each URI below identifies a collection resource:
`http://api.soccer.restapi.org/leagues`
`http://api.soccer.restapi.org/leagues/seattle/teams`
`http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet/players`

#### Store

A store is a client-managed resource repository. A store resource lets an API client put
resources in, get them back out, and decide when to delete them. On their own, stores
do not create new resources; therefore a store never generates new URIs. Instead, each
stored resource has a URI that was chosen by a client when it was initially put into the
store

The example interaction below shows a user (with ID 1234) of a client program using
a fictional Soccer REST API to insert a document resource named `alonso` in his or her
store of favorites:

`PUT /users/1234/favorites/alonso`

#### Controller

A controller resource models a procedural concept. Controller resources are like executable functions, with parameters and return values; inputs and outputs.

Like a traditional web application’s use of HTML forms, a REST API relies on controller
resources to perform application-specific actions that cannot be logically mapped to
one of the standard methods (create, retrieve, update, and delete, also known as
CRUD)

Controller names typically appear as the last segment in a URI path, with no child
resources to follow them in the hierarchy. The example below shows a controller resource that allows a client to resend an alert to a user:

`POST /alerts/245743/resend`

### URI Path Design

Each URI path segment, separated by forward slashes (/), represents a design opportunity. Assigning meaningful values to each path segment helps to clearly communicate the hierarchical structure of a REST API’s resource model design.

```mermaid
{collection-c}/{store-s}/{document-d}
```

> Rule: A singular noun should be used for document names

A URI representing a document resource should be named with a singular noun or
noun phrase path segment

For example, the URI for a single player document would have the singular form:
`http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet/players/claudio`

> Rule: A plural noun should be used for collection names

A URI identifying a collection should be named with a plural noun, or noun phrase,
path segment. A collection’s name should be chosen to reflect what it uniformly contains.

For example, the URI for a collection of player documents uses the plural noun form
of its contained resources:
`http://api.soccer.restapi.org/leagues/seattle/teams/trebuchet/players`