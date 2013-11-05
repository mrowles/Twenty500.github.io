---
layout: post

title: 			"Stop using JUnit @Ignore"
subtitle: 		"Refining testing, one blog post at a time"
categories: 	java junit testing
cover_image:    wollongong-cover.jpg

excerpt: 		"We spend so long writing, refining and running tests. Stop using @Ignore!"

author:
  name: 		Andrew Canby
  twitter: 
  gplus: 
  bio: 			Developer
  image: 		ks.png
---

This post is more of a rant than anything, but it is something that I feel strongly enough about to take the time to write, so here goes.

## Stop using @Ignore in your test suite! ##

There I said it. I really wish it was either never thought of, or that it's usage was more widely frowned upon.

We spend so long writing, refining and running tests. I don't understand why anyone would then go and throw away what is valuable information, just to get a green light on the build.

I understand that sometimes tests fail for unknown reasons. This can be frustrating and I suspect is the catalyst for the widespread use of @Ignore. Tests failing for unknown reasons (i.e. only on the build server) make things hard, and are not what I am ranting about here.

## The Solution ##

1. The most drastic solution is to add the code below to the JUnit jar using the Maven Shade plugin.
2. For a simpler, less intrusive solution, override @Ignore locally in your project (ensuring that you specify the correct package):

{% highlight java %}
package org.junit;

/**
 * Yes! @Ignore is overridden so you can't use it! Think about why the test is failing, and fix that.
 *
 * Don't bandaid the problem for someone else to fix later.
 */

@java.lang.annotation.Retention(java.lang.annotation.RetentionPolicy.RUNTIME)
@java.lang.annotation.Target({})
public @interface Ignore {
    java.lang.String value() default "";
}
{% endhighlight %}

Now this doesn't stop people from commenting out tests, but there isn't much you can do about that. 

Education is the key. Try to instil in your development team a culture which aspires to test more, rather than just resolve issues (resolve is a subjective term when you resolve an issue at the expense of a previously passing test). When you resolve issues at the expense of tests, it generally means that you're ignoring a warning of a problem. These are hard to track down later!
