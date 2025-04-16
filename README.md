Got it! Here is the updated `README.md` content with the corrected project name as `# customer-review-`:

---

```markdown
# customer-review-

A crawler to collect reviews and product information on **Amazon.com** and save them to **SQLite** databases.

---

## 🚀 Quick Start Guide

### ✅ Get Reviews from One Product

To get all reviews for a product:

1. Find the **ASIN** (Amazon Standard Identification Number) of the product.  
   It’s the 10-character alphanumeric ID found in the URL:  
   `https://www.amazon.com/dp/<ASIN>`  
   
2. Use the following code:

```java
Item samsungTab3 = new Item("B00D02AGU4");
samsungTab3.fetchReview();
samsungTab3.writeReviewsToDatabase("reviewtest.db", false);
```

📌 You can manage/export the SQLite database using [SQLiteStudio](https://sqlitestudio.pl/) or [RSQLite](https://cran.r-project.org/web/packages/RSQLite/index.html).

---

### 👤 Get Reviewer Information

```java
GetReviewerInfo reviewer_crawler = new GetReviewerInfo("reviewer_ids.txt", "reviewer_test.db");
reviewer_crawler.crawl();
```

- `reviewer_ids.txt` contains the list of reviewer IDs.
- `reviewer_test.db` is the output SQLite database.

---

### 📦 Get Reviews from a Product Category

1. Identify the **Node ID** from a category URL (`&node=...`).
2. Use the following code:

```java
GetASINbyNode getIDs = new GetASINbyNode("541966%2C1232597011", 1, 10);
getIDs.getIDList();
getIDs.writeIDsToCSV("idlist.txt");

ItemList thelist = new ItemList("idlist.txt");
thelist.writeReviewsToDatabase("reviews.db", false);
```

> The third argument to `GetASINbyNode()` is usually `estimated_number_of_products / 5`.

---

### 💰 Get Pricing Information

1. Register as an Amazon Associate: [Affiliate Program](https://affiliate-program.amazon.com)
2. Add your Associate Tag in `signInput()` in `Item.java`:

```java
variablemap.put("AssociateTag", "your_tag_here");
```

3. Add your Product Advertising **API Key** & **Secret Key** in `SignedRequestsHelper.java`:

```java
private String awsAccessKeyId = "your_api_key";
private String awsSecretKey = "your_secret_key";
```

4. Set the second argument of `writeReviewsToDatabase()` to `true`:

```java
Item testItem = new Item("B00D02AGU4");
System.out.println(testItem.getXMLLargeResponse());
```

> 📦 Pricing information will be saved in the same SQLite database in **XML** format.

---

## ⚠️ Common Exceptions

- **`java.io.IOException`**  
  → Item no longer exists on Amazon.

- **`java.net.SocketTimeoutException`**  
  → Connection took too long. Rerun the crawler for affected items.

---

## 📅 Update Log

- **2015-11-14**: Updated to reflect changes on Amazon website.  
- **2016-06-25**: Amazon no longer displays the total number of helpful votes.

---

## 📝 License

The code is released into the **public domain**.

If you use this code in research, please cite:

> **"Market Dynamics and User-Generated Content about Tablet Computers"**  
> Xin (Shane) Wang, Feng Mai, Roger H.L. Chiang  
> *Marketing Science* 33.3 (2014): 449-458

---
```

Let me know if you want this in a downloadable file or if you'd like help uploading it directly to your GitHub repository!
