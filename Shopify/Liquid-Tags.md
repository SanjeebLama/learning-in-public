# Tags

> used to define logic that tells templates what to do.

- These are special labels or commands that tell Liquid what to do with the objects.

- For example, you can use tags to loop through all the products in a collection and display them on a page.

### Usage

- Tags are enclosed within curly brace percentage delimiters `{% %}`.
- Nesting multiple tags within one set of delimiters is possible using the `liquid` tag.

#### Tags with Parameters

- Certain tags accept parameters, which can be required or optional.
- For instance, the `for` tag can accept parameters like `limit` to exit a loop at a specific index.

## A. Conditional Tags

### if

Syntax:

```liquid
{% if condition %}
   // Code block to execute if the condition is true
{% endif %}
```

### elsif

Syntax:

```liquid
{% elsif condition %}
   // Code block to execute if the previous condition is false and this condition is true
{% endelsif %}
```

### else

Syntax:

```liquid
{% else %}
   // Code block to execute if none of the preceding conditions are true
{% endelse %}
```

- The `else` tag can be used with tags such as `case`, `if`, and `unless`.

### unless

- Renders an expression unless a specific condition is true.
- Similar to the `if` tag, you can use `elsif` to add more conditions to an `unless` tag.

Syntax:

```liquid
{% unless condition %}
   // Code block to execute if the condition is false
{% endunless %}
```

### case

- Renders a specific expression depending on the value of a specific variable.

Syntax:

```liquid
{% case variable %}
{% when first_value %}
   // Code block to execute if the variable's value matches first_value
{% when second_value %}
   // Code block to execute if the variable's value matches second_value
{% else %}
   // Code block to execute if the variable's value has no match
{% endcase %}
```

## B. [HTML tags](https://shopify.dev/docs/api/liquid/tags/html-tags)

HTML tags render HTML elements using Shopify-specific attributes.

### A. [Forms](https://shopify.dev/docs/api/liquid/tags/form)

Generates an HTML `<form>` tag, including any required `<input>` tags to submit the form to a specific endpoint.

Because there are many different form types available in Shopify themes, the form tag requires a type. Depending on the form type, an additional parameter might be required.

### B. [styles](https://shopify.dev/docs/api/liquid/tags/style)

Generates an HTML `<style>` tag with an attribute of data-shopify.

```liquid
{% style %}
  CSS_rules
{% endstyle %}
```

```liquid
{% style %}
  .h1 {
    color: {{ settings.colors_accent_1 }};
  }
{% endstyle %}
```

## C. Iteration Tags

repeatedly run blocks of code.

### for

- Renders an expression for every item in an array.

- You can do a **maximum of 50 iterations** with a for loop. If you need to iterate over more than 50 items, then use the _paginate tag to split the items_ over multiple pages.

- Every for loop has an associated **forloop object** with information about the loop.

```liquid
{% for variable in array %}
  expression
{% endfor %}
```

#### Parameters:

**Limit**

- limit the number of iterations

```liquid
{% for variable in array limit: number %}
  expression
{% endfor %}
```

**offset**

- You can specify a 1-based index to start iterating at using the offset parameter.

```liquid
{% for product in collection.products offset: 2 -%}
  {{ product.title }}
{%- endfor %}
```

**range**

- you can specify a numeric range to iterate over.

```liquid
{% for variable in (number..number) %}
  expression
{% endfor %}
```

```liquid
% for i in (1..3) -%}
  {{ i }}
{%- endfor %}

{%- assign lower_limit = 2 -%}
{%- assign upper_limit = 4 -%}

{% for i in (lower_limit..upper_limit) -%}
  {{ i }}
{%- endfor %}
```

Output

```
1
2
3

2
3
4
```

**reversed**

- You can iterate in reverse order using the reversed parameter.

```liquid
{% for variable in array reversed %}
  expression
{% endfor %}
```

### else

- Allows you to specify a default expression to execute when a for loop has zero length.

```liquid
{% for variable in array %}
  first_expression
{% else %}
  second_expression
{% endfor %}
```

### break

- stops a for loop from iterating
- {% break %}

```liquid
{% for i in (1..5) -%}
  {%- if i == 4 -%}
    {% break %}
  {%- else -%}
    {{ i }}
  {%- endif -%}
{%- endfor %}
```

Output:

```
1
2
3
```

### continue

Causes a for loop to skip to the next iteration.

`{% continue %}`

### cycle

Loops through a group of strings and outputs them one at a time for each iteration of a for loop.

- The cycle tag must be used inside a for loop.

Syntax:
`{% cycle string, string, ... %}`

- Use the cycle tag to output text in a predictable pattern. For example, to apply odd/even classes to rows in a table.

Example:

```template
{% for i in (1..4) -%}
  {% cycle 'one', 'two', 'three' %}
{%- endfor %}

Output:
one
two
three
one
```

**NOTE**

When the cycle tag is used in Liquid, it starts by outputting the first value in the sequence provided. Then, each time the cycle tag is encountered again, it moves to the next value in the sequence. If it reaches the end of the sequence, it starts over from the beginning.

```liquid
<!-- Iteration 1 -->
{% for i in (1..4) -%}
  {% cycle 'one', 'two', 'three' %}
{%- endfor %}

<!-- Iteration 2 -->
{% for i in (1..4) -%}
  {% cycle 'one', 'two', 'three' %}
{%- endfor %}


<!-- Output -->

<!-- Iteration 1 -->
one
two
three
one

<!-- Iteration 2 -->
two
three
one
two

```

<details>
<summary>Explanation</summary>

- When the cycle tag is used in Liquid, it starts by outputting the first value in the sequence provided.
- Then, each time the cycle tag is encountered again, it moves to the next value in the sequence.
- If it reaches the end of the sequence, it starts over from the beginning.

- In your code, during the first iteration, the cycle tag outputs 'one' because it's the first value in the sequence.
- Then, during the second iteration, it moves to the next value in the sequence, which is 'two', because it has already outputted 'one' in the previous iteration.

- So, in simple terms, each time the cycle tag is used, it moves to the next value in the sequence, starting from where it left off in the previous iteration.

</details>

```liquid
<!-- Iteration 3 -->
{% for i in (1..4) -%}
  {% cycle 'group_1': 'one', 'two', 'three' %}
{%- endfor %}

<!-- Iteration 4 -->
{% for i in (1..4) -%}
  {% cycle 'group_2': 'one', 'two', 'three' %}
{%- endfor %}


<!-- Output -->
<!-- Iteration 3 -->
one
two
three
one

<!-- Iteration 4 -->
one
two
three
one
```

<details>
<summary>Explanation</summary>

- **Iteration 3: 'one'**
  The cycle tag outputs 'one' because it's the first value associated with the named group 'group_1'.

- **Iteration 4: 'one'**
  Similarly, the cycle tag outputs 'one' because it's the first value associated with the named group 'group_2'.

</details>

### [tablerow](https://shopify.dev/docs/api/liquid/tags/tablerow)

- Generates HTML table rows for every item in an array.

- The tablerow tag must be wrapped in HTML <table> and </table> tags.

- Every tablerow loop has an associated tablerowloop object with information about the loop.

```liquid
{% tablerow variable in array %}
  expression
{% endtablerow %}
```

**cols**

- You can define how many columns the table should have using the cols paramet

```liquid
{% tablerow variable in array limit: number %}
  expression
{% endtablerow %}
```

**offset**

- You can specify a 1-based index to start iterating at using the offset parameter.

```liquid
{% tablerow variable in array offset: number %}
  expression
{% endtablerow %}
```

**range**

- Instead of iterating over specific items in an array, you can specify a numeric range to iterate over.

```liquid
{% tablerow variable in (number..number) %}
  expression
{% endtablerow %}
```

### [paginate](https://shopify.dev/docs/api/liquid/tags/paginate)

- Splits an array's items across multiple pages.

```liquid
{% paginate array by page_size %}
  {% for item in array %}
    forloop_content
  {% endfor %}
{% endpaginate %}
```

> Because for loops are limited to 50 iterations per page, you need to use the paginate tag to iterate over an array that has more than 50 items. The following arrays can be paginated:

<details>

<summary> </summary>

- all_products
- article.comments
- blog.articles
- collections
- collection.products
- customer.addresses
- customer.orders
- pages
- search.results
- collection_list settings
- product_list settings

### paginate tag parameters

```liquid
{% paginate collection.products by 3, window_size: 1 %}
```

</details>

## D. Syntax Tag

Syntax tags control how Liquid code is processed and rendered.

### comments

```liquid
{% comment %}
  content
{% endcomment %}

{% # This is inline comment %}


{% # this is a comment %}

{% # for i in (1..3) -%}
  {{ i }}
{% # endfor %}

{%
  ###############################
  # This is a comment
  # across multiple lines
  ###############################
%}

```

- You can use inline comment tags inside **liquid** tags. The tag must be used for each line that you want to comment.

```liquid
{% liquid
  # this is a comment
  assign topic = 'Learning about comments!'
  echo topic
%}
```

### liquid tags

- Allows you to have a block of Liquid without delimeters on each tag.

- Because the tags don't have delimeters, each tag needs to be on its own line.

> Use the echo tag to output an expression inside liquid tags.

```liquid
{% liquid
  expression
%}
```

```liquid
{% liquid
  # Show a message that's customized to the product type

  assign product_type = product.type | downcase
  assign message = ''

  case product_type
    when 'health'
      assign message = 'This is a health potion!'
    when 'love'
      assign message = 'This is a love potion!'
    else
      assign message = 'This is a potion!'
  endcase

  echo message
%}
```

### echo

- Outputs an expression.

- Using the echo tag is the same as wrapping an expression in curly brackets `({{ and }})`. However, unlike the curly bracket method, you can use the echo tag inside liquid tags.

```liquid
{% liquid
  echo expression
%}

{% echo product.title %}

{% liquid
  echo product.price | money
%}
```

### raw:

- Outputs any Liquid code as text instead of rendering it.

```liquid
{% raw %}
  expression
{% endraw %}


{% raw %}
{{ 2 | plus: 2 }} equals 4.
{% endraw %}


{% # Output: %}
{{ 2 | plus: 2 }} equals 4.
```

## E. Theme Tags

- Theme tags assign or render content that’s part of your [theme](https://shopify.dev/docs/themes/architecture).

### javascript

- JavaScript code included in a section file.

- You need to use these tags _only if your section or app block is meant to be installed on multiple themes or stores_.

- Otherwise, you should include the JavaScript that your section needs in your _theme's assets directory. Each section or app block can have only one `{% javascript %}` tag._

- Liquid isn't rendered inside of {% javascript %} tags. Including Liquid code can cause syntax errors.

```liquid
{% javascript %}
  javascript_code
{% endjavascript %}
```

### layout

Specify which layout to use.

```liquid
{% layout name %}

{% layout 'full-width' %}
{% layout none %}
```

### [render](https://shopify.dev/docs/api/liquid/tags/render)

- used to display a snippet or an app block.

1. **Scope of Variables**: Variables created outside of a snippet or app block cannot be directly accessed inside them. However, you can pass variables as parameters to snippets to use them inside the snippet.

2. **Access to Objects**: Inside a snippet or app block, you can access global objects as well as objects that are directly accessible outside the block. For instance, a snippet inside a product template can access the product object.

3. **Limitations Outside the Block**: Outside of a snippet or app block, you cannot access variables created inside the block.

4. **Restriction on Nested Tags**: When rendering a snippet using the `render` tag, you cannot use the `include` tag inside the snippet.
   `{% render 'filename' %}`

- This would render the contents of the 'filename' snippet or app block.

### [section](https://shopify.dev/docs/api/liquid/tags/section)

### [sections](https://shopify.dev/docs/api/liquid/tags/sections)

### [stylesheet](https://shopify.dev/docs/api/liquid/tags/stylesheet)

## F. Variables

Variable tags enable you to create new Liquid variables.

> **Predefined Liquid objects can be overridden by variables with the same name. To make sure that you can access all Liquid objects, make sure that your variable name doesn't match a predefined object's name.**

### assign

- Creates a new variable.

- You can create variables of any basic type, object, or object property.
  `{% assign variable_name = value %}`

```liquid
{%- assign product_title = product.title | upcase -%}

{{ product_title }}
```

### capture

- capture is used to store a block of content into a variable in Liquid.

- used to capture the output of any code within its block and store it in a variable. This is particularly useful when you want to manipulate or conditionally display content before rendering it.

- You can create complex strings with Liquid logic and variables.

```liquid
{% capture variable %}
  value
{% endcapture %}


{% capture greeting %}
  Hello, World!
{% endcapture %}

{{ greeting }}

```

<details>
<summary>More info</summary>

Certainly! Let's delve into `capture` with a straightforward example and explore its use cases.

**Example:**

```liquid
{% capture greeting %}
  Hello, World!
{% endcapture %}

{{ greeting }}
```

**Explanation:**

In this example:

1. `{% capture greeting %}`: This line starts the capture block and specifies the variable name `greeting` to store the captured content.

2. `Hello, World!`: This is the content we want to capture. It could be any text, HTML, or even Liquid code.

3. `{% endcapture %}`: This line marks the end of the capture block.

4. `{{ greeting }}`: This line outputs the content stored in the `greeting` variable.

**Use Cases:**

1. **Storing Complex Content**: You can capture complex content, such as HTML or Liquid code, and store it in a variable for later use. For example, capturing a block of HTML code for a section of a webpage.

2. **Dynamic Content Generation**: You can capture dynamic content generated by Liquid code and reuse it elsewhere in the template. For example, capturing the result of a conditional statement or a loop.

3. **Conditional Content**: You can capture different pieces of content based on conditions and display them selectively later. For example, capturing different greetings based on the time of day.

4. **Avoiding Repetition**: If you have a piece of content that you need to use multiple times in a template, capturing it once and storing it in a variable can help avoid repetition and make your template more manageable.

In summary, the `capture` tag in Liquid allows you to capture a section of content and store it in a variable for later use, offering flexibility and efficiency in template creation.

</details>

### decrement

- Creates a new variable, with a default value of -1, that's decreased by 1 with each subsequent call.

`{% decrement variable_name %}`

### increment

Creates a new variable, with a default value of 0, that's increased by 1 with each subsequent call.

`{% increment variable_name %}`
