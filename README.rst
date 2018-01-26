Haskell Ecosystem Proposals
============================

This repository contains specifications for proposed changes to the
broader haskell ecosystem. See the `Proposal
Process Process
<https://github.com/haskell/ecosystem-proposals/blob/master/proposals/0000-proposal-process.rst>`_
for a complete description of the ecosystem proposal process.

It is shamelessly copied from the one used for `GHC Proposals <https://github.com/ghc-proposals/ghc-proposals>`_


What is a proposal?
-------------------

An Ecosystem Proposal is a document describing a proposed change to the Haskell Ecosystem. These
include,

* Interoperability between package managers (e.g. cabal-install/hackage and
  stack/stackage).

* Anything else of broader interest to the community.

This list is currently deliberately short to keep it simple and focussed, it can
be expanded as we as a community gauge the receptiveness of the community to
this process.

How do I comment on a proposal?
-------------------------------

Discussion on a proposal occurs on its associated pull request. Click on the
Pull Requests tab in GitHub to see a listing of the proposals currently under
discussion. To see the text of the proposal click on the "Files Changed" tab on
corresponding Pull Request page.

Github offers two ways of viewing diffs: the "source diff" view, which shows a
plain text diff, and the "rich diff" view, which provides a more readable
rendered view of the markup. The view can be selected using the buttons on the
top-right corner of the "Files Changed" tab.

.. figure:: rich-diff.png
    :alt: The view selector buttons.
    :align: right

    Use the view selector buttons on the top right corner of the "Files
    Changed" tab to change between "source diff" and "rich diff" views.

Feedback on a proposal can be offered on open pull requests using both Github's
in-line and pull request commenting features. Do note, however, that inline
comments can only be added via the "source diff" view.

.. figure:: inline-comment.png
    :alt: The ``+`` button appears while hovering over line in the source diff view.
    :align: right

    Hover over a line in the source diff view of a pull request and
    click on the ``+`` to leave an inline comment

How do I submit a proposal?
---------------------------

While the full process is described in the `proposal
<https://github.com/haskell/ecosystem-proposals/blob/master/proposals/0000-proposal-process.rst>`_ describing the proposal
process, here is a short summary,

1. Edit the `template
   <https://github.com/haskell/ecosystem-proposals/blob/master/proposals/0000-template.rst>`_
   to reflect your proposal. Rename the template file according to your
   desired proposal, but leave the numerical prefix as ``0000``.
   This can be done either online through GitHub's in-place
   editing feature (the pencil icon visible when viewing a file on GitHub)
   or by forking this repository and cloning the fork.
   See GitHub's `documentation
   <https://help.github.com/articles/fork-a-repo/>`_ if you are unfamiliar with
   this aspect of GitHub's workflow.

2. Write the proposal. At very least this should describe the following,

   a. *Motivation*: What is the problem that you are trying to solve? Be specific:
      a concrete example or two can do wonders. Be sure to point out the
      particular ways in which the status quo falls short.
   b. *Proposed Change*: What change are you proposing? This is the
      specification of your change and should be precise and comprehensive. This
      might include,

      * scope of the change, what does it affect? cabal? stack? a web site?
      * the intended operation of the new change
      * how the proposed change addresses the original problem
        (perhaps returning to the concrete examples introduced in the
        *Motivation* section).
      * how the proposed change might interact with existing ecosystem features.
        In particular, pay attention to any unintended effects outside the
        immediate scope of the particular change.

      This generally needn't discuss the implementation of the change.
   c. *Drawbacks*: There's no such thing as a free lunch; what is the cost of
      your proposal? This includes the cost of implementing the proposal,
      mainintaining it indefinitely, teaching it to new users, and considering
      its interaction with future proposals.
   d. *Alternatives*: What alternatives to the proposed change exist? These can
      range from minor variants to completely . This doesn't need to go into
      great detail, just give the reader a sketch of the design space.
   e. *Unresolved questions*: What issues area still outstanding in the design?
      This needn't discuss outstanding *implementation* questions, we are
      presently only concerned with the conceptual design of your idea.

   Note that proposals are written in `ReStructuredText
   <http://www.sphinx-doc.org/en/stable/rest.html>`_ rather than Markdown for
   its expressiveness and ease of integration into other GHC infrastructure.
   See the `GHC Users Guide
   <http://downloads.haskell.org/~ghc/latest/docs/html/users_guide/editing-guide.html>`_
   for a brief introduction to ReStructuredText.

3. When you feel your proposal document is complete, push your branch to your
   fork (e.g. ``git push origin fancy-new-idea``), and open a Pull
   Request requesting that your branch be merged into the ``master`` branch of
   the ``haskell/ecosystem-proposals`` repository. If you unfamiliar with
   GitHub pull requests then see the `relevant documentation
   <https://help.github.com/articles/creating-a-pull-request/#creating-the-pull-request>`_.

   Be sure to include a link to the rendered view of your proposal in the pull
   request description. Your proposal will automatically be announced on the
   ``TBD, probably haskell-cafe`` mailing list when this pull request is opened.

4. Discussion will proceed on the pull request; it is very likely that multiple
   iterations will be necessary before the proposal stabilizes.

5. To be decided (as a community): what it means for a proposal to be accepted,
   and what reasonable expectations are if this happens.
   
   In particular, changes require resources, and the haskell ecosystem has become
   a big ship which has a very wide turning circle.
