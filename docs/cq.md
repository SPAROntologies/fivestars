## Competency Questions

FiveStars can be used for answering several questions related to the main characteristics of online journal articles.
In the following subsections, some of them are introduced together with their respective SPARQL queries. 

The prefixes that are used in all the SPARQL queries provided below are defined as follows:

    PREFIX fivestars: <http://purl.org/spar/fivestars/>

### CQ1

What is the overall five-star rating and associated evaluation comment for a given resource?

    SELECT ?resource ?overallRating ?comment
    WHERE {
        ?resource fivestars:hasOverallFiveStarsRating ?overallRating .
        OPTIONAL { ?resource fivestars:overallFiveStarsRatingComment ?comment . }
    }

### CQ2

What is the peer review rating and its explanatory comment for a resource?

    SELECT ?resource ?peerReviewRating ?comment
    WHERE {
        ?resource fivestars:hasPeerReviewRating ?peerReviewRating .
        OPTIONAL { ?resource fivestars:peerReviewRatingComment ?comment . }
    }

### CQ3

What is the open access rating and its justification for a resource?

    SELECT ?resource ?openAccessRating ?comment
    WHERE {
        ?resource fivestars:hasOpenAccessRating ?openAccessRating .
        OPTIONAL { ?resource fivestars:openAccessRatingComment ?comment . }
    }

### CQ4

What are the content enhancement and dataset availability ratings for a resource?

    SELECT ?resource ?enhancedContentRating ?enhancedContentComment ?datasetsRating
    WHERE {
        ?resource fivestars:hasEnhancedContentRating ?enhancedContentRating ;
            fivestars:hasAvailableDatasetsRating ?datasetsRating .
        OPTIONAL { ?resource fivestars:enhancedContentRatingComment ?enhancedContentComment . }
    }

### CQ5

What is the complete five-star dimensional breakdown (peer review, open access, enhanced content, available datasets, and machine-readable metadata) for a resource?

    SELECT ?resource ?peerReview ?openAccess ?enhancedContent ?datasets ?metadata ?overall
    WHERE {
    ?resource fivestars:hasPeerReviewRating ?peerReview ;
        fivestars:hasOpenAccessRating ?openAccess ;
        fivestars:hasEnhancedContentRating ?enhancedContent ;
        fivestars:hasAvailableDatasetsRating ?datasets ;
        fivestars:hasMachine-readableMetadataRating ?metadata ;
        fivestars:hasOverallFiveStarsRating ?overall .
    }