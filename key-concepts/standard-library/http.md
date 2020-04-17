# HTTP

CSML includes a native HTTP client. The following verbs are accepted:

* GET
* POST
* PUT
* PATCH
* DELETE

### Performing a HTTP request

To build your request, you can chain explicit methods to the HTTP function. No request is actually performed until `.send()` is added, allowing you to gradually build your request.

Here is a simple example:

```cpp
do pet = HTTP("https://example.com/pets/1").get().send()

// or, if no verb is specified, .get() is implicitly used
do pet2 = HTTP("https://example.com/pets/2").send()

say "This pet is called: {{pet.name}}"
```

You can also create more complex requests:

```cpp
do req = HTTP("https://example.com/pets").set({"authorization":"Bearer XXXXX"})

if (query_mode == "retrieve") {
    // retrieve all the available pets from the API
    do req = req.get()
}
else {
    // this will create a new pet
    do req = req.post({"name": "Oreo", "breed": "poodle"})
}

do res = req.send()

say "{{res}}"
```

The available methods are:

* `.get()` / `.post(body)` / `.put(body)` / `.patch(body)` / `.delete()` : set the request verb
* `.set(body)`: set the request headers
* `.query(body)`: set the query strings \(?key=value\)

where `body` is optional JSON-formatted data.



