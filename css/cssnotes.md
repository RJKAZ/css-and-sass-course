- Measurments in CSS

Pixels, Percentages, Ems, and Rems

In CSS you use measurments alot. Margin, padding, font size, width, height, etc...all use measurments to determine the size of a specifc value.

Here is a breakdown of the most common measurments

Unit Description

px - pixels

% - percent

em - Relative to the font size of the parent element. If the parent element has a font size of 14px, then 1em will = 14px

rem = Relative to the font size of the root element. If the HTML element is 18px, then 1rem will = 18px.

- The CSS Box Model

Think of all elements in HTML as appearing within a box. CSS treats all elements this way
Both block and inline-level elements occupy a box
All boxes have margin, padding, and borders.
Block Level elements have a width property, whereas inline-level elements do not.

So lets take a div for example, that DIV has its content area (width) and surrounding that is padding. Surrounding that is the border, and beyond that is the margin

- Margins
  Margins live outside the box. In the browser, margins are invisible

Top and bottom margins overlap on adjacent elements.

If you have an h3 followed by an h4, then you've defined the h3 to have margin-bottom: 30px and the h4 to have margin-top: 10px, you might think this adds up to 40px but it doesn't. The two margins overlap and the larger of the two margins are used. Therefore the margin between these elements would be 30px.

h3 element
[30 px margin]
[10 px margin]
h4 element

You would think thats how they stack, but the smaller margin would get absorbed into the larger one

h3 element
[30 px margin]
h4 element

to note, this only applies to top and bottom margins. Not left and right

Inline elements do not display verticle margins. However they do display left and right margins

Padding resides within the box. So a background color that defines the color of the div would extend to the padding.

- Using Margins and Padding

to add margin and padding in CSS, all we have to do is define the size of the margin on all four sides of the box

margin-top: 10px;
margin-right: 10px;
margin-bottom: 10px
margin-left: 10px

or a shorter cut

margin: 10px 10px 10px 10px

or even shorter, using this way the browser would treat all sides as having 10px

margin: 10px

if any of the values are equal to 0px, we can skip writing the unit of measure

margin: 0;

but to define specifc margins

margin: 0 10px 20px 30px

these go in a specific order; top, right, bottom, left

Now you can also use two values if you want

margin 0 10px;

the first number would be top and bottom, and the 2nd number would be left and right

and even use 3 values if you want

margin: 0 10px 20px

with the first value being top, the 2nd value being left and right, and then the 3rd value being bottom

all these techniques applue to padding and borders as well

- Borders

Borders are little different. Borders don't only have a border-width, they also have a border-style property, and a border-color property. Only the border-style property is required. Here's how you declare them.

border-style: solid;
border-width: 4px;
border-color: #333;

Now, what if all sides have the same style, width, and color? there is a shorthand for that

border: solid 4px #333

You can also create variatons in the border properties by overriding some properties with more specific declarations

border; solid 4px #333;
border-bottom-color: #fc3;

since the second border declaration comes later in the stylesheet, the CSS overrides the bottom border color of #333 with #fc3 instead.

- The Specificity Rule

Sometimes when you make large scale projects, your CSS files become large, very large, and the larger they are, the higher the chance of more problems.

So the Specificity Rule is - More specific, Higher Priority

CSS means cascading style sheets. The styles cascade down the document

h1 {
background: black;
}
h1 {
background: white;
}

In this example, the latter style is applied to the h1 because it comes later in the document.

Typically you wouldn't add identical selectors in your CSS, but the larger the CSS file, the more likely you'll do so by accident and have conflicting CSS rules.

p em { font-weight: bold; }
em { font-weight: normal; }

even though the single em style came later in the document, its font-weight will be bold simply becasue the p em selector is more specific than em alone

There is a way to calculate the specificity of a selector to see if it will take precedence over another. For example

1000 points - inline styles (Most specific)
100 points - IDS
10 points - Class, Attributes, Pseduo Classes
1 point - Elements, Pseudo elements (Least specific)

so even though inline styling isn't recommened, it will always overpower any other style

In the same vein, an ID would take precedent over a class

so here's a weird example

#fish h1.bass em = specificity of 112

Because its an ID (100 points) + HTML Element (1 point) + Class (10 point) + HTML Element (1 point)

so in this example

111 points - #fish h1.bass {background: blue; }
110 points - #fish .bass {background: red; }

The first selector would win out and the background of .bass would be blue becasue it has more points then the bottom selector, even though the second selector comes later in the stylesheet.
