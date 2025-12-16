
2024-12-27

Tags: [[Javascript]] [[Web]]
# Sending HTTP requests with JS
```
fetch("https://jsonplaceholder.typicode.com/todos",
    {
        method: "POST",
        body: JSON
        .stringify
        ({
          userId: 1,
          title: "Demo Todo Data",
          completed: false,
        }),
        headers: {
          "Content-type": "application/json",
        },
      })
        .then((response) => response.json())
        .then((json) => console.log(json));
```
This is one way to send a request using the base api fetch()
```
fetch("http://localhost:8080/games/conway/post",
	{
		method: "POST",
		body: data, 
		headers: 			
		{
			"Content-Type": "application/x-www-form-urlencoded"
		}
	}).then((response) => console.log(response));

```
This is another way that avoids having to use the horrific .json file
# References
[[HTTP]]