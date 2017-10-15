## Some stuff* about Drupal
*Hopefully useful

---

## The intro bit

--

<!-- .slide: data-background="./images/willis.jpg" -->
## We be talking about

- This Drupal thing
- What can you do with it

--

## Skills you should learn

- Content modelling
- Content administration
- Site building
- Getting help

--

## Stuff we won't get time for

- Hosting
- Version control
- Configuration management
- Deployment best practice

--

## Stuff we might get time for

- Templates and theming*

<code><pre>* Will involve some &lt;html&gt;</pre></code>

Note:
- If we don't get time for this, happy to do more training

---

## What's this Drupal thing

--

## Drupal is

<blockquote>
- A content modelling framework<br>
- A content management system<br>
- A kickass community
</blockquote>

Angela Byron

---

## Who uses Drupal?

--

<!-- .slide: data-background="./images/princess-cruises.png" -->

## Corporate

--

<!-- .slide: data-background="./images/tesla.png" -->

## Corporate

--

<!-- .slide: data-background="./images/amaysim.png" -->

## Corporate

--

<!-- .slide: data-background="./images/lush.png" -->

## Corporate

--

<!-- .slide: data-background="./images/australia.png" -->

## Governments

--

<!-- .slide: data-background="./images/bundaberg.png" -->

## Governments

--

<!-- .slide: data-background="./images/whitehouse.png" -->

## Governments

--

<!-- .slide: data-background="./images/la.png" -->

## Governments

--

<!-- .slide: data-background="./images/london.png" -->

## Governments

--

<!-- .slide: data-background="./images/brisbane.png" -->

## Governments

--

<!-- .slide: data-background="./images/grammy.png" -->

## Entertainment

--

<!-- .slide: data-background="./images/bruno.png" -->

## Entertainment

--

<!-- .slide: data-background="./images/suncorp.png" -->

## Finance

--

<!-- .slide: data-background="./images/ge.png" -->

## Finance

--

<!-- .slide: data-background="./images/redcross.png" -->

## Charities

--

<!-- .slide: data-background="./images/earth-hour.png" -->

## Charities

--

<!-- .slide: data-background="./images/aljazeera.png" -->

## News

--

<!-- .slide: data-background="./images/weather.png" -->

## News

--

<!-- .slide: data-background="./images/olympics.png" -->

## Sports

--

<!-- .slide: data-background="./images/arsenal.png" -->

## Sports

--

<!-- .slide: data-background="./images/dallas.png" -->

## Sports

--

<!-- .slide: data-background="./images/oxford.png" -->

## Education

--

<!-- .slide: data-background="./images/uts.png" -->

## Education

--

## Did you notice a pattern?

---

## Who owns Drupal?

* Nobody - its GPL

--

## Who builds Drupal?

<!-- .slide: data-background="./images/group.jpg" -->

* Anyone who is willing

--

## Getting to know <br>the community

* https://drupal.org/user/register
* http://drupalslack.herokuapp.com/

---

## Let's get started

* Less yack, more hack
* Roughly based on user guide https://www.drupal.org/docs/user_guide/en/index.html

---

## Exercise 1

Planning our content model

--

<blockquote>You are making a website for a farmers market. The site needs to display information about the location and hours of the market, and an About page with the history of the market. It also needs to list the vendors. Vendors should be able to edit their listings (including a logo or photo), and post recipes. Site visitors should be able to browse recipes, or locate recipes using ingredients that they purchased at the market</blockquote>

Note:
- basic page (title, body)
- vendor (name, body, image, url)
- recipe (name, body, image, vendor, ingredients)
- block for footer notices
- ingredients taxonomy
- user profile

---

## Exercise 2

Planning our site structure

Note:
- location with directions and map
- opening hours
- history
- contact form
- list of vendors
- vendor details
- searchable list of recipes
- recipe details
- recently added recipes

---

## Exercise 3

Navigation

---

## Concepts

Entities and field types

--

## Concepts

Modules, Themes and Distributions

--

## Concepts

Paths and alises

---

## Exercise 4

Creating and administering content

Note:
- Create the about page
- create the home page

---

## Exercise 5

Setting a home page

---

## Exercise 6

Adding menus and menu items

Note:
- add about page to menu

---

## Exercise 7

Adding and deleting content types

Note:
- add a vendor content type
- add a recipe content type
- remove the agov content types

---

## Exercise 8

Adding fields to content types

Note:
- basic page (title, body)
- article
- vendor (name, body, image, url)
- recipe (name, body, image, vendor, ingredients)

---

## Exercise 9

Taxonomy

Note:
- ingredients taxonomy
- add ingredients field to recipe

---

## Exercise 10

Forms and widgets

Note:
- change widget of recipes field

---

## Exercise 11

View modes and formatters

Note:
- remove label for image and url
- put image first
- make image smaller

---

## Exercise 12

Managing users, roles and permissions

Note:
- add vendor role
- allow editing of own vendor and recipe content

---

## Exercise 13

Text formats and editors

Note:
- add h2

---

## Exercise 14

Blocks

Note:
- add some promoted vendors
- add an hours and locations block
- add a tagline block

---

## Exercise 15

Views

Note:
- add a vendor listing
- add a searchable recipes listing
- add a most recent recipes block

---

## Exercise 16

Image styles

Note:
- add a nicer sized image style

---

## Exercise 17

Home page

---

## Exercise 18

Path aliases

---

## Exercise 19

Expanding your site functionality

---

## Templating and theming

Let's look at some code

Note:
- delete all content
- delete block placements
- delete home page
- delete custom blocks
- fix home page settings to /node
- delete menu links from footer, main and quick
- delete news/pubilcations and latest updates views
- delete publication content type
