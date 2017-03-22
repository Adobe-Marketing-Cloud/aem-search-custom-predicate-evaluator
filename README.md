# Custom Predicate Evaluator for Replication Metadata Implementation

This is an AEM 6.0, 6.1, 6.2 and 6.3 reference implementation for a predicate evaluator that handles the evaluation of certain predicates, which are the defining constraints of a query.
As an example this bundle describes how to create a custom predicate evaluator that filters resources based on the replication metadata:

_cq:lastReplicated_ that stores the date of the last replication action  
_cq:lastReplicatedBy_ that stores the id of the user who triggered the last replication action  
_cq:lastReplicationAction_ that stores the last replication action (e.g. Activation, Deactivation)

## How to build

To build the bundle run in the project root directory the following command with Maven 3

    mvn clean install

If you have a running AEM instance you can build and deploy into AEM with  

    mvn clean install -PautoInstallBundle

## Testing

The goal of the ReplicationPredicateEvaluator is to support the query using the following syntax.

    path=/content    
 
    replic.by=admin
    replic.since=2013-01-01T00:00:00.000+01:00
    replic.action=Activate

First check the custom predicate evaluator is correctly installed at _http://{host}:{port}/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29_  
Then test the above query using _http://{host}:{port}/libs/cq/search/content/querydebug.html_



## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    http://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html
