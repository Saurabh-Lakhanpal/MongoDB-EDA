# MongoDB-miniProject

### Part 1: Import Data from an API
Collect data from the Metropolitan Museum of Art API and update the database.

  - Connect to the Database
    - Import your dependencies: MongoClient from pymongo, pprint from pprint, json, and requests.
    - Create an instance of MongoClient.
    - Assign the met database to a variable called `db`.
    - Assign the artifacts collection to a variable called `artifacts`.

  - Collect the Data
    - A list of ObjectIDs from the Met's API where the departmentId is 5 and the query string is "[cave](https://collectionapi.metmuseum.org/public/collection/v1/search?departmentId=5&q=cave).
    - Run the code provided to extract the data from the Met's API about each of the artifacts in the `cave_ids` list.
      
  - Update the Database
    - Write code to check the database to see if an artifact is already in the collection.
    - If it's not, then add it to the database.
    - Combine teh code to loop through your results and only add the artifacts that are not yet in the collection.
      - Choose just one item from the returned data and set it to a variable called `item_to_add`. Use the `returned_data_list` and square bracket notation to select a single item from the list.
      - Pretty print `item_to_add`.
      - Using the `objectID` from `item_to_add`, write a query to check if the item already exists in the artifacts collection.
      - Using the above query, write an `if` statement that checks if the result equals `None`.
      - Inside your `if` statement:
          - Use `insert_one` to add `item_to_add` to the artifacts collection.
          - Print out the `objectID` when it is added to the collection.
      - Combine the above steps to loop through the whole list of data contained in `returned_data_list` only adding to the collection when the artifact does not yet exist in the database. Follow these steps:
          - Loop through `returned_data_list`.
          - Save the data from the list item to the `item_to_add` variable.
          - Check if the artifact already exists in the collection.
      - Inside your `if` statement:
          - Use `insert_one` to add `item_to_add` to the artifacts collection.
          - Print out the `objectID` when it is added to the collection.
       
### Part 2: Aggregation and Analysis
Building a more complex query and another aggregation pipeline, then normalizing the resulting DataFrame.

* Run the first two blocks of code to import your dependencies, create an instance of MongoClient, and assign the database and collection to variables.

* Write a query that:

    * Uses `find()` to find documents about artifacts that come from the "Maya" culture and returns the following fields: `accessionNumber`, `accessionYear`, `classification`, `country`, `department`, `measurements.elementMeasurements.Height`, `measurements.elementMeasurements.Width`, `measurements.elementMeasurements.Depth`, `medium`, `title`,`objectURL`.

    * Uses `sort()` to sort by the artifact's height.

    * Uses `limit()` to limit the number of results to 5.

* Convert the results to a Pandas DataFrame and then display the DataFrame.

* Build an aggregation pipeline that:

    * Matches:

        * Artifacts that have a width greater than or equal to 10cm and less than 50cm

        * Artifacts that have a height greater than or equal to 20cm and less than 60cm

        * Artifacts that have "Sculpture" as part of their classification

    * Counts the artifacts and groups by: classification and then culture

        **Hint:** Set `_id` to a list or a dictionary of the fields that are being grouped on. If you use a dictionary, you will also need to assign names (or keys) for the fields you are selecting.

    * Sorts by count in descending order

* Pretty print the first 10 results of the aggregation pipeline.

* Write code that will extract the fields from `_id` from the aggregation pipeline to create a Pandas DataFrame that will include the following columns: classification, culture, number of artifacts. If necessary, rename and reorder the columns to match.

    > **Note:** There are multiple ways to do this, but the easiest way is to use `pd.json_normalize()`. If you need help using this new Pandas method, [check out the documentation](https://pandas.pydata.org/docs/reference/api/pandas.json_normalize.html).

## Reference

[The Metropolitan Museum of Art](https://www.metmuseum.org/) (2022). The Metropolitan Museum of Art Collection API <https://metmuseum.github.io/>. Licensed under the [Creative Commons 0 License](https://creativecommons.org/publicdomain/zero/1.0/)

Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".

---

© 2022 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.


## Reference

[The Metropolitan Museum of Art](https://www.metmuseum.org/) (2022). The Metropolitan Museum of Art Collection API <https://metmuseum.github.io/>. Licensed under the [Creative Commons 0 License](https://creativecommons.org/publicdomain/zero/1.0/)
