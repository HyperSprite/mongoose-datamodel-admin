#Mongoose Data Model Admin

----------
The Mongoose Data Model Admin is a tool for creating and managing mongoose schema. You can use it for a new project in a data first model or you can use it to document an existing project to keep everyone and everything on the same page.

I'll be the first to tell you I am no expert at this. I built this tool because I wanted one to work the way I thought about schema and data usage.

While I could build the View with EJS or Handlebars, which I already know, I will be using React and Redux for the View once I get to that point because I want to build something I care about in React and this seems like a good greenfield place to start.

----------
##Setup
We can start with a vanilla Express app. As with most dev projects, we are going to skip the user access setup. This is the first building block of our app, and so is being built before user access exists. We can use it to design our user model and then instantiate routes and access models with that.

>I know, you are probably rolling your eyes, that is what everyone says and I have yet to find a great way to protect the rest of my app and you are not helping. Sorry, but that is beyond the scope of this setup, maybe I'll make a User Admin thing in the future, but right now that is not my focus.

//write something about how to set it up once you have something to setup. I am sure it will include git clone and npm install....

--------

 The first thing we do is make a datamodel collection schema. Each item will be a field in one of our schemas. Each field will be documented with the following fields:

>Have you ever noticed how hard it is to document something that you are self describing. It always sounds like a big circle.

 - dmSchemaName - String : Schema Name, is what will be exported from the schema js file and required by our handlers for collection access.
 - dmCollectionName - String : Collection Name, is the name as it appears in Mongodb.
 - dmFieldName - String : Field Name, as used in the schema.
 - dmDisplayName - String : Display Name, as users see it.
 - dmType - String : What Type is this, String, Number, Array....
 - dmIndexed - Boolean : Is this indexed.
 - dmUnique - Boolean : Is this unique.
 - dmRequired - Boolean : Is this required.
 - dmMin - Number: Min value or length
 - dmMax - Number: Max value or length
 - dmOptions - Array of Sub Documents : Used for constrained value fields, should be an array of objects. e.g. [{name: foo, value: 1}, {name:bar, value: 2}. Consider carefully if a field will contain a readable value or a reference to a value. Both have their advantages and disadvantages. For instance, if we use a reference value, we will need to lookup the real value every time we need to display that value. Also, what is the likely hood of that value needing to change?
 - dmDescription - String : Explain what this is for and why it exists to devs.
 - dmHelp - String : Explain what this is for and how to use it to end users.
 - dmReff - Array : is this field referenced by another field or schema.
 - dmLookup - Array : is this field looked up by another field or schema.
 - dmVirtuals - Array : is this field used in schema virtuals.
 - dmCharsAccepted - String : What characters are allowed (this could be a regex string)
 - dmAccess - Array of Sub Documents : What group or user has access to edit this field in the collection.

>Note: Some fields may remain empty but careful thought should be given before doing so.

--------

Once we define the schema for our schema definition we can go to the view to get a copy of our schema as it would be written in the model.

-----
###Routes

Using typical Rest routes:

 - get datamodel/ : datamodel.find() - returns all field definitions with all fields
 - get datamodel/new : form only - returns form to make new field definition
 - post datamodel/ datamodel.create - post a new field definition
 - get datamodel/:id datamodel.findById - returns one field definition
 - get datamodel/:id/edit datamodel. findById - returns edit view of field definition
 - put datamodel/:id datamodel.findByIdAndUpdate - updates a field definition
 - delete datamodel/:id datamodel.findByIdAndRemove - delete a field definition


Other Routes:

 - datamodel/model/:dmSchemaName - Displays the schema based on the fields.
 - help/fields - displays the dmHelp with Display Name and user help






