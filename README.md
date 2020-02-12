# query-redirect
A simple Javascript query (?[domain]) redirect script and template. Can be invoked by visiting `http://siteurl.com/redirect.html?[newdomain]`.

It can be unified under one `<script>` tag, or defined as a function to your JS file. No external JS libraries are needed, and it works in all major browsers. 

---

### Inline script:

```
<script>
    setTimeout(function() { // sets time to redirect to 5 seconds
        if (window.location.search.indexOf('?') !== -1) { // checks for query in address bar
                if (window.location.search.indexOf('https://') !== -1) { // checks for https:// protocol in query
                    var query = window.location.search; // gets query from address bar
                    var target = query.replace("?", ""); // removes "?" from query
                    window.location.href = target; // sends user to target
                } else if (window.location.search.indexOf('http://') !== -1) { // checks for http:// protocol in query
                    var query = window.location.search; // gets query from address bar
                    var target = query.replace("?", ""); // removes "?" from query
                    window.location.href = target; // sends user to target
                } else { // if no protocol is declared
                    var query = window.location.search; // gets query from address bar
                    var target = query.replace("?", ""); // removes "?" from query
                    window.location.href = "http://" + target; // sends user to http://[target] in case target does not support SSL
                }
            } else { // if no query
                window.location.href = "https://yourdomain.com" // sends user back to homepage
            };
    }, 5000);
</script>
```

---

This repository contains two files: `index.html`, which is a test page that demonstrates how the redirect works, and `redirect.html`, which is a basic template for the redirect script (inculdes a cancel button). Most users will only ever need `redirect.html`, and it can be customized easily. 

You can clone this repository for a ready-to-go redirect page, which can be uploaded to any webroot and modified to your liking. A live version of this page is also available at https://query-redirect.000webhostapp.com. 
