 Trivial - A Little Something to Get You Started (Web CTF Write-up)

 Challenge Overview
- Challenge Name: Trivial - A Little Something to Get You Started
- Category: Web
- Difficulty: Easy
- Objective: Find the hidden flag by analyzing the page source.

 Approach & Solution

 Step 1: Inspecting the Page Source
Since the challenge hint suggests looking at the source of the page, the first step was to open the website and inspect its HTML source code.

- In most browsers, this can be done by right-clicking on the page and selecting View Page Source or by pressing `Ctrl + U`.

 Step 2: Searching for Hidden Elements
After opening the page source, I carefully examined the HTML content to identify anything out of the ordinary.

- Many CTF challenges hide flags in HTML comments.
- Using `Ctrl + F`, I searched for terms like flag, ctf, or hidden.
- In this case, the following comment was found within the source:

```html
<!-- Flag0: FLAG{^FLAG^9da151eb01d932ddc00921ba124c8acc11beb56ef06070768cab9fd461deb1d0$FLAG$} -->
```

 Step 3: Submitting the Flag
With the flag found in the HTML comments, I copied it and submitted it to complete the challenge:
Visiual 
```

```

 Lessons Learned
- Always check the page source for hidden flags or comments.
- Use browser developer tools (`Ctrl + Shift + I` or `F12`) to analyze elements, network requests, and hidden scripts.
- Searching within the HTML can quickly reveal hidden information.

 Conclusion
This challenge was a great introduction to web-based CTF challenges, emphasizing the importance of understanding how web pages are structured and how developers may leave hints in the source code.

🚀 Happy Hacking!

