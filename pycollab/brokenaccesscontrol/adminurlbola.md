# admin url bola i guess

so i just installed burp suite and i was extremely excited to test it on my friends site
i went to the /admin endpoint with intercept and i saw it was a GET /admin/users/(my id)
and as someone who JUST installed burpsuite for an easy ctf, i did what anyone would do
/admin/users/4 (4 was the id of the owner)

and then i actually got into the admin panel as him

who knew his site was gonna be exactly like a ctf

then he got proper authentication (jwt) and i got fried
