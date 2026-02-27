# Document your edge case here
- To get marks for this section you will need to explain to your tutor:
1) The edge case you identified
`\n`
When the `/stats` endpoint is called while there are no students stored in the database.
Without handling this case, calculating statistics would cause errors such as:

Division by zero when calculating the average (runtime error)
Calling `min()` or `max()` on an empty list (value error)

2) How you have accounted for this in your implementation
`\n`
In my implementation, this case is explicitly checked:
```python
if not students:
    return jsonify({
        "count": 0,
        "average": 0,
        "min": 0,
        "max": 0
    }), 200
```
The endpoint therefore still returns a consistent response structure and frontend applications can safely display statistics without additional error handling. Ensures API behaves predictably even when the DB contains no data.