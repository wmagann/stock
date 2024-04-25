const express = require('express');
const MongoClient = require('mongodb').MongoClient;

const app = express();
const port = 2000;

// MongoDB connection URI
const uri = "mongodb+srv://wmagann:mvbbsk78@products.stxj7c9.mongodb.net/Stock";

// Database and collection names
const dbName = 'Stock';
const collectionName = 'PublicCompanies';

// Middleware to parse request bodies
app.use(express.urlencoded({ extended: true }));

// Serve the HTML file
app.get('/', (req, res) => {
    res.sendFile(__dirname + '/stock-get.html');
});

// Process form submission
app.get('/process', (req, res) => {
    let searchQuery = req.query.search;
    const searchType = req.query.searchType;

    // Convert search query to lowercase
    searchQuery = searchQuery.toLowerCase();

    // Connect to MongoDB
    MongoClient.connect(uri, { useNewUrlParser: true, useUnifiedTopology: true }, (err, client) => {
        if (err) {
            console.error(err);
            return res.status(500).send('Error connecting to database');
        }

        // Access the database and collection
        const db = client.db(dbName);
        const collection = db.collection(collectionName);

        // Construct the query based on search type
        let query = {};
        if (searchType === 'ticker') {
            query = { stockTicker: { $regex: new RegExp('^' + searchQuery, 'i') } };
        } else if (searchType === 'company') {
            query = { companyName: { $regex: new RegExp('^' + searchQuery, 'i') } };
        }

        // Find all documents in the collection that match the query
        collection.find(query).toArray((err, results) => {
            if (err) {
                console.error(err);
                client.close();
                return res.status(500).send('Error searching for company');
            }

            if (results.length === 0) {
                client.close();
                return res.status(404).send('No matching companies found');
            }

            // Send the prices back to the client
            let response = '';
            results.forEach((result) => {
                response += `The price for ${result.companyName} (${result.stockTicker}) is $${result.latestPrice}<br>`;
            });
            res.send(response);
            client.close();
        });
    });
});



// Start the server
app.listen(port, () => {
    console.log(`Server is running on port ${port}`);
});
