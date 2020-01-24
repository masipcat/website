---
title: Caddyfile Quick-start
---

# Caddyfile quick-start

Create a new text file named `Caddyfile` (no extension).

The first thing to type in a Caddyfile is your site's address:

```
localhost
```

Then hit enter and type what you want it to do, so it looks like this:

```
localhost

respond "Hello, world!"
```

Save this and run Caddy from the same folder that contains your Caddyfile:

<pre><code class="cmd bash">caddy start</code></pre>

Either open your browser to [localhost:2015](http://localhost:2015) or `curl` it:

<pre><code class="cmd"><span class="bash">curl localhost:2015</span>
Hello, world!</code></pre>

You can define multiple sites in a Caddyfile by wrapping them in curly braces `{ }`. Change your Caddyfile to be:

```
localhost {
	respond "Hello, world!"
}

localhost:2016 {
	respond "Goodbye, world!"
}
```

You can give Caddy the updated configuration two ways, either with the API directly:

<pre><code class="cmd bash">curl localhost:2019/load \
  -X POST \
  -H "Content-Type: text/caddyfile" \
  --data-binary @Caddyfile
</code></pre>

or with the reload command, which does the same API request for you:

<pre><code class="cmd bash">caddy reload</code></pre>

Try out your new "goodbye" endpoint [in your browser](http://localhost:2016) or with `curl` to make sure it works:

<pre><code class="cmd"><span class="bash">curl localhost:2016</span>
Goodbye, world!</code></pre>

When you are done with Caddy, make sure to stop it:

<pre><code class="cmd bash">caddy stop</code></pre>

## Further reading

- [Caddyfile concepts](/docs/caddyfile/concepts)
- [Directives](/docs/caddyfile/directives)