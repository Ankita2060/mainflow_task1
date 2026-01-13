# mainflow_task1
1. Imagine you're given a CSV file with 10,000 customer records, but 15% of the "Age"
column values are missing. How would you handle this missing data before analysing
customer demographics?
2. You need to identify which products are frequently purchased together. What kind of
analysis would you perform, and what specific techniques or tools would you use?
3. Explain the difference between a bar chart and a histogram. When would you use
each, and what does this tell you about the nature of the data they represent?
4. Write a simple SQL query to find all customers from "New York" who spent more than
$500 in January, ordered by their total spending (highest to lowest).
5. You analyse website traffic data and find that page load times increase dramatically
when more than 100 users are active. What are at least three possible reasons for this
correlation, and how would you investigate further?
answers:

With 15% of data missing (1,500 records), simply deleting the rows might bias your results. I would handle this using the following steps:Analyze the Missingness: I’d check if the data is "Missing at Random" (e.g., a technical glitch) or "Missing Not at Random" (e.g., older users being less likely to share their age).Imputation by Central Tendency: For a quick demographic overview, I would replace missing values with the Median (rather than the mean) because age data is often skewed and the median is more robust against outliers.Predictive Imputation: If accuracy is critical, I’d use a regression model or K-Nearest Neighbors (KNN) to predict the missing ages based on other variables like "Income" or "Product Category."Flagging: I would create a binary "Age_Missing" column to track which records were imputed, ensuring transparency during the final analysis.2. Identifying Products Purchased TogetherThis is a classic Market Basket Analysis.The Technique: I would use Association Rule Mining. The primary algorithm for this is Apriori.Key Metrics:Support: How often the product combination appears in all transactions.Confidence: How often product B is bought when product A is purchased.Lift: The strength of the association (a lift > 1 suggests a real relationship rather than a coincidence).Tools: In Python, I would use the mlxtend library. In R, the arules package is the standard.3. Bar Chart vs. HistogramThe fundamental difference lies in the type of data being measured.FeatureBar ChartHistogramData TypeCategorical (Discrete groups)Quantitative (Continuous ranges)SpacingGaps between barsBars are touching (shows continuity)X-AxisLabels (e.g., City, Product Name)"Bins" or intervals (e.g., 0-10, 11-20)UsageComparing different groups.Showing the distribution of a dataset.When to use: Use a Bar Chart to see which car brand sold the most. Use a Histogram to see the age distribution of those car buyers.4. SQL Query: High-Spenders in New YorkAssuming your table is named Sales, the query would look like this:SQLSELECT Customer_Name, SUM(Amount_Spent) AS Total_Spent
FROM Sales
WHERE City = 'New York' 
  AND Order_Date BETWEEN '2026-01-01' AND '2026-01-31'
GROUP BY Customer_Name
HAVING SUM(Amount_Spent) > 500
ORDER BY Total_Spent DESC;


Describe your process for learning a completely new technical skill or technology.
How do you approach it, what resources do you use, and how do you know when you've
understood it well enough?
2. You're stuck on a technical problem for several hours. What do you do? Outline at
least three specific strategies you would use to make progress.
3. How would you explain a technical concept from your domain (like a database, API, or
machine learning model) to a non-technical family member?
4. What does "debugging" mean beyond just fixing code errors? Describe the mindset
and systematic approach you would take to debug any complex system problem.
5. Why is documentation important in technical work, even if you're the only one who
will ever see the code or project?

answers:

The Learning Framework: The "Inside-Out" Approach
I follow a structured path that moves from passive consumption to active creation.

The "Why" and "What": I start with the high-level purpose. I don't look at syntax first; I look at what problem the technology solves.

The 20-Hour Rule: I focus on the "vital few" concepts (the 20%) that provide 80% of the functionality. For a new language, this is data structures, control flow, and error handling.

Resources: I prefer a mix of official documentation (for accuracy), high-quality video tutorials (for mental modeling), and "Cheat Sheets" (for quick syntax reference).

The "Understanding" Metric: I know I’ve understood a concept when I can build a small, functioning project from scratch without following a tutorial and when I can explain the "trade-offs" of that technology compared to its competitors.

2. Breaking the Deadlock: Strategies for Being Stuck
Getting stuck is part of the process. When I hit a wall for more than two hours, I pivot:

The "Rubber Duck" Method: I explain the problem out loud to an inanimate object (or a colleague). The act of verbalizing the logic often reveals the flaw in my assumptions.

The "Binary Search" of Logic: I start commenting out or "turning off" parts of the system until the error disappears. Once it's gone, I know the last piece I removed contains the bug.

State Verification: I stop guessing and start measuring. I use print statements or debuggers to check the value of every variable at every step to find exactly where the reality of the data diverges from my mental model.

3. Explaining a "Database" to a Family Member
"Imagine you run a massive library. A Database isn't just the books; it’s the entire system of shelves, the card catalog, and the librarian.

If you just threw all the books in a pile on the floor, you'd have data, but you couldn't use it. A database is the 'smart shelving' that ensures every time you want a specific recipe from a specific book, the librarian can find it in seconds, even if there are millions of other books in the room."

4. Debugging: More Than Just Fixing Errors
Beyond fixing a typo, debugging is scientific investigation. It’s the process of identifying why a system is behaving in an unintended way.

The Mindset: I approach it with humility and skepticism. I assume my assumptions are wrong and that the system is doing exactly what it was told to do, even if that's not what I intended.

The Systematic Approach:

Reproduce: Can I make the error happen consistently?

Isolate: Which specific component is failing? (The frontend? The database? The network?)

Hypothesize: Based on the evidence, what is the most likely cause?

Test: Apply a fix and—crucially—check if it broke anything else.

5. The Importance of "Self-Documentation"
Even if I am the only user, documentation is a gift to my "future self."

Memory Decay: In six months, I won't remember why I chose a specific complex logic over a simpler one. Documentation captures the intent.

The "Onboarding" of Future You: Good documentation allows you to pick up a project after a long break without spending two days relearning how it works.

Code as Communication: Writing documentation forces me to review my own work. If I find it hard to explain how a function works, it’s usually a sign that the code is too complex and needs to be simplified.
5. Investigating Website LatencyA dramatic increase in load times at a specific threshold (100 users) usually points to a bottleneck.Possible Reasons:Server Resource Exhaustion: The CPU or RAM on the web server might be hitting 100% utilization, causing requests to queue up.Database Connection Pooling: The database may only allow a limited number of concurrent connections (e.g., 100). The 101st user has to wait for a previous session to close.
