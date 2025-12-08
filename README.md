# MSBA-Capstone-Individual-Notebook Introduction
Individual notebook for IS 6813-001 Fall 2025 MSBA Capstone Case Comp. Summary of the project and the business value of our results. 

# Summary of business problem and project objective
Swire Coca-Cola’s digital ordering platform, MyCoke360, is experiencing significant cart abandonment, where customers add items to their carts but fail to complete purchases by their next order date. This behavior results in direct revenue loss, disrupts product mix performance, and risks long-term customer disengagement. Understanding the drivers of cart abandonment and recovery is critical to reducing revenue leakage, improving order completion, and strengthening customer retention. Insights from this analysis will identify behavioral patterns that influence cart abandonment and recovery and make recommendations to address these patterns.

In this project, we defined "abandoned" and "recovered" carts within the context of Swire's business structure and available data, and quantified their financial impact. We used Google Analytics and order data to identify behavioral patterns that influenced cart abandonment/recovery, and provided insights to improve order completion.

The purpose of this project was to gain hands-on experience working in a group to execute a complex data analytics project for a sponsoring company in a case competition format and to develop a portfolio of the individual project-related analytics work at Github to showcase technical and communication skills for prospective employers. 

# My group's solution to the business problem
We defined Abandoned and Recovered carts using the following rules:

* A cart/order window is abandoned if there was an add_to_cart within an order window, but no purchase event.
* A cart/order window is recovered if it was abandoned AND if there was a purchase event in the next order window.

we used a text analytics approach to better understand behavioral patterns that lead to cart abandonment, then clustered order windows into four main groups. These four groups represented 4 distinct populations that use MyCoke360, and revealed why users in each group may abandon their cart. Using this information, we provided specific UI improvements that could be implemented in MyCoke360 to improve order completion.

# My contribution to the project
I performed EDA for the operating_hours table and for the orders table. I collaborated with the group to merge our EDA notebooks and brainstorm the types of models we would use for the project. I added bar charts for Estimated Financial Loss from Abandoned Carts by Brand and by Pack Type. I reviewed and formatted the Modeling notebook. Lastly, I created the final presentation slides.

# The business value of the solution
Nearly $2.9 M in potential profits were lost due to cart abandonment during the year we analyzed. A successful solution will enable Swire Coca-Cola to reduce revenue leakage by increasing the percentage of customers who complete their orders. By identifying key behavioral patterns and addressing issues in the ordering process, Swire can strengthen customer engagement and loyalty while maximizing recurring revenue from existing accounts. Our solution pinpoints the specific behavioral patterns that precede abandonment, and delivered specific UI enhancements that could improve order completion for each group.

# Difficulties that my group encountered along the way
## Defining Abandoned and Recovered Carts: 
It was hard to define abandoned and recovered carts within this project. While the Swire team had a guide to define these, it was still vital that the definition we chose reflected the rest of our analysis. Creating a flag for abandoned and recovery involved doing a lot of data cleaning to ensure consistency among time stamps. It was also important that the right event names were chosen to identify whether a cart was completed, abandoned, or recovered.

## Processing large datasets with limited computational resources: 
Specifically when tagging the GA data with order window information, our Colab Notebooks would crash easily. We had to temporarily use a more expensive compute option, then save the data to a csv to use in our analysis going forward.

## Potential Train-Test contamination when building and evaluating predictive models: 
When we created a random forest on the event TF-IDF matrix, we found suspiciously high performance (AUC-ROC of 0.92). To prevent potentail data leakage, we rebuilt the classification pipeline so that we could pass in a corpus of events/order windows, then apply cross-validation splits before fitting a TF-IDF vectorizor on the training set. We also made sure not to include any events in the corpus that would "give away" whether a cart was abandoned. i.e. `purchase_success`, `order_placed`, etc.

# What I learned in the project
- I learned that it's best to use everyone's strenghts instead of learning all of the tools from scratch. Using our strengths collaboratively helped us be more efficient and ultimately do a better job.

- Taking a creative approach to a business problem can deliver high-quality, actionable insights.
  
- I learned a lot from my classmates. Their ideas were fantastic and helped me to have a broader mindset approaching and working on this project.
