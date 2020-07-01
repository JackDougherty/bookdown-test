Preface
=======

<!-- R global options: each R chunk image to display without code (no echo); display PDF version over JPG/PNG when available -->

This is a test book

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png" /></a><br />This
work is licensed under a
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative
Commons Attribution-NonCommercial-ShareAlike 4.0 International
License</a>.

Authors and Contributors
------------------------

Info about each author

Info about each author

Info about each author

Info about each author

Info about each author

Info about each author

Info about each author

and contributor

Copyright with Open License
---------------------------

All text and code for this book is available on
[GitHub](https://github.com/jackdougherty/bookdown-test). This work is
licensed under a
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative
Commons Attribution-NonCommercial-ShareAlike 4.0 International
License</a>.<br>
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png" /></a>

<!--chapter:end:index.Rmd-->

Video Tests
===========

Problem: Video stream content from CT Digital Archives and Trinity
Kaltura automatically runs in autoplay mode in web browsers, and I have
not yet found a consistent way to block this from happening.

**BEFORE TESTING**: TEST in both Firefox and Chrome for auto-play issue.
Make sure that your browser settings do NOT block autoplay content by
default, since we cannot ensure that users will have same browser
settings as developers.

#### Best solution so far: Upload relevant clip to YouTube to display as iframe in web edition, with static image in PDF/Word editions, with caption link and footnote to full video, uploaded for historical preservation to CTDA or Kaltura

<iframe src="https://www.youtube.com/embed/NuWg9Jrkrpw?start=64" width="100%" height="400px">
</iframe>
<p class="caption">
Image 1: Here’s a sample YouTube caption, with option to add Markdown
links and footnote to full video at CTDA.
</p>

#### Works: Kaltura HTML5 embed avoids autoplay, but is it still supported?

…as shown below in <a href="#fig:2011-sheff-elizabeth2">2</a>.[1]. See
additional oral histories with participants in the Sheff v O’Neill
school desegregation lawsuit.[2]

<iframe src="https://cdnapisec.kaltura.com/html5/html5lib/v2.76/mwEmbedFrame.php/p/2366381/uiconf_id/42684261/entry_id/1_66aksvf1?wid=_2366381&amp;iframeembed=true&amp;playerId=kaltura_player&amp;entry_id=1_66aksvf1" width="100%" height="400px">
</iframe>
<p class="caption">
Image 2: View the [oral history video interview and
transcript](http://digitalrepository.trincoll.edu/cssp_ohistory/16) with
Elizabeth Horton Sheff in 2011.
</p>

#### Works but not properly formatted: Kaltura default embed code avoids autoplay

…as shown below in <a href="#fig:2011-sheff-elizabeth3">3</a>.This is
actually Anne Goldstein.

<iframe src="https://cdnapisec.kaltura.com/index.php/extwidget/preview/partner_id/2366381/uiconf_id/42684261/entry_id/1_qwum4bmu/embed/dynamic" width="100%" height="400px">
</iframe>
<p class="caption">
Image 3: This is actually Anne Goldstein sample video.
</p>

#### Issue Background

Here is an oral history video as displayed on the CTDA site, which does
NOT autoplay:

<a href="https://collections.ctdigitalarchive.org/islandora/object/120002:172" class="uri">https://collections.ctdigitalarchive.org/islandora/object/120002:172</a>

Here is the CTDA MP4 video stream for that object, which runs AUTOPLAY
in Chrome and FFox for Mac (and perhaps other browsers). CTDA says there
is no setting to turn off autoplay from datastreams

<a href="https://collections.ctdigitalarchive.org/islandora/object/120002:172/datastream/MP4" class="uri">https://collections.ctdigitalarchive.org/islandora/object/120002:172/datastream/MP4</a>

The stream above also works with this “view” ending, but also runs
autoplay:

<a href="https://collections.ctdigitalarchive.org/islandora/object/120002:172/datastream/MP4/view" class="uri">https://collections.ctdigitalarchive.org/islandora/object/120002:172/datastream/MP4/view</a>

#### Failed: CTDA iframe with autoplay=false

Here is Bookdown code-chunk that displays CTDA video in web edition,
static image in PDF edition, BUT CANNOT TURN OFF AUTOPLAY using the
iframe method, even if I add “?autoplay=0” or “?autoplay=false” to the
end of the src string, as suggested in Stackoverflow further below.

<iframe src="https://collections.ctdigitalarchive.org/islandora/object/120002:172/datastream/MP4?autoplay=false" width="100%" height="400px">
</iframe>
<p class="caption">
Image 4: Here’s a sample CTDA video caption, with option to add Markdown
link and footnote.
</p>

Also tried but did not succeed in adding a “no autoplay” command to the
iframe through jQuery in the custom-script.html

#### Not Bookdown-friendly: HTML5 video tag solution

Here’s a solution using the [HTML5 video
tag](https://www.w3schools.com/tags/tag_video.asp), which inserts user
“controls” but omits “autoplay”.

<video controls width="640" height="360">
<source src="https://collections.ctdigitalarchive.org/islandora/object/120002:191/datastream/MP4" type="video/mp4">
</video>

The HMTL5 video tag solution stops autoplay, but it is NOT ideal for
Bookdown-generated books because:

-   Bookdown/knitr does not *appear* to support the HMTL 5 video tag in
    the same way as it supports knitr::include\_url. I could submit a
    request to Bookdown to support HTML5 video tag, but it’s not likely
    to happen soon….
-   This means that I cannot use Bookdown built-in support for figures
    using the HMTL5 video tag, such as:
    -   the if-else statement in the R code-chunk that places the
        interactive iframe in HTML and the static floating image in the
        PDF, but the same caption for both
    -   figure auto-numbering, such as Figure 1.2, 1.3, etc.

#### Failed: iframe solution with short video clip, stored locally, with custom script - but it autoplays

<iframe src="images/2011-bernstein-demo-clip.mp4" width="100%" height="400px">
</iframe>
<p class="caption">
Image 5: Here’s a sample local video clip caption, with option to add
Markdown link and footnote.
</p>

An alternative method is to store the video locally and display with
HTML5 video tags, with a custom-script to stop auto-play. But Bookdown
does not recognize HMTL5, so no figure auto-numbering and captions will
be displayed, and therefore not ideal, as described above.

#### More resources

See Stackoverflow discussions about HTML iframe, HTML5 video, and
autoplay:

<a href="https://stackoverflow.com/questions/49256942/how-to-disable-autoplay-video-in-iframe" class="uri">https://stackoverflow.com/questions/49256942/how-to-disable-autoplay-video-in-iframe</a>
and
<a href="https://stackoverflow.com/questions/31956221/how-to-disable-auto-play-for-local-video-in-iframe" class="uri">https://stackoverflow.com/questions/31956221/how-to-disable-auto-play-for-local-video-in-iframe</a>

See Google Chrome Developer autoplay policy change in April 2018:

<a href="https://developers.google.com/web/updates/2017/09/autoplay-policy-changes" class="uri">https://developers.google.com/web/updates/2017/09/autoplay-policy-changes</a>

See Firefox Developer note for Video HTML5 autoplay:

<a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video" class="uri">https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video</a>

<!--chapter:end:1-video.Rmd-->

Notes chapter test
==================

Testing dynamic reference with footnote

In addition its financial assets, Clark also praised Hartford’s abundant
cultural riches. The nation’s best-known authors, Samuel Clemens (more
commonly known as Mark Twain) and Harriet Beecher Stowe (whose
best-seller, *Uncle Tom’s Cabin*, influenced the Civil War), both took
up residence in the city, alongside many of their literary companions,
editors, and publishers. In addition to serving as the state capital,
Hartford prized its extensive libraries, museum, and hospital. “The
Hartford school buildings are said to the finest in the State,” Clark
added, and called special attention to his alma mater, Hartford Public
High School, the second oldest in the nation, which also enjoyed “a
reputation with all the leading colleges as one of the best of all the
preparatory schools,” as shown in Figure
<a href="#fig:1876-scribners-monthly">6</a>.[3] In fact, the education
that young people received in the city’s public school system far
surpassed what was available in the outlying rural towns, known today as
the suburbs.

<iframe src="https://ontheline.github.io/otl-google-books-api/scribners-monthly-1876.html" width="100%" height="600px">
</iframe>
<p class="caption">
Image 6: Scroll [the full-screen
document](https://ontheline.github.io/otl-google-books-api/scribners-monthly-1876.html)
from *Scribner’s Monthly* in 1876, which declared Hartford as “the
richest city in the United States,” relative to its population.
Digitized by Google Books.
</p>

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[4]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[5]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[6]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum. Duis aute irure dolor in reprehenderit in
voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur
sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[7]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[8]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum..[9]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.Lorem ipsum dolor sit amet, consectetur
adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore
magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco
laboris nisi ut aliquip ex ea commodo consequat.[10]

### Third-level header non-numbered

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur.

#### Fourth-level header non-numbered

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[11]

##### Fifth-level header non-numbered

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[12]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[13]

Testing hashtag cross-reference to the [media chapter](#media)

Testing hashtag cross-reference to the [subchapter section](#subchapter)

Testing html cross-reference to the [bibliography
chapter](bibliography.html)

<!--chapter:end:2-notes-chapter.Rmd-->

Notes subchapter test
---------------------

Minor revision More text here More text here More text here More text
here More text here More text here More text here More text here More
text here More text here More text here More text here More text here
More text here More text here More text here More text here More text
here More text here More text here More text here More text here More
text here More text here More text here More text here More text here
More text here More text here.[14]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[15]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[16]

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[17]

<!--chapter:end:2.1-notes-subchapter.Rmd-->

PDF image testing
=================

Note that auto\_pdf is true in global options

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[18]

##### Static image in all editions, no interactive version

<img src="images/1937-holc-hartford-map-scan.jpg" alt="Caption for sample static image, with Markdown formatting, links, citation."  />
<p class="caption">
Image 7: Caption for sample static image, with Markdown formatting,
links, citation.
</p>

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
occaecat cupidatat non proident, sunt in culpa qui officia deserunt
mollit anim id est laborum.[19]

##### Interactive iframe in web edition (with adjusted height), static image in PDF edition, WITH auto\_pdf

<iframe src="https://ontheline.github.io/otl-redlining/" width="100%" height="400px">
</iframe>
<p class="caption">
Image 8: Caption for all versions here, with link to [full-screen
interactive map with its own
caption](https://ontheline.github.io/otl-redlining/index-caption.html),
and link to sources and the code View [map historical sources, known
issues, and the code](https://github.com/ontheline/otl-redlining/),
developed by Ilya Ilyankou and Jack Dougherty, with footnote (if I can
get it to work)
</p>

<!--chapter:end:3-pdf-image.Rmd-->

Table test
==========

Removed

<!--chapter:end:4-table.Rmd-->

Cross-references test
---------------------

removed

<!--chapter:end:5-cross-refs.Rmd-->

Bibliography
============

<!--chapter:end:9-bibliography.Rmd-->

Berends, Mark, Marisa Cannata, and Ellen Goldring, eds. *School Choice
and School Improvement*. Cambridge Mass.: Harvard Education Press, 2011.
<http://www.hepg.org/hep-home/books/school-choice-and-school-improvement>.

Cities Suburbs and Schools Project Archives, Trinity College Digital
Repository. Accessed July 15, 2019.
<https://digitalrepository.trincoll.edu/cssp_papers/>.

Clark, Charles H. “The Charter Oak City.” *Scribner’s Monthly* 13, no. 1
(November 1876): 1–21.
<https://books.google.com/books?id=2q_PAAAAMAAJ&pg=PA1#v=onepage&q&f=false>.

Dougherty, Jack. “Bridging the Gap Between Urban, Suburban, and
Educational History.” In *Rethinking the History of American Education*,
edited by William Reese and John Rury, 245–59. New York: Palgrave
MacMillan Press, 2007.
<http://digitalrepository.trincoll.edu/cssp_papers/5/>.

———. “Conflicting Questions: Why Historians and Policymakers
Miscommunicate on Urban Education.” In *Clio at the Table: Using History
to Inform and Improve Education Policy*, edited by Kenneth Wong and
Robert Rothman, 251–62. New York: Peter Lang, 2009.
<http://digitalrepository.trincoll.edu/cssp_papers/4/>.

———. “Review of ’Connecticut’s Public Schools: A History, 1650-2000’ by
Christopher Collier.” *Connecticut History* 50, no. 1 (2011): 120–22.
<http://digitalrepository.trincoll.edu/cssp_papers/41>.

Dougherty, Jack, Jeffrey Harrelson, Laura Maloney, Drew Murphy, Russell
Smith, Michael Snow, and Diane Zannoni. “School Choice in Suburbia: Test
Scores, Race, and Housing Markets.” *American Journal of Education* 115,
no. 4 (August 2009): 523–48.
<http://digitalrepository.trincoll.edu/cssp_papers/1>.

Dougherty, Jack, Jesse Wanzer, and Christina Ramsay. “Sheff V. O’Neill:
Weak Desegregation Remedies and Strong Disincentives in Connecticut,
1996-2008.” In *From the Courtroom to the Classroom: The Shifting
Landscape of School Desegregation*, edited by Claire Smrekar and Ellen
Goldring, 103–27. Cambridge, MA: Harvard Education Press, 2009.
<http://digitalrepository.trincoll.edu/cssp_papers/3/>.

On The Line Digital Archives, Connecticut Digital Archives, n.d.
<https://collections.ctdigitalarchive.org/islandora/object/120002:otl>.

Pennington, Lis, Emily Steele, and Jack Dougherty. “A Political History
of School Finance Reform in Metropolitan Hartford, Connecticut,
1945-2005.” American Educational Research Association conference paper,
April 2007. <http://digitalrepository.trincoll.edu/cssp_papers/29/>.

Sheff, Elizabeth Horton. “Oral History Interview on Sheff Vs. O’Neill.”
Cities, Suburbs, Schools Project, Trinity College Digital Repository,
July 28, 2011. <http://digitalrepository.trincoll.edu/cssp_ohistory/16>.

Tegeler, Philip, ed. *Finding Common Ground: Coordinating Housing and
Education Policy to Promote Integration*. Washington, DC: Poverty & Race
Research Action Council, 2011.
<http://www.prrac.org/pdf/HousingEducationReport-October2011.pdf>.

Wells, Amy Stuart, Bianca J. Baldridge, J. Duran, C. Grzesikowski, R.
Lofton, A. Roda, M. Warner, and T. White. “Boundary Crossing for
Diversity, Equity, and Achievement: Interdistrict School Desegregation
and Educational Opportunity.” Cambridge MA: Charles Hamilton Houston
Institute for Race and Justice, November 2009.
<http://charleshamiltonhouston.org/assets/documents/publications/Wells_BoundaryCrossing.pdf>.

Whitten, Robert Harvey. *West Hartford Zoning: Report to the Zoning
Commission on the Zoning of West Hartford*. West Hartford, Conn: Zoning
Commission, 1924.
<http://magic.lib.uconn.edu/magic_2/raster/37840/hdimg_37840_155_1924_unkn_CSL_1_p.pdf>.

[1] Elizabeth Horton Sheff, “Oral History Interview on Sheff Vs.
O’Neill” (Cities, Suburbs, Schools Project, Trinity College Digital
Repository, July 28, 2011),
<http://digitalrepository.trincoll.edu/cssp_ohistory/16>

[2] Trinity College Digital Repository Cities Suburbs and Schools
Project Archives, accessed July 15, 2019,
<https://digitalrepository.trincoll.edu/cssp_papers/>; On The Line
Digital Archives, Connecticut Digital Archives, n.d.,
<https://collections.ctdigitalarchive.org/islandora/object/120002:otl>.

[3] Charles H. Clark, “The Charter Oak City,” *Scribner’s Monthly* 13,
no. 1 (November 1876): 1–21,
<https://books.google.com/books?id=2q_PAAAAMAAJ&pg=PA1#v=onepage&q&f=false>

[4] Philip Tegeler, ed., *Finding Common Ground: Coordinating Housing
and Education Policy to Promote Integration* (Washington, DC: Poverty &
Race Research Action Council, 2011),
<http://www.prrac.org/pdf/HousingEducationReport-October2011.pdf>.

[5] Robert Harvey Whitten, *West Hartford Zoning: Report to the Zoning
Commission on the Zoning of West Hartford* (West Hartford, Conn: Zoning
Commission, 1924),
<http://magic.lib.uconn.edu/magic_2/raster/37840/hdimg_37840_155_1924_unkn_CSL_1_p.pdf>.

[6] Lis Pennington, Emily Steele, and Jack Dougherty, “A Political
History of School Finance Reform in Metropolitan Hartford, Connecticut,
1945-2005” (American Educational Research Association conference paper,
April 2007), <http://digitalrepository.trincoll.edu/cssp_papers/29/>.

[7] Jack Dougherty, “Review of ’Connecticut’s Public Schools: A History,
1650-2000’ by Christopher Collier,” *Connecticut History* 50, no. 1
(2011): 120–22, <http://digitalrepository.trincoll.edu/cssp_papers/41>.

[8] Jack Dougherty, “Conflicting Questions: Why Historians and
Policymakers Miscommunicate on Urban Education,” in *Clio at the Table:
Using History to Inform and Improve Education Policy*, ed. Kenneth Wong
and Robert Rothman (New York: Peter Lang, 2009), 251–62,
<http://digitalrepository.trincoll.edu/cssp_papers/4/>.

[9] Jack Dougherty, Jesse Wanzer, and Christina Ramsay, “Sheff V.
O’Neill: Weak Desegregation Remedies and Strong Disincentives in
Connecticut, 1996-2008,” in *From the Courtroom to the Classroom: The
Shifting Landscape of School Desegregation*, ed. Claire Smrekar and
Ellen Goldring (Cambridge, MA: Harvard Education Press, 2009), 103–27,
<http://digitalrepository.trincoll.edu/cssp_papers/3/>.

[10] Jack Dougherty, “Bridging the Gap Between Urban, Suburban, and
Educational History,” in *Rethinking the History of American Education*,
ed. William Reese and John Rury (New York: Palgrave MacMillan Press,
2007), 245–59, <http://digitalrepository.trincoll.edu/cssp_papers/5/>.

[11] Jack Dougherty et al., “School Choice in Suburbia: Test Scores,
Race, and Housing Markets,” *American Journal of Education* 115, no. 4
(August 2009): 523–48,
<http://digitalrepository.trincoll.edu/cssp_papers/1>.

[12] Amy Stuart Wells et al., “Boundary Crossing for Diversity, Equity,
and Achievement: Interdistrict School Desegregation and Educational
Opportunity” (Cambridge MA: Charles Hamilton Houston Institute for Race
and Justice, November 2009),
<http://charleshamiltonhouston.org/assets/documents/publications/Wells_BoundaryCrossing.pdf>.

[13] Mark Berends, Marisa Cannata, and Ellen Goldring, eds., *School
Choice and School Improvement* (Cambridge Mass.: Harvard Education
Press, 2011),
<http://www.hepg.org/hep-home/books/school-choice-and-school-improvement>.

[14] Pennington, Steele, and Dougherty, “A Political History of School
Finance Reform in Metropolitan Hartford, Connecticut, 1945-2005.”

[15] Dougherty, “Review of ’Connecticut’s Public Schools.”

[16] Tegeler, *Finding Common Ground*.

[17] Whitten, *West Hartford Zoning*.

[18] Tegeler, *Finding Common Ground*.

[19] Whitten, *West Hartford Zoning*.
