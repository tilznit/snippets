### Is the site content static?
Problem with static conect is: It's static. There is nothing to exploit. So the only thing you could try doing is attacking the actual server implementation (like apache) or any used forward proxy. Both of these attacks imo. rarely work unless the server is stupidly out of date or there comes a new zero day.  
What you really want to do with static pages is look if you can find any useful information. Like possible usernames or even password. Look into the source code as well.  
Oh right, one thing I forgot: html pages can actually be (user-side) dynamic via javascript. So if you find javascript in that html page that does stuff like loading in content from other sites and/or an API, that might be worth poking at.  
Let me clarify.
Really I mean getting stuff from other pages. But this can be of course triggered by a mouse-over. The actual animation you might see is (nowadays) typically done in css which is again static.  
So look for stuff loaded by javascript. Often that might be things like REST APIs that will then serve the dynamic content. That API is worth poking at.  
If the JS only loads in static stuff agian, it's less interesting.
