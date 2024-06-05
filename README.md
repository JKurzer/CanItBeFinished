# Can it be finished?
- Not all software can be finished. This is not knowable.
- Not all software can be finished from the perspective of the user. This is knowable.
- Not all software can be finished from the perspective of the user's build environment. This is knowable.

## Definition By Negative
Finishability is not good or bad. Many vital pieces of software exist in high-change domains where there is no way to even imagine a point where that piece of software might stop fundamentally changing. We need a way to say that this piece of software can or cannot be finished from the end user's perspective. Let's call these user-breaking changes. In SemVer, these would be changes that necessitate incrementing the left-most version number, rather than merely likely meriting it. Generally, it's hard to say that a piece of software won't receive such a change, but it's easy to say that a piece of software certainly will. These changes fall into four categories.  

- Subtractive API changes.
- Semantic API changes, regardless of syntactic changes.
- Minimum environment requirement changes with no fallback path.
- Inability to meet the minimum safety requirements necessary for function.

These changes are guaranteed, practically speaking, to break at least one user's existing code. While our definitions are absolute for the purposes of this document, we recognize that's not useful. Instead, we propose four major categories of software. These are unlikely to be labeled in most applications or codebases, but are important as ways of thinking about dependencies.

## Categories
### ORCs
If a piece of software can expect these changes, we can say that it **Often Receives Changes.** This isn't good or bad. It just is. Many critical pieces of software MUST fall into this category. Orcs are an important part of our lives as engineers and can't be avoided. A defining aspect of ORCs is that they are not finishable. A great example of this is Chrome. Chrome cannot be finished and will **Often Receive Changes**.

### NORCs
If a piece of software probably receives user-breaking changes at a slow cadence irrelevant to most users other than library maintainers, we can say that **Number One Rarely Changes**. These are pieces of software where the major version is not __required__ to change more than every few years. We do not place a boundary on the scope of the user-breaking changes. NORC is the loosest of these categories, and is generally a descriptive rather than prescriptive term. It's something one can really only assess long into a piece of software's lifecycle. Software where the **Number One Rarely Changes** exists in domains that are moderate to high change, but where the user-facing outcomes of those changes are both small and rare.

### NONCs
Some pieces of software represent either a very small piece of specific functionality or are finishable by definition. The implementation of quicksort might change, but the API for an implementation will likely never change in a subtractive fashion. One important idea here is that almost no software starts in a state where the **Number One Never Changes** from a semantic versioning perspective. Most, instead, can be said to reach a state where the **Number One Never Changes** again. Thanks to our definitions, this concept is most useful for discussing *libraries* that actively seek to ensure that the **Number One Never Changes**. These are relatively rare, but often critically important.

### NIBs
Finally, some pieces of software exist that offer an explicit guarantee that breaking changes will be avoided at almost any cost. For it to be meaningful, this goal is generally a literal guarantee driven by provable test compliance. These pieces of software can be said to have **No Intended Breakage**, but may exist in a domain where such a change is necessary due to external factors such as a discovered cryptographic vulnerability that would create an *inability to meet the minimum safety requirements* and *changes the minimum build requirements in a breaking way*. 

## Usefulness
ORCs, NORCs, NONCs, and NIBs. It's too many terms, and most things are **NORCs** if you get pedantic. A specific library may be a **NONC** but this is rare. That leaves **ORC** and **NIB**. Unlike the other defintions, these are project philosophies. That means that they can be stated definitively and intentionally. This makes them extremely powerful ways of shaping the development goals during the engineering process. You are unlikely to ever call something an **ORC** or a **NIB** but you should know which you are making. Good luck, and I'll see you on the other side.
