Mimecast Flow
These are a set of linked flows that can be used by other flows within Node Red to make API calls to Mimecast's API 2.0 endpoints. These make use of the public API documentation found here: https://developer.services.mimecast.com/apis

![image001](https://github.com/dhb41/nodered/assets/141678879/6694629b-cd7e-4803-9548-080fd377b4eb)

To start using these flows, copy the flows.json file contents, and in Node Red, go to the top-right hamburger menu, and select import

![image](https://github.com/dhb41/nodered/assets/141678879/9b5c04f4-3c9c-4d82-b48f-651f9136eea3)

There's nothing really to do with it after importing; everything else will make use of the link flows in here. Nice to see how some common tasks are handled, and the concepts being used to make this as repeatable as possible for additional API capabilities. Think of this as a Mimecast SOAR integration, and the flows here are different actions that can be taken.

This does handle turning API keys into tokens, reusing tokens, getting new ones when needed, standard pagination, retrying when rate-limiting kicks in, etc.

What you can now do is start to create your own flows (ideally, on a different tab) that make use of these:

![image002](https://github.com/dhb41/nodered/assets/141678879/c5b18de4-fa35-4d27-8549-0e584d3c4a50)

Here's what these examples do:

1. This uses the credential module to securely store your API keys:

![image003](https://github.com/dhb41/nodered/assets/141678879/118c6dd0-a141-499d-a3bc-b8e482c923ec)

3. This is a basic example to interact with the API to get account info. When you trigger the flow, the "Add Auth Info" (the flow in Step 1) will add connectivity info, including API keys. Then passes it on to the "Get Account" linked flow, which will make the API call on the other flow, and output the results:

![image004](https://github.com/dhb41/nodered/assets/141678879/7ecb851e-b940-4de0-8823-dd2889159e80)

3. This is another basic example to get TTP-IP logs. When you trigger the flow, the "Add Auth Info" does it's thing again, but then passes it to a different linked flow, which will return the impersonation logs:

![image005](https://github.com/dhb41/nodered/assets/141678879/9fc27bae-94e0-40d8-8de9-34ab90f389f1)

This one builds on top of 2 & 3, where you can actually supply some input data to alter the results you'd get (it's possible with Step 3, as well, but not required). By adding flags, filters, searches, etc. in the payload data object, you can scope the results you want returned.

![image006](https://github.com/dhb41/nodered/assets/141678879/4250c85e-21b8-437f-a71e-90b0f854434a)
