This is an evolving draft of the "open namespace process".  It is phrased for use with activitystreams, but the changes to generalize it would be trivial.

----

## The "namespace database"

There will be a master "database" maintained as one or more files in the w3c/activitystreams repo.  This database will enumerate all the terms in the namespace, and for each term it will state:

 - a stability level, one of "unstable", "testing", "stable", or "archaic", defined below
 - various RDF schema information about the term (domain, range, etc)
 - zero of more people who serve as editor (including relevant contact info, especially github username)
 - a specification fragment (in safe HTML or markdown) which describes and defines the term,
   possibly including examples and references
 - pointers to a test suite and/or validator for this term
 - pointers to systems which use or intend to use this term (possible
   with pointers to evidence, and more details like test results.)


The HTML and JSON-LD documents available at the vocabulary namespace URL will be generated from this database.  Since size is important for a JSON-LD context document, it may link to the full information rather than including it.

Not exactly sure the right way to maintain this database for easy hand editing with PRs.  See one suggestion for [syntax of namespace database files](./format.md).

## Pull requests

Pull requests to the database are evaluated by one or more "namespace maintainers" at their earliest convenience.  They are evaluated for process and safety, not for other issues like ontology design, uniqueness, relevance, adoption, utility, or editorial quality. If the PR is not an obvious accept or reject on process and safety grounds, it should be prompty escalated to the full group of namespace maintainers and potentially the CG for investigation, discussion, and a decision.  Safety issues may need to be escalated to the W3C or GitHub safety teams. Process issues are defined in this document; safety issues are defined in the CG code-of-conduct, the [W3C CEPC](https://www.w3.org/Consortium/cepc/), and other relevant documents.

Maintainers may make suggestions for improvement to the PR, as long as it is clear the PR will be approved promptly even if the suggestions are not accepted.

## New terms

This process allows anyone to add terms not currently in the database, with the following constraints:
 - the term is classified as "unstable"
 - the person making the pull request must be named as editor
 - one or more implementations must be listed (they may be "pending", that is, planning to implement support for the term) 
 - the editor must be a maintainer one of the listed implementations
 - additional people may be named as editor; they must comment on the PR stating they accept the responsibilities of co-editor.

## Updating terms

This process allows any editor of an "unstable" term to edit its documentation at will via PR. They may also add co-editors, subject to assent of the new editors, and change the implementation list.  They may also resign, by removing themselves from the editors list.

## Orphaned terms

Any term which has no editors may be claimed by someone who is a maintainer of an implementation.  (Or should there be a CG decision?  Or a waiting period to see if they are the only one who wants it?)

## Public Comments

People are encouraged to raise issues against the term.  They should do this as issues on the as repo which include the term prefixed by "as:" in the issue title.  Editors are required to be responsive to issues on their terms.  Issues ignored for more than 30 days are grounds for removal of all current editors, after 10 day warning.  (Alternatively, certain sets of terms may have their issues put on a different repo.  The term can include a link to the relevant issue tracker to use.)

## Advancement from "unstable" to "testing"

Once a terms has two or more working implementations and a test suite and/or validator, an editor may ask the CG to be advanced from "unstable" to "testing" status (by sumitting a PR with this change).  This is comparable to W3C Candidate Recommendation: it asks that people try implementing it, saying it will no longer be changed without good cause.  This advancement requires approval of the CG, which should heavily consider the track record on issue handling and the status of current implementations.

Any edits in testing require approval of the group.

## Advancement from "testing" to "stable"

Once a term has been in testing for at least 8 weeks, an editor may ask the CG to advance it to "stable".  This is comparable to W3C Recommendation, in that it signals the term is ready for wide use and that no more "substantive" changes (ones which might require changes to a conforming implementation) will be made to the terms documentation.  This advancement also requires approval of the CG.

Any edits in "stable" require approval of the group, and are unlikely to be approved unless they are fixing clear errors and supported by all implementors.

## Advancement from "stable" to "archaic"

If the community decides people should be generally steered away from a term, but it's already "stable" so it can't just be removed, its status may be advanced to "archaic".
