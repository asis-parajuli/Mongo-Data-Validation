# Mongo-Data-Validation
Build-in Validators, Custom Validators, Async Validators and validation errors

* Callback custom validation approach
```
validate:{
  isAsync: {
    validator: function(v, callback){
      setTimeout(() => {
        const result = c && v.length > 0;
        callback(result)
      }, 4000)
    }
  }
}
```
* The above approach is depreciated and promise should be used as shown below
```
validate: {
 validator: (v) => Promise.resolve(v && v.length > 0),
 message: "A course must have a tag.",
},
```    

* And connection to mongodb should use useNewUrlParser: true, useUnifiedTopology: true, useFindAndModify: false, as belows
```
mongoose
  .connect("mongodb://localhost/playground", {
    useNewUrlParser: true,
    useUnifiedTopology: true,
    useFindAndModify: false,
  })

  .then(() => console.log("Connected to MondoDb..."))
  .catch((err) => console.error("Could not connect to MondoDb..", err));

```

* Here is the document structure in MongoDB Compass
![Alt text](mongodb-compass-screenshot.png "Mongodb Compass")
