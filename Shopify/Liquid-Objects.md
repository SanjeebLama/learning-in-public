# Objects

- objects are data structures that hold information about various aspects of an online store.

- These objects provide access to different types of data, such as products, collections, orders, customers, and more.

- Understanding Liquid objects is essential for customizing Shopify themes and building dynamic storefronts.

Here's an overview of some commonly used Shopify Liquid objects:

1. **Product Object**:

   - The `product` object represents an individual product in the store.
   - It provides access to properties such as title, description, price, variants, images, and tags.
   - Example usage: `{{ product.title }}`, `{{ product.price }}`, `{{ product.images.first }}`.

2. **Collection Object**:

   - The `collection` object represents a group of related products in the store.
   - It provides access to properties such as title, description, products, and image.
   - Example usage: `{{ collection.title }}`, `{{ collection.description }}`, `{{ collection.products }}`.

3. **Order Object**:

   - The `order` object represents a customer's order in the store.
   - It provides access to properties such as order number, line items, total price, shipping address, and customer information.
   - Example usage: `{{ order.order_number }}`, `{{ order.line_items }}`, `{{ order.total_price }}`.

4. **Customer Object**:

   - The `customer` object represents a customer in the store.
   - It provides access to properties such as name, email, shipping address, billing address, and order history.
   - Example usage: `{{ customer.name }}`, `{{ customer.email }}`, `{{ customer.default_address }}`.

5. **Variant Object**:

   - The `variant` object represents a specific variant of a product.
   - It provides access to properties such as title, price, inventory quantity, SKU, and image.
   - Example usage: `{{ variant.title }}`, `{{ variant.price }}`, `{{ variant.inventory_quantity }}`.

6. **Page Object**:

   - The `page` object represents a static page in the store, such as an About Us or Contact page.
   - It provides access to properties such as title, content, URL, and SEO meta information.
   - Example usage: `{{ page.title }}`, `{{ page.content }}`, `{{ page.url }}`.

7. **Blog Object**:
   - The `blog` object represents a blog in the store.
   - It provides access to properties such as title, articles, URL, and meta information.
   - Example usage: `{{ blog.title }}`, `{{ blog.articles }}`, `{{ blog.url }}`.

These are just a few examples of Shopify Liquid objects. Each object has its own set of properties and methods that can be used to access and manipulate data within a Shopify theme. By leveraging Liquid objects effectively, developers can create dynamic and personalized shopping experiences for customers.
