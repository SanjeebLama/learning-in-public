# Liquid

- a template language created by Shopify and written in Ruby

- It is the backbone of Shopify themes and is used to load dynamic content on storefronts.

- Liquid has been in production use at Shopify since 2006 and is now used by many other hosted web applications.

- Liquid uses a _combination of objects, tags, and filters_ inside template files to display dynamic content.

  - **Objects** 📦 These are like little boxes that hold all the information about different parts of your store, like products, collections, and customers.

  - **Tags** 🏷️ These are special labels or commands that tell Liquid what to do with the objects. For example, you can use tags to loop through all the products in a collection and display them on a page.

  - **Filters** ⚙️ These are like superpowers that let you modify or format the content in the objects. For example, you can use a filter to make the product titles appear in all capital letters or to show the product price with a currency symbol.

## Q. What is a template language?

a template language is like a blueprint or a fill-in-the-blank form for creating web pages or documents. It lets you make a basic structure for something, and then fill in specific details later on.

# Basics

### Object Handles

- an object handle is like a _unique name or identifier for different types of objects in your store_.

- It's a way to refer to and access specific objects and their properties.

For example, some common object handles in Shopify are:

- `product`: This handle represents an individual product in your store. You can use it to access properties like `product.title`, `product.price`, `product.description`, etc.

- `collection`: This handle refers to a collection of products. You can use it to loop through all the products in a collection or access the collection's properties like `collection.title`, `collection.description`, etc.

- `customer`: This handle represents a customer account. You can use it to access customer details like `customer.first_name`, `customer.last_name`, `customer.email`, etc.

- `cart`: This handle refers to the customer's shopping cart. You can use it to access cart properties like `cart.total_price`, `cart.item_count`, or loop through `cart.items` to display the items in the cart.

These object handles act like keys that unlock access to different types of data and functionality in your Shopify store. You use them in your Liquid code to fetch and display relevant information on your store's pages.

For example, on a product page, you might use the `product` handle to display the product's title, price, and description:

```liquid
<h1>{{ product.title }}</h1>
<p>{{ product.price | money }}</p>
<div>{{ product.description }}</div>
```

Similarly, on a collection page, you could use the `collection` handle to loop through all the products in that collection:

```liquid
{% for product in collection.products %}
  <div>{{ product.title }}</div>
{% endfor %}
```

Object handles make it easier to organize and access different types of data in your Shopify store, without having to write complex code. They provide a simple and structured way to interact with your store's data using Liquid templating.

## Creating and modifying handles

Handles are unique identifiers for resources like products, collections, etc. They are auto-generated based on the resource title, following these rules:

- All lowercase
- Spaces and special characters replaced with hyphens
- Duplicate titles get incremented handles (e.g. product-1)

You can't directly create handles, but you can access them using the `handle` property (e.g. `product.handle`).

Handles can be modified manually in the Shopify admin, but changing the resource title won't update the handle automatically.

When referencing resources by handle, use dot notation (e.g. `product.variants`) or square brackets with the handle (e.g. `product['variants']`).

If modifying a handle, be sure to update any references to the old handle in your Liquid code.

In essence, handles are auto-generated unique identifiers that you can access and reference, but not directly create or modify without updating your Liquid code accordingly.

## Operators

| Operator | Function                                |
| -------- | --------------------------------------- |
| ==       | equals                                  |
| !=       | does not equal                          |
| >        | greater than                            |
| <        | less than                               |
| >=       | greater than or equal to                |
| <=       | less than or equal to                   |
| or       | Condition A or Condition B              |
| and      | Condition A and Condition B             |
| contains | Checks for strings in strings or arrays |

## contains

- to check for the presence of a string within an array, or another string.

- You can’t use contains to check for an object in an array of objects.

```liquid
{% if product.tags contains 'healing' %}
  This potion contains restorative properties.
{% endif %}
```

## Order of operations

In Liquid, when you use multiple operators within a single tag or output, they are evaluated from right to left. This order cannot be changed.

For example, let's say you have the following Liquid code:

```liquid
{{ 3 + 2 * 5 }}
```

In this case, the multiplication (`*`) will be evaluated first, and then the addition (`+`). So the output would be:

```
13
```

Now, let's look at another example:

```liquid
{{ 3 * 2 + 4 / 2 }}
```

Here, the order of operations would be:

1. `4 / 2` (which is 2)
2. `3 * 2` (which is 6)
3. `6 + 2` (which is 8)

So the output would be:

```
8
```

It's important to note that you cannot use parentheses `()` to change the order of operations in Liquid, as they are not valid characters within Liquid tags. If you try to include parentheses, your tag won't be rendered.

```liquid
{% unless true and false and false or true %}
  This evaluates to false, since Liquid checks tags like this:

  true and (false and (false or true))
  true and (false and true)
  true and false
  false
{% endunless %}
```

<details>
    <summary> Explanation </summary>

1. The code starts with an `unless` tag, which is used to _render the content inside the block if the condition is false._

2. The condition inside the `unless` tag is: `true and false and false or true`

3. In Liquid, operators are evaluated from right to left, as per the order of operations.

4. So, the expression is evaluated as follows:

   - `false or true` is evaluated first, which is `true`
   - Then, `false and true` is evaluated, which is `false`
   - Finally, `true and false` is evaluated, which is `false`

5. This means that the entire expression `true and false and false or true` evaluates to `false`.

6. Since the `unless` tag is used, and the condition is `false`, the content inside the block will be rendered.

In summary, this code demonstrates how Liquid evaluates logical expressions from right to left, and how the `unless` tag works. The content inside the `unless` block is rendered because the condition `true and false and false or true` evaluates to `false`.

</details>

# Data Types

In Liquid, there are six data types that you can work with. Here's an overview of each type with examples:

1. **String**

   - A sequence of characters enclosed in single or double quotes.
   - Example: `'Hello, world!'`, `"This is a string"`
   - You can check whether a string is empty with the `blank` object.

2. **Number**

   - Can be an integer or a floating-point number.
   - Example: `42`, `3.14`

3. **Boolean**

   - Represents a logical value of either `true` or `false`.
   - Example: `true`, `false`

4. **Nil**

   - Represents a null or undefined value.
   - Tags or outputs that return nil don't print anything to the page.
   - They are also treated as false.
   - A string with the characters “nil” is not treated the same as nil.
   - Example: `nil`

5. **Array**

   - An ordered collection of values, which can be of _different types_.
   - To access all of the items in an array, you can loop through each item in the array using a for or tablerow tag.
   - Example: `['apple', 'banana', 'cherry']`, `[1, 2.5, false]`

6. **Object**

   - An unordered collection of key-value pairs.
   - `empty`
     An empty object is returned if you try to access an object that is defined, but has no value.

     You can compare an object with `empty` to check whether an object exists before you access any of its attributes.

   - Example: `{ 'name': 'John Doe', 'age': 30 }`

You can work with these data types in Liquid by using variables, filters, and tags. For example:

```liquid
{% assign name = 'John Doe' %}
{% assign age = 30 %}
{% assign is_member = true %}
{% assign scores = [85, 92, 78] %}

<h1>{{ name }}</h1>
<p>Age: {{ age }}</p>
<p>Is Member: {{ is_member }}</p>
<p>Latest Score: {{ scores.last }}</p>
```

Additionally, you can create objects and access their properties:

```liquid
{% assign person = { 'name': 'Jane Smith', 'email': 'jane@example.com' } %}
<p>Name: {{ person.name }}</p>
<p>Email: {{ person.email }}</p>
```

Understanding and working with these data types is essential for effective Liquid templating in Shopify.

# Truthy and Falsy -- Verify

Here's the table representing truthy and falsy values in Liquid Shopify:

| Value        | Truthy | Falsy |
| ------------ | ------ | ----- |
| true         | ✓      |       |
| false        |        | ✓     |
| nil          |        | ✓     |
| empty string | ✓      |       |
| 0            | ✓      |       |
| integer      | ✓      |       |
| float        | ✓      |       |
| array        | ✓      |       |
| empty array  | ✓      |       |
| page         | ✓      |       |
| empty object | ✓      |       |

In Liquid Shopify, values that are considered truthy include `true`, non-zero integers, non-zero floats, non-empty arrays, and non-empty objects like `page`. Values that are considered falsy include `false`, `nil`, empty strings, `0`, empty arrays, and empty objects.

# Whitespace control - hyphen operators

The hyphens (-) in Liquid code are used for controlling whitespace.

- By including hyphens in your Liquid tag, you can strip any whitespace that your Liquid generates when rendered.

- If you want to remove whitespace on only one side of the Liquid tag, then you can include the hyphen on either the opening or closing tag.

**Example:**

```liquid
{% for i in (1..5) -%}
  {%- if i == 4 -%}
    {% continue %}
  {%- else -%}
    {{ i }}
  {%- endif -%}
{%- endfor %}
```

<details>
<summary> Example explanation </summary>

Here's how the hyphens are used in the provided code:

{% for i in (1..5) -%}: The hyphen (-) after the opening {% tag removes any leading whitespace that might be generated by the for loop.

-%}: The hyphen (-) before the closing %} tag removes any trailing whitespace that might be generated by the for loop.

{%- if i == 4 -%}: The hyphens (-) here ensure that any whitespace immediately following the {% and preceding the -%} is removed. This helps to maintain a clean output without extra whitespace.

-%}: Similarly, the hyphen (-) here ensures that any whitespace immediately following the {% and preceding the -%} is removed.

</details>
