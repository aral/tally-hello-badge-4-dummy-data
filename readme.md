<img src='http://aralbalkan.com/images/tally-hello-badge-4-dummy-data.png'>

Tally Hello Badge Example: Dummy Data (part 4 of 4)
===

In the previous installments, we used the [Tally template engine](http://tally.jit.su) ([fork Tally on GitHub](https://github.com/aral/tally)) to create a sheet of name badges for attendees and speakers. We covered how to set the text and attributes of elements, how to repeat elements, and how to conditionally display elements.

In this, the final example in the series, we’re going to add some dummy data to our template so that it contains all the elements present in the rendered output. This will allow us to style the template even if we don’t have access to the server.

Usage
---

1. Clone the repository.
2. Run server.coffee (I use ```nodemon server.coffee``` while developing. Or you can just run ```coffee server.coffee```). Once the server is running, go to ```http://localhost:3000``` to see the example and ```http://localhost:3000/hello-badge.html``` to see the template source.
3. Read the notes below and take a peek at the source code.

How it works
---

Templates in Tally are pure HTML 5. Tally uses ```data-``` attributes to populate templates either on the server or on the client (or both).

One of those attributes, ```data-tally-dummy``` is used to mark up dummy elements that will not be included in the final render of the template. You can use dummy elements to add mock data to your templates so that you can keep evolving the design of the template without requiring constant access to (a possibly-ever-changing and unstable) server-side implementation.

You can also use data that tests edge cases e.g., word‐wrapping on very long names, etc.

The template
---

We’ve modified our template to add dummy data for users to help us style the speaker notice and the perforations and scissors icon between badges without requiring access to the rendered output.

```html
	<ul>
		<li data-tally-repeat='person people'>
			<a data-tally-attribute='href person.homepage'>
				<p>
					Hello, my name is <span data-tally-text='person.name'>Inigo Montoya</span>
					<span data-tally-if='person.isSpeaker'>Speaker</span>
				</p>
			</a>
		</li>
		<li data-tally-dummy>
			<a data-tally-attribute='href person.homepage'>
				<p>
					Hello, my name is <span data-tally-text='person.name'>Sarah</span>
					<span data-tally-if='person.isSpeaker' style='display:none'>Speaker</span>
				</p>
			</a>
		</li>
		<li data-tally-dummy>
			<a data-tally-attribute='href person.homepage'>
				<p>
					Hello, my name is <span data-tally-text='person.name'>Joe</span>
					<span data-tally-if='person.isSpeaker'>Speaker</span>
				</p>
			</a>
		</li>
	</ul>
```

You can see the updated template by visiting ```http://localhost:3000/hello-badge.html``` after you run the server for this example.

The server
---

Nothing has changed on the server.

That’s it!

You can use your templates to evolve your design and stylesheets in parallel with the evolution of the server.

Table of Contents
---

* Part 1: [Text and Attribute](https://github.com/aral/tally-hello-badge-1-text-and-attribute)
* Part 2: [Repetition](https://github.com/aral/tally-hello-badge-2-repetition)
* Part 3: [Conditionals](https://github.com/aral/tally-hello-badge-3-conditionals)
* Part 4: [Dummy Data](https://github.com/aral/tally-hello-badge-4-dummy-data)

This is just a very simple example. [Check out the Tally web site](http://tally.jit.su) for more complicated ones.