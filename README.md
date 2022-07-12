![image](https://user-images.githubusercontent.com/91864024/178474510-ae55a5d1-2039-41ab-a82f-1b48fcea9d4e.png)
# Tiki Online Retail Recommendation System
## I. Outline
- This Recommendation System is built based on a dataset crawled on Tiki Vietnam (https://tiki.vn).
- The demo app is implemented on Heroku, available for your experience:
https://tiki-recommended-system.herokuapp.com/
## II. Business Objective/ Problem
- Tiki is an "all in one" commerce ecosystem, including tiki.vn, which is an e-commerce website ranked top 2 in Vietnam, top 6 in Southeast Asia.
- This platform has implemented many utilities to enhance user experience and now they want to build more.
- This user recommendation system is built on that request
## III. Project implementation
### 1. Business Understanding
Based on the above description => identify the problem:
- Build a Recommendation System for one or several groups of goods on tiki.vn to help make recommendations and suggestions for users/customers.
- Proposed models: 
 1. Content-based filtering (recommendation based on the similarity of products for each user)
 2. Collaborative filtering (recommendation based on the similarity of other users)
 ![image](https://user-images.githubusercontent.com/91864024/178473628-60208dd9-a151-4384-b652-50679c14b1a7.png)
### 2. Data Understanding/ Acquire
There are 2 files (csv format) that contained:
1. ProductRaw.csv: information about the products
2. ReviewRaw.csv: information about customers and ratings for these products.

The file **ProductRaw.csv** contained below columns:
- item_id: products's id
- name: products' name
- description: products's description
- price: product's price after apply discount
- list_price: product's true price
- rating: product's rating average
- brand: product's brand
- group: type of product
- url: the url to the webpage product
- img: the link to the image of the product

The file **ReviewRaw.csv** contained below columns:
- customer_id: Customer's id
- product_id: Product's id
- name: customer's last name
- full_name: customer's full name
- create_time: the time when the record was created
- rating: the number of star was rated in range (1 - 5)
- title: title of the review
- content: content of the review
### 3. Build model
- TFIDF to find the similarity between products then recommend to users.
- Collaborative filtering to find similarity between users and recommend the products that they may be interested.
- Applied model:
  - Cosine similarity
  - Gensim
  - Spark ALS
  - SVD
### 4. User interface
You can connect to the demo app (https://tiki-recommended-system.herokuapp.com/) for your experience. Below image show welcome screen:
![image](https://user-images.githubusercontent.com/91864024/178523545-8f59e795-e3db-4d77-aeed-ce403d29cd67.png)
**1. Content-based filtering**

- By default, Content-based filtering is entered. You can either select one product from drop-box on the left, or type some words to describe one product (please type product name in Vietnamese, e.g: máy tính bảng, tai nghe bluetooth, ...)
- Note: you can only select one product from drop-box or type one description for a product at the time.
- Some photos for these options as following:
![image](https://user-images.githubusercontent.com/91864024/178524873-e2558f39-9060-4452-8a5f-716107807f32.png)
![image](https://user-images.githubusercontent.com/91864024/178524979-56ef73af-fed0-4a2e-80ba-d31ae1d74b39.png)
**2. Collaborative filtering**

When you select Collaborative filtering, you can choose customer_id from the drop-box on the left to track history invoice of user and products that he/ she may be interested in.
![image](https://user-images.githubusercontent.com/91864024/178525748-9c27dbab-72fc-4a6f-94aa-dfdc1bbab72f.png)
### 5. Conclusion
- Model can recommend to user the products based on his behavior or other people interests.
- However, new users or new products can not be updated to model in realtime. New data must be crawled periodically and re-build model to update changes.

Thank you for your experience with my application. Hope you enjoy it!
