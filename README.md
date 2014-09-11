# Params in Sinatra

### What are params?

Params is short for the word parameter. A parameter is a key-value pair that is encoded in a HTTP request. There are three kinds of params: `user supplied parameters`, `routing parameters`, and `default parameters`. In this case, we are discussing `routing parameters`.

Using the example from the previous *Routes* module, let's say that we have a HTTP request, `GET /medicines/17`, and it matches the following controller method.

```ruby
# medicines_controller.rb
get '/medicines/:id' do
  ...
end
```

So here we see that the HTTP verb and paths match between the HTTP request and the controller action; they both have a `get` verb and they both have the `/medicines` path. The only difference is that the HTTP request has this `17` parameter, and the controller action has the `:id` parameter. What's significant about this? The controller action basically specifies that whenever a `GET` request is sent to the `/medicines` path with a parameter, the parameter is equal to the `id` key. So, to complete our thought above, we are looking for the `Medicine` object that has an `id` equal to 17.

Let's look at the completed controller action and corresponding block below:

```ruby
# medicines_controller.rb
get '/medicines/:id' do
  @medicine = Medicine.find(params[:id])

  erb :'/medicines/show.html'
end
```

You've noticed that we have `Medicine.find(params[:id])`. You might be wondering, "what does a params structure look like?" To answer your question, params is simply a hash that stores the key-value pairs that were encoded inside of the URL/HTTP request. See below:

```ruby
params = {
  "id" => "17"
}
```

So our params is a way to encapsulate data that is passed around through our encoded URL/HTTP requests. 

### Resources
- [Sinatra URL Matching](http://ruby.about.com/od/sinatra/ss/sinatra3_3.htm)
- [Sinatra Readme](http://www.sinatrarb.com/intro.html)
