
 

Nothing really to do with it after importing; everything else will make use of the link flows in here. Nice to see how I managed to handle some common tasks, and the concepts being used to make this as repeatable as possible for additional API capabilities. Think of this as a Mimecast SOAR integration, and the flows here are different actions that can be taken.

 

This does handle turning API keys into tokens, reusing tokens, getting new ones when needed, standard pagination, retrying when rate-limiting kicks in, etc.

 

What you can now do is start to create your own flows (ideally, on a different tab) that make use of these:

 



 

Here's what these examples do:

This uses the credential module to securely store your API keys.

This is a basic example to interact with the API to get account info. When you trigger the flow, the "Add Auth Info" (the flow in Step 1) will add connectivity info, including API keys. Then passes it on to the "Get Account" linked flow, which will make the API call on the other flow, and output the results

this is another basic example to get TTP-IP logs. When you trigger the flow, the "Add Auth Info" does it's thing again, but then passes it to a different linked flow, which will return the impersonation logs.

This one builds on top of 2 & 3, where you can actually supply some input data to alter the results you'd get (it's possible with Step 3, as well, but not required). By adding flags, filters, searches, etc. in the payload data object, you can scope the results you want returned.
