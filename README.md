# MongoDB VS Code Bug Bash

## Setup Instructions

### 1. **Install the Azure Cosmos DB for MongoDB vCore Extension**
Ensure you have the **Azure Cosmos DB for MongoDB vCore** extension installed in your Visual Studio Code environment. This extension is crucial for managing and interacting with your MongoDB vCore clusters seamlessly.

### 2. **Sign In and Select Your Azure Subscription**
After signing in to Azure, choose the subscription associated with your MongoDB vCore cluster. This step links your VS Code environment with your Azure resources.

### 3. **Explore Your Resources in the Azure Tree View**
Navigate to the **Azure Resources** section in VS Code. Locate the item labeled **Azure Cosmos DB for MongoDB (vCore)** and expand it to reveal your available clusters and databases.

### 4. **Select and Access Your MongoDB vCore Cluster**
Identify your cluster in the expanded tree view and select it. This will open the details and management options for your cluster.

### 5. **Authenticate with Your Admin Password**
When prompted, enter the admin password for your MongoDB vCore cluster. This step is necessary to authenticate your session and securely manage your database.

---

## Bugs/ Feedback
Kindly report any bugs [here](https://msdata.visualstudio.com/ba574a88-a171-48e0-8fcb-5fef6d23739c/_workitems/create/Bug?templateId=719fd0fc-f4ea-48ba-8be9-cfe2ab3061d1&ownerId=6ab390ff-a326-49d7-8722-b92a14912596).

---
## Testing Scenarios
### 1. **Create a New Database and Collection Using the Extension**
   - **Scenario**: Use the MongoDB extension in Azure to create a new database named `RestaurantDB` and a collection named `Restaurants`.
   - **Action**: 
     1. Open the MongoDB extension.
     2. Create `RestaurantDB`.
     3. Add a collection named `Restaurants`.
     4. Insert sample data into the `Restaurants` collection. [Data](https://github.com/khelanmodi/mongo-vs-code-bug-bash/blob/main/business_demo.json) can be found in this repo. 

### 2. **Find All Restaurants That Have `is_open = 1`**
   - **Scenario**: Query to fetch all open restaurants.
   - **Action**: Enter the following command in the Filter textbox: 
     ```javascript
     { "is_open": 1 }
     ```
   - **Expected Result**: A list of open restaurants.

### 3. **Using the Table View, Give Monday's Working Hours for Open Restaurants**
   - **Scenario**: Display the names of open restaurants and their Monday working hours in a table view.
   - **Action**: You can filter open restaurants with the following command: 
     ```javascript
     { "is_open": 1 }
     ```
   - **Task**: Capture a screenshot of the table view showing the names and Monday hours. You can view the hours by double-clicking on the hours of operation field. To return to the root level, click the Root level button at the bottom left of the screen.

### 4. **Edit the Time for a Specific Entry and Share the Screenshot**
   - **Scenario**: Modify the Monday working hours for one of the open restaurants.
   - **Action**: Update the entry using this filter:
     ```javascript
     { "name": "Shalhoob's Funk Zone Patio" }
     ```
   - **Task**: Capture and share a screenshot of the updated entry in the table view, with the new name "Cosmic Restaurant."

### 5. **Delete One Entry That Has `is_open = 0`**
   - **Scenario**: Remove a closed restaurant named "Minnow Cafe."
   - **Action**: Use the following command to find the entry:
     ```javascript
     { "is_open": 0 }
     ```
   - **Expected Result**: Confirmation of deletion.

### 6. **Add a New Entry**
   - **Scenario**: Insert a new restaurant entry into the collection.
   - **Action**:
     ```javascript
     {
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
     }
     ```
   - **Expected Result**: The new entry should appear in the collection.

### 7. **Export Query Results with `is_open = 0`**
   - **Scenario**: Export all documents where `is_open = 0`.
   - **Action**: Use the following command to filter the results:
     ```javascript
     { "is_open": 0 }
     ```
   - **Task**: Export the results to a JSON file and count the number of documents in the file.
   - **Expected Result**: A new file containing all documents with `is_open = 0`, along with a document count summary.
