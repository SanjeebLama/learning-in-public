# [Filters](https://shopify.dev/docs/api/liquid/filters)

- filters are powerful tools used to _modify the output of variables, objects, or expressions_.

- They allow you to manipulate data in various ways to achieve the desired formatting or presentation.

Syntax:

- `{{ }}`, preceded by a pipe character `|`.

```liquid
{% # product.title -> Health potion %}

{{ product.title | upcase }}
```

Here's an overview of filters in Liquid Shopify:

1. **Basic Filters**: These are fundamental filters that perform basic operations on data:

   - `capitalize`: Capitalizes the first letter of a string.
   - `downcase`: Converts a string to lowercase.
   - `upcase`: Converts a string to uppercase.
   - `escape`: Escapes special characters in a string.

2. **String Filters**: These filters are used for string manipulation:

   - `append`: Appends a string to another string.
   - `prepend`: Prepends a string to another string.
   - `remove`: Removes occurrences of a specified substring from a string.
   - `replace`: Replaces occurrences of a substring with another substring in a string.
   - `slice`: Extracts a substring from a string based on starting and ending positions.

3. **Array Filters**: These filters are used for working with arrays:

   - `join`: Joins the elements of an array into a single string using a specified delimiter.
   - `sort`: Sorts the elements of an array.
   - `reverse`: Reverses the order of elements in an array.
   - `map`: Applies a specified filter to each element of an array.
   - `compact`: Removes any nil items from an array.
   - `first`: Returns the first item in an array.
   - `where`: Filters an array to include only items with a specific property value.
   - `concat`: Concatenates (combines) two arrays.
     > The concat filter won't filter out duplicates. If you want to remove duplicates, then you need to use the uniq filter.

4. **Math Filters**: These filters perform mathematical operations:

   - `plus`: Adds a number to another number.
   - `minus`: Subtracts a number from another number.
   - `times`: Multiplies a number by another number.
   - `divided_by`: Divides a number by another number.
   - `modulo`: Returns the remainder of dividing one number by another.

5. **Date Filters**: These filters are used for working with dates and times:

   - `date`: Formats a date according to a specified format.
   - `time_tag`: Converts a time to a format suitable for HTML time elements.
   - `date_modify`: Modifies a date by adding or subtracting time intervals.

6. **Miscellaneous Filters**: These filters offer additional functionalities:

   - `default`: Sets a default value if a variable is not defined or is empty.
   - `json`: Converts a variable to JSON format.
   - `size`: Returns the size of a string, array, or object.

Filters can be chained together to perform multiple operations sequentially. For example:

```liquid
{{ product.title | upcase | prepend: "PRODUCT: " }}
```

This code snippet takes the title of a product, converts it to uppercase, and then prepends "PRODUCT: " to the beginning of the title.

Understanding and effectively using filters in Liquid Shopify can greatly enhance your ability to customize and format your store's content and presentation according to your specific requirements.
