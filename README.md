LinkParser
=================================================

For this homework, you will get all of the well-formed URLs from a snippet of HTML.

Eventually, we want to be able to crawl the web and parse web pages. As such, we must be able to find the URLs (or links) embedded in the HTML code of the web pages. This assignment is a step towards this functionality. Specifically, you must return a list of HTTP or HTTPS URLs (or links) from the HTML `a` anchor tag `href` attribute. This should not include links in the `href` attribute of the `link` tag!

You have been provided with a method that will make sure URLs are in a semi-consistent properly-encoded form. You will need to figure out how to deal with relative vs absolute links, however. See below for more.

## Hints ##

There are many helpful resources on the web to learn more about HTML. Some resources include:

* [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML)
* [W3C Markup Validation](http://validator.w3.org/)
* [Web Design Group](http://htmlhelp.com/)
* [Codecademy](https://www.codecademy.com/learn/web)

You will need to be familiar with the anchor tag `<a>` for this assignment. Some resources include:

* [MDN - &lt;a&gt; The Anchor element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)
* [MDN - What is a URL](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL)
* [The Java Tutorials - Creating a URL](https://docs.oracle.com/javase/tutorial/networking/urls/creatingUrls.html)

The anchor tag is used to create links on web pages. For example:

```html
<a href="https://www.cs.usfca.edu/">USF CS</a>
```

The above code will generate the link <a href="https://www.cs.usfca.edu/">USF CS</a>, where the link text is `USF CS` and the link destination is `https://www.cs.usfca.edu/`. The link will always be placed in the `href` attribute of the `a` tag, but not all `a` tags will have this attribute. For example, this is a valid `a` tag without the `href` attribute:

```html
<a name="home" class="bookmark">Home</a>
```

And, the `href` attribute may appear in other tags. For example, this is a valid `link` tag to include a style sheet:

```html
<link rel="stylesheet" type="text/css" href="style.css">
```

The majority of URLs on webpages are relative (i.e. specified relative to the current webpage URL). You will need to convert those relative URLs into an absolute URL. For this, you may use the `java.net.URL` class. For example, consider the following:

```java
URL base = new URL("http://www.cs.usfca.edu/~sjengle/cs212/");
URL absolute = new URL(base, "../index.html");

// outputs http://www.cs.usfca.edu/~sjengle/index.html
System.out.println(absolute);
```

This works even if the provided string was already absolute. For example:

```java
URL base = new URL("http://www.cs.usfca.edu/~sjengle/cs212/");
URL absolute = new URL(base, "http://www.example.com/");

// outputs http://www.example.com/
System.out.println(absolute);
```

Because of this, you do not need to test if a link was relative or absolute. You can simply **always use the above code**.

## Requirements ##

See the Javadoc and `TODO` comments in the template code in the `src/main/java` directory for additional details. You must pass the tests provided in the `src/test/java` directory. Do not modify any of the files in the `src/test` directory.

See the [Homework Guides](https://usf-cs212-fall2020.github.io/guides/homework/) for additional details on homework requirements and submission.
