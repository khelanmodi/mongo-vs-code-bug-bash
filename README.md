# mongo-vs-code-bug-bash

Here’s a step-by-step outline for the testing scenarios you provided:

### 1. **Create a New Database and Collection Using the Extension**
   - **Scenario**: Use the MongoDB extension in Azure to create a new database named `RestaurantDB` and a collection named `Restaurants`.
   - **Action**: 
     1. Open the MongoDB extension.
     2. Create `RestaurantDB`.
     3. Add a collection `Restaurants`.
     4. Insert sample data into the `Restaurants` collection.

### 2. **Find All Restaurants That Have `is_open = 1`**
   - **Scenario**: Query to fetch all open restaurants.
   - **Action**:
     ```javascript
     db.Restaurants.find({ "is_open": 1 })
     ```
   - **Expected Result**: A list of open restaurants.

### 3. **Using the Table View, Give Monday's Working Hours for Open Restaurants**
   - **Scenario**: Display open restaurants’ names and their Monday working hours in a table view.
   - **Action**: 
     ```javascript
     db.Restaurants.find(
       { "is_open": 1 },
       { "name": 1, "hours.Monday": 1, "_id": 0 }
     )
     ```
   - **Task**: Capture a screenshot of the table view showing names and Monday hours.

### 4. **Edit the Time for a Specific Entry and Share the Screenshot**
   - **Scenario**: Modify the Monday working hours for one of the open restaurants.
   - **Action**: 
     ```javascript
     db.Restaurants.updateOne(
       { "name": "Specific Restaurant Name" },
       { $set: { "hours.Monday": "10:0-22:0" } }
     )
     ```
   - **Task**: Capture and share a screenshot of the updated entry in the table view.

### 5. **Delete One Entry That Has `is_open = 0`**
   - **Scenario**: Remove a restaurant that is closed.
   - **Action**:
     ```javascript
     db.Restaurants.deleteOne({ "is_open": 0 })
     ```
   - **Expected Result**: Confirmation of deletion.

### 6. **Add a New Entry**
   - **Scenario**: Insert a new restaurant entry into the collection.
   - **Action**:
     ```javascript
     db.Restaurants.insertOne({
       "business_id": "abc123def456ghi789jkl",
       "name": "Golden Gate Catering Services",
       "address": "123 Culinary Ave",
       "city": "San Francisco",
       "state": "CA",
       "stars": 4.5,
       "review_count": 15,
       "is_open": 1,
       "categories": "Caterers, Event Planning & Services, Food, Professional Services",
       "hours": {
         "Monday": "8:0-20:0",
         "Tuesday": "8:0-20:0",
         "Wednesday": "8:0-20:0",
         "Thursday": "8:0-20:0",
         "Friday": "8:0-20:0",
         "Saturday": "10:0-18:0",
         "Sunday": "Closed"
       },
       "location": {
         "type": "Point",
         "coordinates": [ -122.419416, 37.774929 ]
       },
       "description": "### Business Summary\n\nGolden Gate Catering Services, based in San Francisco, CA, is renowned for delivering exquisite culinary experiences for a variety of events. ..."
     })
     ```
   - **Expected Result**: The new entry should appear in the collection.

### 7. **Export Query Results with `is_open = 0`**
   - **Scenario**: Export all documents where `is_open = 0`.
   - **Action**:
     ```javascript
     db.Restaurants.find({ "is_open": 0 }).toArray()
     ```
   - **Task**: Export the results to a JSON file and count the number of documents in the file.
   - **Expected Result**: A new file containing all documents with `is_open = 0`, with a document count summary.

---

Once you perform these actions, you can capture screenshots at the necessary steps and provide a summary of the number of documents exported in the last step.
