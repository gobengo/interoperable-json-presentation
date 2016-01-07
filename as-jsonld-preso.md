autoscale: true

# [fit] Interoperable JSON
## [fit] w/ W3C Activity Vocabulary and JSON-LD

#### Benjamin Goering
#### Product Manager, Platform @Livefyre

---

# Real-Time JSON?

^ Who has designed a JSON API/domain before? Do they work together?
^ Going to look at some standards and tools that can help with interoperability.

* REST APIs
* {Web,}Socket APIs
* Webhook APIs
* JavaScript Object APIs
* Import/Export

---

# Outline

* Why?
* ActivityStreams
  - History
  - Current Status
* += JSON-LD
  - Extensibility
  - Translation
* In the Wild

---

# Why do I care?

* Provided lots of APIs
* Consumed lots of APIsTwitter, Facebook, Instagram, {m,}RSS
* Imported Lots of Data
    - e.g. Comments, Single Sign On with customers' IDPs
* They are ALL different :unamused:
* Built lots of Web Components
    - Open Sourced most. Doesn't matter.

---

^ We have lots of web components, see. And half are open source.
^ Customers should be able to fork them to add feature they want.
^ Or build their own with the UX they prefer, but without having to worry about Backend/Real-time.
^ (but this rarely happens)

![fit](https://cldup.com/ul5yk1dkHF.png)

---

![left,fit](https://cldup.com/teFSzJ-dMk.png)
![right,fit](https://cldup.com/pEADCOjG8R.png)

---

# Snowflakes[^1]

![](https://c1.staticflickr.com/9/8393/8668859150_3b9bd7a6d3_b.jpg)

![inline](https://cldup.com/pNe-i4O1LF.png)

[^1]: [https://indiewebcamp.com/snowflake](https://indiewebcamp.com/snowflake)

---

# JSON Standards

^ Mixed Success
^ Blip of PortableContacts highlights importance of stewardship

* PortableContacts[^3] \(2008\)
    - Wiki Down, Last list post 2013, Google dropped support 2012
* oEmbed[^2] \(2010\) - "Embeds" and media
    - Powers WordPress shortcodes, Livefyre Content Attachments
* Swagger[^4] - HTTP APIs
  * Nov, 2015: donated to Open API Initiative, Linux Foundation
* ActivityStreams - "Social" Data

[^2]: [http://oembed.com/](http://oembed.com/)

[^3]: [http://portablecontacts.net/](http://portablecontacts.net/)

[^4]: [http://swagger.io/](http://swagger.io/)

---

# "Activity Streams" History

* 4/2005 - Why The Lucky Stiff [coins "Tumblelog"](http://viewsourcecode.org/why/redhanded/inspect/tumbleloggingAssortedLarvae.html)
* 7/2006 - Twitter launches
* 9/2006 - Facebook launches News Feed
* 2/2007 - Tumblr Launches
* 7/2007 - XEP-0108: User Activity (in XMPP)
* 10/2007 - Friendfeed launches
* 12/2007 - DiSo (Distributed Social) Community [is Born](https://web.archive.org/web/20150930044942/http://factoryjoe.com/blog/2007/12/06/oauth-10-openid-20-and-up-next-diso/)
* 1/2008 - DiSo wiki starts catalogging ['activity-streams'](https://web.archive.org/web/20080305123155/http://diso-project.org/wiki/activity-streams) design pattern
* 1/2008 - (Google's) OpenSocial 0.7 [introduces](https://opensocial.github.io/spec/2.5.1/OpenSocial-Specification-Release-Notes.xml#rfc.section.10) `opensocial.Activity`, went on to power Buzz, Google+, Apache Shindig
* 3/2008 - DiSo WordPress Plugin [adds "ActionStream"](https://github.com/diso/diso/commit/975e8e4ce3bce825ee3193fcda414621e2e222f0)
* 6/2008 - Chris Messina proposes ["Adding richness to activity streams"](https://web.archive.org/web/20151029155723/http://factoryjoe.com/blog/2008/06/11/adding-richness-to-activity-streams/), proposes AtomPub extensions

---

![fit](https://cldup.com/mJPcu__Cvm.png)

---

# "ActivityStrea.ms" History

* 12/2008 - http://activitystrea.ms [kicked off](http://factoryjoe.com/blog/2008/12/20/where-were-going-with-activity-streams/)
    - ["Activities in Atom"](http://factoryjoe.com/blog/2008/12/20/where-were-going-with-activity-streams/): actor, verb, object, indirect object
    - ["Activity Schema"](https://web.archive.org/web/20090205072910/http://martin.atkins.me.uk/specs/activitystreams/activityschema): Blog Entry, Note, Photo, Video, Bookmark
* 4/2009 - [Facebook Open Stream API uses it](https://web.archive.org/web/20090514174714/http://developers.facebook.com//news.php?blog=1&story=225)
* 12/2008 - MySpace, Windows Live, Opera, YouTube, and [30 other international social networks](https://web.archive.org/web/20091223044804/http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!43432.entry)
* 5/2009 - Monica: "we should probably discuss what the activities would look like in JSON"
* 6/2010 - "[Gnip pledges allegiance to Activity Streams](https://blog.gnip.com/activity-streams/)"
* 7/2010 - ["json-activity-01"](https://web.archive.org/web/20100917032204/http://activitystrea.ms/head/json-activity.html)
* 12/2010 - Facebook Drops Activity Streams (Open Graph, Timeline came 6 months laterer)
* 08/2011 - [OpenSocial 2.0 adopts ActivityStrea.ms](https://opensocial-resources.googlecode.com/svn/spec/2.0/OpenSocial-Specification-Release-Notes.xml#ActivityStreamsSupport)
* 2011-2014 - The dark period... not really
    - GNIP did great
    - AJAX became more supported, JavaScript/JSON became more prevalent. Websockets and Webhooks happened. The web got way more real-time
    - ActivityStreams 1.0 JSON solidified
    - The big Social Networks got bigger, platforms more controlled (e.g. [Twitter v1.1](https://blog.twitter.com/2012/changes-coming-in-version-11-of-the-twitter-api)), got better at tracking user behavior, launched advertising products, IPO'd

---

# ~~ActivityStrea.ms~~ - W3C Social Data Syntax

* 7/2013 - [James Snell posts first draft of ActivityStreams 2.0](https://web.archive.org/web/20130716020256/http://tools.ietf.org/html/draft-snell-activitystreams-00#section-1.1)
* 7/2014 - [W3C Announces Social WG](https://www.w3.org/blog/news/archives/3958)[^5]
* 12/2014 - [OpenSocial Donates all work to W3C](http://www.w3.org/2014/12/opensocial.html.en)

> **Social Data Syntax**
> A JSON-based syntax to allow the transfer of social information, such as status updates, across differing social systems. One input to this deliverable is ActivityStreams 2.0.
-- W3C Social WG Charter, "Deliverables"

* 12/2015 - Social WG F2F in San Francisco. [Resolved to keep AS2 on Technical Reocmmendation track](http://socialwg.indiewebcamp.com/irc/social/2015-12-01#t1448995347282). Many issues resolved.
    - [http://www.w3.org/TR/activitystreams-core/](http://www.w3.org/TR/activitystreams-core/)
    - [http://www.w3.org/TR/activitystreams-vocabulary/](http://www.w3.org/TR/activitystreams-vocabulary/)

[^5]: [https://www.w3.org/wiki/Socialwg/](https://www.w3.org/wiki/Socialwg/)

---

![](https://www.w3.org/wiki/images/thumb/d/d6/2015-12-02-w3c-f2f.jpg/1000px-2015-12-02-w3c-f2f.jpg)

---

```json
{
  "@context": "http://www.w3.org/ns/activitystreams",
  "type": "Add",
  "actor": {
    "type": "Person",
    "name": "Sally"
  },
  "object": {
    "type": "Image",
    "name": "A picture of my cat",
    "url": "http://example.org/img/cat.png"
  },
  "target": {
    "type": "Collection",
    "name": "My Cat Pictures"
  }
}
```

---

![left,fit](https://cldup.com/teFSzJ-dMk.png)
![right,fit](https://cldup.com/pEADCOjG8R.png)

---

![left,fit](https://cldup.com/uKlYcYxPCc.png)
![right,fit](https://cldup.com/pEADCOjG8R.png)

---

# I forgot something...

```json
{
    "tweetMeta": {
        "verified_user": false
    }
}
```

---

![fit](http://imgs.xkcd.com/comics/standards.png)

---

# JSON-LD

## Extensibility, Standard Transformation Algorithms

---

# Warning! Namespaces ahead!

---

# Bella

```json
{
  "@context": "http://www.w3.org/ns/activitystreams",
  "id": "acct:1428430672529@livefyre.com",
  "name": "Bella Boomerang",
  "url": "http://livefyre.com/BellaBoom84",
  "image": "https://appkit-mock-assets.s3.amazonaws.com/avatars/model-013.jpg",
  "isTwitterVerified": true // What does that mean... Whyn not is_verified? ??
}
```

---

# Bella, Verified

```json
{
  "@context": [
    {"isTwitterVerified": "https://twitter.com/ns#isVerified"},
    "http://www.w3.org/ns/activitystreams"
  ],
  "id": "acct:1428430672529@livefyre.com",
  "name": "Bella Boomerang",
  "url": "http://livefyre.com/BellaBoom84",
  "image": "https://appkit-mock-assets.s3.amazonaws.com/avatars/model-013.jpg",
  "isTwitterVerified": true
}
```

---

# JSON-LD Algorithms

> This specification defines a set of algorithms for programmatic transformations of JSON-LD documents. Restructuring data according to the defined transformations often dramatically simplifies its usage. Furthermore, this document proposes an Application Programming Interface (API) for developers implementing the specified algorithms.
-- [JSON-LD 1.0 Processing Algorithms and API](http://www.w3.org/TR/json-ld-api/)

* Expanding
* Compacting

---

# Bella, Verified, Moody, Expanded

Distributes the context into all the keys/values (messy but explicit)

```json
[
  {
    "http://www.w3.org/ns/activitystreams#id": [
      {
        "@value": "acct:1428430672529@livefyre.com"
      }
    ],
    "http://www.w3.org/ns/activitystreams#image": [
      {
        "@id": "https://appkit-mock-assets.s3.amazonaws.com/avatars/model-013.jpg"
      }
    ],
    "https://twitter.com/ns#isVerified": [
      {
        "@value": true
      }
    ],
    "http://jabber.org/protocol/mood#mood": [
      {
        "@id": "http://jabber.org/protocol/mood#proud"
      }
    ],
    "http://www.w3.org/ns/activitystreams#name": [
      {
        "@value": "Bella Boomerang"
      }
    ],
    "http://www.w3.org/ns/activitystreams#url": [
      {
        "@id": "http://livefyre.com/BellaBoom84"
      }
    ]
  }
]
```

---

# Bella w/ is\_twitter\_verified

What if I (or a colleague, partner, customer) had done this?

We have to translate! Bugs?

```json
{
  "@context": [
    {"is_twitter_verified": "https://twitter.com/ns#isVerified"},
    "http://www.w3.org/ns/activitystreams"
  ],
  "id": "acct:1428430672529@livefyre.com",
  "name": "Bella Boomerang",
  "url": "http://livefyre.com/BellaBoom84",
  "image": "https://appkit-mock-assets.s3.amazonaws.com/avatars/model-013.jpg",
  "is_twitter_verified": true
}
```

---

# Translation w/ JSON-LD Compaction

compact(objectWithOldContext, newContext) -> translatedObject

---

# Object

```json
{
  "@context": [
    {
      "isTwitterVerified": "https://twitter.com/ns#isVerified"
    },
    "http://www.w3.org/ns/activitystreams"
  ],
  "id": "acct:1428430672529@livefyre.com",
  "name": "Bella Boomerang",
  "url": "http://livefyre.com/BellaBoom84",
  "image": "https://appkit-mock-assets.s3.amazonaws.com/avatars/model-013.jpg",
  "isTwitterVerified": true
}
```

---

# New Context

```json
{
  "@context": [
    {
      "is_verified": "https://twitter.com/ns#isVerified"
    },
    "http://www.w3.org/ns/activitystreams"
  ]
}
```

---

# Translated

```json
{
  "@context": [
    {
      "is_verified": "https://twitter.com/ns#isVerified"
    },
    "http://www.w3.org/ns/activitystreams"
  ],
  "id": "acct:1428430672529@livefyre.com",
  "image": "https://appkit-mock-assets.s3.amazonaws.com/avatars/model-013.jpg",
  "name": "Bella Boomerang",
  "url": "http://livefyre.com/BellaBoom84",
  "is_verified": true
}
```

---

# Translating old JSON to new format

1. Add a `@context` to old JSON, mapping the properties to URIs
2. Decide on the new shape you want
3. Create a new `@context` mapping the new shape's properties to URIs
4. Compact

Little boilerplate required for interoperability.

---

# Contexts are Useful

## www.w3.org/ns/activitystreams

```json
{
  "@context": [
    {
      "dc": "http://purl.org/dc/elements/1.1/",
      "dct": "http://purl.org/dc/terms/",
      "dctypes": "http://purl.org/dc/dcmitype/",
      "foaf": "http://xmlns.com/foaf/0.1/",
      "vcard": "http://www.w3.org/2006/vcard/ns#",
      "org": "http://www.w3.org/ns/org#",
      "prov": "http://www.w3.org/ns/prov#",
      "geo": "http://www.w3.org/2003/01/geo/wgs84_pos#",
      "geos": "http://www.opengis.net/ont/geosparql#",
      "ical": "http://www.w3.org/2002/12/cal/ical#",
      "xsd": "http://www.w3.org/2001/XMLSchema#"
    },
    {
      "@vocab": "_:",
      "as": "http://www.w3.org/ns/activitystreams#",
      "updated": {
        "@id": "as:updated",
        "@type": "xsd:dateTime"
      },
      "width": {
        "@id": "as:width",
        "@type": "xsd:nonNegativeInteger"
      },
      "optional": {
        "@id": "as:optional",
        "@type": "xsd:boolean"
      },
      "role": {
        "@id": "as:role",
        "@type": "@id"
      }
    }
  ]
  // LOTS MORE
}
```

---

# Big Deal. But does anyone use it?

Yes[^10]

* Google Knowledge Graph Search API, Actions in Gmail
* Schema.org
* Microsoft
* Yandex
* cio.gov "Project Open Data Metadata Schema v1.1"
* Many other W3 WGs
  - Web Payments
  - Web Annotation
  - Open Badges
* GOV.UK - Court and tribunal finder
* https://project-open-data.cio.gov/v1.1/schema/catalog.jsonld

[^10]: [https://github.com/json-ld/json-ld.org/wiki/Users-of-JSON-LD](https://github.com/json-ld/json-ld.org/wiki/Users-of-JSON-LD)

---

# What does this buy the standards community?

* Focus on vocabularies, not syntax
* Because linked data vocabularies can now be equally represented in XML, JSON(-LD) with whatever shape, YAML, Turtle, HTML+RDFa
  - [Demo in AS-Vocabulary](http://www.w3.org/TR/activitystreams-vocabulary/)?
* ActivityStreams is more of a Vocabulary than a Syntax
* Re-use old vocabularies in any serialization
  - PubSubHubBub - Was XML-RPC, but really a lot of the value in it was vocabulary and semantics
  - foaf - Social Relationships
  - sioc - Semantically Interlinked Online Communities
  - [Dublin Core](http://dublincore.org/documents/dcmi-terms/) - publishing, citation, provenance
* Let's never talk about Syntax Again

---

# What does this buy the Social Web?

* Moving on to harder problems
  * Synchronization
  * Security and Privacy
  * Identity
  * Scale

The other two Social WG Deliverables:

> **Social API**
> A document that defines a specification for a client-side API that lets developers embed and format third party information such as social status updates inside Web applications. One input to this deliverable is the OpenSocial 2.5.1 Activity Streams and Embedded Experiences APIs Member Submission.
> <br >
> **Federation Protocol**
> A Web protocol to allow the federation of activity-based status updates and other data (such as profile information) between heterogeneous Web-based social systems. Federation should include multiple servers sharing updates within a client-server architecture, and allow decentralized social systems to be built. One possible input to this task is WebMention and another possible input is the Linked Data Platform. Note that the Working Group may not develop the Federation Protocol into a Recommendation and it may become a Working Group Note.

* [ActivityPump](https://w3c-social.github.io/activitypump/)
* [OpenID Connect](https://openid.net/connect/) - JSON-LD should make syntax/vocab debates unnecessary

---

# What does this buy you?

* Don't invent another snowflake
* Design your domain, not syntax
  - Future-syntax proof
* JSON translation or re-shaping without bugs
* A standard import/export format

---

# Follow Along

* W3 Social WG Mailing List [^11]
* W3 JSON-LD Community Group [^12]
* Indiewebcamp and Homebrew Website Club[^13]
* slides link

[^11]: [https://lists.w3.org/Archives/Public/public-socialweb/](https://lists.w3.org/Archives/Public/public-socialweb/)

[^12]: [https://www.w3.org/community/json-ld/](https://www.w3.org/community/json-ld/)

[^13]: [http://indiewebcamp.com/Homebrew_Website_Club](http://indiewebcamp.com/Homebrew_Website_Club)
