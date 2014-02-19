CoreDataMigrations-DefaultMigration
===================================

Demo 4 project from my Core Data Migrations talk at San Antonio iOS Meetup.

The demo is run the same as Demo 2. Differences include addition of mapping models and a custom TopicToTopic migration policy.

In this demo, the use of these mappings and policy code accomplish the following:
* Model1->Model2. We set the timeBudget to be 20% of the topic content length…vs defaulting to 5 min. This is done using a value expression in the mapping model.
* Model3->Model4. The conversion of timeBudget to seconds from minutes works using a value expression in the mapping model.
* Model4->Model5. Presenter data is successfully split from the Topic and a Member entity populated as needed. Relationships between Topic and Member are created correctly.

Script
------
1. Delete app and data in simulator and run with Model1 to get baseline database populated
2. Show that we have 5 models in our Versioned Model file now.
3. Show the options in RootViewController to enable Automatic Lightweight Migration.
4. Set current model to Model2. Show that it contains new timeBudget attribute with default of 5 min. 
5. Run the app and then open the store. You will see a 5 min default timeBudget in each Topic.
6. Quit app and set current model to Model3. Renamed *content* to *title* on Topic using Renaming Identifier. 
7. Run app and open store. Show that we’ve lost our Topic content. Need to uncomment code in CDMTopicsViewController.m in cellForRowAtIndexPath to use new title property to set cell content.
8. Run and show topic content now showing.
9. Quit app and set Model4 as current model. This is the minutes to seconds conversion…using Hash Modifier.
10. Run app and open store. Migration occurs, but data is still in minutes. This is limit of Lightweight migration.
11. Quit app and set model to Model5. Run app and open store.
12. Migration occurs and schema is changed, but we’ve lost the presenter information in our new database. This is another limit of Lightweight migration.
12. Demo ends.
