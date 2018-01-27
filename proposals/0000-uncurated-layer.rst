.. proposal-number:: Leave blank. This will be filled in when the proposal is
                     accepted.

.. highlight:: haskell

Uncurated Hackage Layer
==============

Motivation
----------

There is a tension between two purposes of Hackage -- first as a central repository of Haskell code, and second as a curated store that has artifacts that are intended to be correctly built and depended upon in a self-contained fashion (i.e. which contain all information necessary to correctly build them). The way the latter is accomplished is by asking packages follow the Package Versioning Policy (https://pvp.haskell.org/) that is used to inform clients of a package of changes to that package that might affect them, and to provide a way for clients to specify a particular range of versions of a dependency that they are compatible with.

The aim of this proposal is to separate these two purposes, by allowing authors to distinguish if they wish to opt-out of following the PVP and the attendant curation process that helps to maintain correct dependency information. In so doing, they recognize that their discoverability on Hackage may be reduced, since the UI will give precedence to those packages which, in conjunction with potential cabal revisions, are self-contained with regards to the information necessary to build them.

Proposed Change
---------------

This is a phased proposal with gradual rollout possible, in dependency order of the steps. The first phase is immediate. Other phases may be rolled out at any pace, but necessarily in the order specified (including the collapse of two steps into a joint step).

The desired end-state will have the following properties:

1) Packages will have an additional flag set in the Hackage package database, that indicates if they are curated or not. This flag is set *per version*.
2) Package authors will set this flag *on upload*, by setting the "x-uncurated" property of the cabal file of a package to "true". If no "x-uncurated" property is set, this will be considered "false".
3) Hackage will provide two package repository roots -- http://hackage.haskell.org and http://hackage.haskell.org/uncurated These roots will provide index-01.tar.gz files that contain the information, respectively, for curated packages, or for all packages. The uncurated root will contain no revision information.
4) Curated packages cannot depend on uncurated packages, and the hackage server will detect this as an error at upload time.
5) Uncurated packages may be "adopted" into the curated ecosystem by trustees. Metadata revisions necessarily remove the x-uncurated property from the revised cabal metadata.

The first phase of this rollout is simply social. It has the following properties:

+ Hackage trustees will recognize and respect the uncurated flag, and not contact those who set it with any issues. They *will* retain the ability to make metadata revisions, bearing in mind that they must remove the x-uncurated property from revised metadata.

The second phase is a technical change as soon as possible to enforce the semantics of x-uncurated:

+ Hackage will ensure that no revision has x-uncurated set to true.

The third phase is implementation of UI:

+ The uncurated flag will be detected and displayed on a package's page, as part of the general data provided about a package. It will also be provided in search and browse results. Ideally, search and browse results will be extended in general with the ability to preform in-page filtering on flags and fields, such as "library", curated status, deprecation status, etc.

The fourth phase is indices:

+ The uncurated package repo root will be built and provided.

Fifth, Hackage can now begin to enforce the policy regarding curated packages not depending on uncurated packages.

+ Curated package uploads will be checked on upload to ensure they don't have dependencies on uncurated packages. Further, the curated index will only provide information on curated packages.

In the end state, the intent is that uncurated (as well as deprecated) packages will be hidden by default in the filtering settings of search and browse interfaces. These UI settings will be able to be persisted, so that users may change their preferences in this regard.

Future Plans
---------------
In the future, full support for collections may be implemented in Hackage. At such point, the current "curated" layer may simply become one of a number of collections (though likely the largest). The UI surrounding display and discovery of curated and uncurated packages, etc. would likely be transformed in such a setting (and indeed the two package repos might be merged again, with support for distinguishing curated and uncurated instead coming through some future collection specification). This is just speculation at the moment, but worth bearing in mind. The end-state given by this proposal is not necessarily the end-state of hackage -- just something that accomplishes the narrow goals set forward in the motivation without reliance on other potential work that is not yet fully specified.
