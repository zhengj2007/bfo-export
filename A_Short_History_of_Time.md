# UNDER CONSTRUCTION #

See status notes and TODO list at bottom. For the moment I would appreciate that this page not be edited directly, or, if necessary, to have comments by other to be added to the bottom of the page below the status section, with the author noted.

# Introduction #

This page is compiled initially by [Alan Ruttenberg](http://alan.ruttenbergs.com/) in order to capture pointers to early discussions and writings in the archive that relate to temporalizing relations in BFO OWL. It aims to provide a more easily accessible way to review the trail of activity on the subject and to hopefully provide background for discussion of the current (2013) controversy about adoption of temporalized relations in BFO 2. From the record presented below, it should be clear that temporal relations have been part of the theory of relation ontology for at least 8 years, and there have been concerns about this issue in the user community, on the record and for the most part unmet for 5 years, with work on trying to address the problem in practical application of ontology for somewhere between 5 and 8 years.

Note that the Relation Ontology was first instantiated as an OBO format ontology and only later as an OWL ontology. As best as I can tell, the OBO version predates 2004 (based on reading [this paper](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2447432/pdf/CFG-05-509.pdf), while an OWL version first appears in 2006 (based on the date recorded in this [first version of RO in the sourceforge CVS repository](http://obo.cvs.sourceforge.net/viewvc/obo/obo/website/htdocs/ro/ro.owl?revision=1.1&view=markup)

# History #

## April 2005 Relations in Biomedical Ontologies ##

This [paper](http://genomebiology.com/2005/6/5/R46) provided a formal theory of the relationship between class and instance level relationships, creating a more solid basis for the Relation Ontology. In it the distinction between continuants and processes is made, and throughout the paper relations are defined in these terms. Most relations involving at least one continuant are 3-place relations with the third argument being time, whereas most process-process relationships are 2 place relations at the instance level. The class level relations are defined by quantifying over time in their definitions. Different quantifications are used. In many cases the class relations obtain when the instance relation is satisfied at all times. In some cases (e.g. has\_participant) the class level relation is obtained when instance level relation is satisfied at some time.

## May 2008 Workshop on the Relationship Ontology ##

This two-day [NCBO workshop](http://www.bioontology.org/wiki/index.php/OntologyRelations)  focused on the relationship between classes in ontologies, as well as relationships among instances of those classes.

This meeting brought together [many stakeholders](http://www.bioontology.org/wiki/index.php/OntologyRelations#Attended_.28alphabetically.29) and developers of the relations ontology. Among other things, a number of issues that are central to understanding the motivation of the current temporal relation proposal are raised there.

  * A review of the role of time in relations. Time at the instance level is discussed at several points.
  * Presentations [1](http://www.bioontology.org/wiki/images/a/a1/Relations_for_representing_developmental_anatomy.ppt) [2](http://www.bioontology.org/wiki/images/f/f3/Fabian_developmental_relations.pdf) by Fabian Neuhaus and David Osumi-Sutherland offering proposals to address some of the temporal relation needs.
  * The difference between class-level and instance relations
  * Noting that OWL has limited native facilities for representing classes, in Alan Ruttenberg's [slides](http://www.bioontology.org/wiki/images/d/dd/Ruttenberg-ro.pdf)
  * Some discussion of the transformation\_of relation, which was inexpressible in OWL

A series of action items is recorded in the [meeting notes](http://www.bioontology.org/wiki/index.php/OntologyRelationsMeetingNotesCompiled). I note a couple of these here as they are pertinent to the current discussion:

```
3. Define instance level relations as well. Clarity is important. Relations need to be clarified whether they be used
for type_type/type_instance/instance_instance.

4. RO should have a commitment to an upper ontology and it shall be BFO.
```

## October 2008 email to OBO-relations email list ##

[Bill Hogan writes](https://groups.google.com/d/msg/obo-relations/u9gEGYNq7xA/YBQ4TCikds8J) raising issues about problems with the inverses of relations as recorded in the [then-RO](http://obo.cvs.sourceforge.net/viewvc/obo/obo/website/htdocs/ro/ro.owl?view=log). As will be the case, a long discussion ensues.<br>

<b>Class vs. instance level relations and inverse relations</b><br><br>

Presently in the Relation Ontology, it appears that all the relations are assumed to be class-class (or type-type) relations.  If so, then there are errors in the asserted properties of relations.<br>
<br>
part_of and has_part are stated to be inverses of one another, which is not universally true at the class level (but it is so at the instance level).  For example, uterus part_of pelvis, but not pelvis has_part uterus (because not every pelvis has a uterus as a part). Hence the need for the integral_part_of and has_integral_part relations which are truly inverses of one another (note that these two relations are not needed at the instance level, because instance_part_of and instance_has_part are inverses already).<br>
<br>
<h2>November 2008 email in OBO-relations</h2>

<a href='https://groups.google.com/d/msg/obo-relations/pNabO2LhXoI/vM4qcCfErFoJ'>Alan Ruttenberg writes</a> a response to a message in this thread noting the lack of specification for how temporality at instance level is represented in OWL, and having the first (informal) proposal of the current form the temporalized relations take in the BFO 2 draft <br><br>

<b>Re: [Obo-relations] original_part_of is not transitive</b> <br>

OK. Here is where the disconnect is. I didn't (and don't) read the<br>
instance level part_of as true for all time. In  RO the abstraction<br>
over time happens in the class relation. Instead OWL ontologies are<br>
typically considered SNAPs - they exist at some particular time. That<br>
time is the implicit time argument for all ternary relations with time<br>
in it.<br>
<br>
To avoid confusion I think this should be stated in terms of the<br>
binary instance level relation always_part_of relation<br>
always_part_of(x,y) = for all t: part_of (x, y, t)<br>
<br>
Otherwise we lose all ability to have time specific instance level<br>
relations in OWL ontologies (think development specific anatomy).<br>
<br>
<br>
<h2>April 2009 email to OBO-relations and BFO-discuss mailing lists</h2>

This <a href='https://groups.google.com/d/msg/obo-relations/X3yeI71uGck/Uddi3v8_4EgJ'>email</a> starts with an early, explicit, notice by <a href='Marijke.md'>Keet</a>, someone outside the direct group of OBO relations developers, noting discomfort with the treatment of time in the then current RO instantiation by her and others in the community. The thread extends for more than 50 posts, and is a wide-ranging discussion.<br>

<b>a modest proposal for transformation_of</b><br>

Dear all,<br>
I, and so I've heard some other people, are not quite happy with the<br>
limitations that one can't really represent temporal stuff, yet some<br>
of the RO relations do allude to temporal things.<br>
<br>
<BR><br>
<br>
<br>
<br>
<h2>November 2011 Basic Formal Ontology Editorial Meeting</h2>

This <a href='http://www.bioontology.org/wiki/index.php/BFO_2011'>meeting</a> launched the most recent BFO2 development effort. It's goals are expressed as:<br>
<br>
<blockquote><i>To define a strategy for the future maintenance of Basic Formal Ontology.<br>
To create a BFO Reference, designed as an authoritative documentation of the<br>
BFO ontology, including an updated version of the BFO 1.0 taxonomy together<br>
with the top level relations of the Relation Ontology. To define a strategy to<br>
create BFO OWL, including a treatment of temporal relations, based on BFO Reference.</i></blockquote>

During that meeting, <a href='http://bfo.googlecode.com/svn/trunk/docs/Mungall_RO_2012.pptx'>Chris Mungall presented</a> an idea we came up with for simplifying the authorship of ontologies, called shortcut relations - essentially a macro system in which an original OWL file with <a href='http://bfo.googlecode.com/svn/trunk/docs/npre20115292-2.pdf'>"shortcut" relations</a> is preprocessed to generate a new OWL file with the shortcut relations expanded into longer, more complicated, expressions necessary for better interoperation with the suite of OBO ontologies. The idea originates from work with the <a href='http://www.incf.org/programs/pons/activities/multi-task-force-meeting/at_download/event_pdf'>INCF</a> in which a deep dive into what desired relations between neurons would be, and noting the verbosity of their use in OWL, for which short-cut relations were offered as a solution. Short cut relations are present in RO, and code that preprocessed them is part of the <a href='http://code.google.com/p/owltools/wiki/OortIntro'>OORT</a> tool.<br>
<br>
Of note, that presentation mentioned what is now called <a href='http://purl.obolibrary.org/obo/bfo/2010-05-25/ruttenberg-bfo.owl'>ruttenberg-bfo</a> but was originally placed at <a href='http://purl.obolibrary.org/obo/bfo.owl'>http://purl.obolibrary.org/obo/bfo.owl</a>. In that presentation I note (slide 5)<br>
<br>
<b>
<blockquote>bfo.owl is a prototype – more of a model than an candidate. It isn't<br>
yet aligned with BFO reference and that is the eventual intention. It<br>
doesn't have definitions, it is subject to change, though classes and<br>
relations that are present in the final version will retain the same URIs<b><br>
</b></blockquote></b>

Alan Ruttenberg <a href='http://code.google.com/p/bfo/source/browse/releases/owl-ruttenberg-2010-05-25/README'>moved ruttenberg-bfo</a> to its current PURL in preparation for the BFO2 development group's release of a version of BFO2 for discussion.<br>
<br>
<h2>May 2012 Policy on coordination of BFO OWL with the BFO Reference</h2>

<a href='http://code.google.com/p/bfo/wiki/Proposal_for_how_we_manage_OWL_Reference_coordination'>This page</a> records a policy for how we will develop BFO OWL, the first principle of which establishes that the OWL version of BFO should have a clear understanding in terms of the BFO2 reference. It should be noted that Chris Mungall, who is listed as supporting these principles, has stated (personal communication) that he no longer supports this aspect of the development policy.<br>
<br>
<h2>July 2012 release of a the first version of BFO2 developed by the working group</h2>

In preparation for <a href='ICBO.md'>2012</a> the group release, on July 7, 2012, a <a href='http://purl.obolibrary.org/obo/bfo/2012-07-20/bfo.owl'>version of BFO2</a> intended for a wider community to review and for which they solicited feedback, accompanied by these <a href='http://purl.obolibrary.org/obo/bfo/2012-07-20/ReleaseNotes'>release notes</a>

<h2>January 2013 proposal for a release of "BFO 1.2"</h2>

In January 2013, <a href='http://groups.google.com/forum/?fromgroups=#!topic/bfo-discuss/iKBlfDPv5GM'>James Overton sent</a> a proposal to the bfo-discuss mailing list that a version of BFO version 1.2 be release, based, with little modification, on ruttenberg-bfo. Several things are worthy of note. Overton comments he has done little previous work on BFO.  While the proposal involves some members of the BFO2 OWL working group, no work on this version has happened on the fora for that group. The proposal is not in line with the agree upon development policy of the BFO2 OWL group. The proposal is made to the BFO-discuss group, whereas development of BFO2 has thus far occurred on the BFO-owl-devel mailing list.<br>
<br>
In addition, some interesting implications are made:<br>
<ul><li>That ruttenberg-bfo2 was a released version of BFO2<br>
</li><li>That "all of the relations published in the 2005 Relation Ontology paper" are included<br>
</li><li>That the work "reflects current OBO best-practices"</li></ul>

<b>Proposal for an Official BFO 1.2 Release</b><br>

On the last BFO OWL developers' call (2012-11-26), several developers raised concerns about the fragmentation of BFO versions (i.e. 1.1, ruttenberg-bfo2, Graz) currently used by OBO projects, which is causing problems with interoperability. It was suggested that a transitional release of BFO could consolidate improvements already in place and facilitate the transition to BFO 2. We have prepared a proposal for an official BFO 1.2 release that addresses these points (see <a href='1.md'>1</a> below).<br>
...<br>
<br>
<h1>Status</h1>

Doing this kind of digital archeology is time consuming. At this stage the rough outlines of the history are present. So this list is by no means complete, and I intend to do further work to fill out the essential history.<br>
<br>
TODO:<br>
<ul><li>Find and include emails discussing or announcing release of new RO, and choice to base OBO to OWL translation on ruttenberg-bfo.<br>
</li><li>Include reference to Mungall Critiques, and my email response assessing that many of the issues relate to permanent generic parthood.<br>
</li><li>Include email regarding representation of permanent generic part hood<br>
</li><li>History of Grewe et al paper drafts<br>
</li><li>Dig out more discussion of temporal relations and needs from mailing lists<br>
</li><li>Track down info about the CL meeting in which several of us - IIRC Chris, Robert Stevens, David O-S, Barry, discussed various options.