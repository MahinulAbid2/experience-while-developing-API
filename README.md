# experience-while-developing-API
* A good question should be how to peoperly name the sub function.

<br>
<br>

# Alternative of AWS S3 since it's not free
![image](https://github.com/MahinulAbid2/experience-while-developing-API/assets/70069009/d877cf96-9458-47a7-831e-4f060b78fe5d)
![image](https://github.com/MahinulAbid2/experience-while-developing-API/assets/70069009/c9fcea53-fec0-42f3-b487-2e8e8e7e9b99)

<br>
<br>

# falsy values 
```javascript
if (!data) {
   // ...
}
```
* when you use the `!` (logical NOT) operator, it coerces the operand to a boolean value and then negates it. If the operand is a falsy value (such as `null`, `undefined`, `false`, `0`, `NaN`, or an `empty string ''`), then applying ! will result in true. If the operand is a truthy value, applying ! will result in false.


<br>
<br>

# Error Types
### Duplicate Key Error
* what is duplicate key error index? <br> The E11000 duplicate key error index is an error that occurs when we try to insert a document into a MongoDB collection with a unique index, and the index already contains a document with the same value for the unique key. In mongoose Schema -- when I specify a field with `unique key`, and when user enters a `non-unique value` this gives an `duplicate key error`.
```javascript
 const handleDuplicateFieldsDB = err => {
  const value = err.errmsg.match(/(["'])(\\?.)*?\1/)[0];

  const message = `Duplicate field value: ${value}. Please use another value!`;
  return new AppError(message, 400);
};

// when to call it
if (error.code === 11000) error = handleDuplicateFieldsDB(error);
```

<br>
<br>

### Cast Error
Mongoose's `findById` method casts the `id` parameter to the type of the model's `_id` field so that it can properly query for the matching doc. 
* CastError : Mongoose could not convert a value to the type defined in the schema path. 
* If you set a type in `string` but what the data was a number, MAYBE this is when I will get a `cast Error`
```javascript

// how to catch the cast error
if (error.name === 'CastError') error = handleCastErrorDB(error);

// what to do to handle cast error
const handleCastErrorDB = err => {
  const message = `Invalid ${err.path}: ${err.value}.`;
  return new AppError(message, 400);
};

```




