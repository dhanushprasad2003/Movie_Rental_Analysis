# 🎬 Movie Rental Analysis Project

A beginner-friendly **data analysis project** that explores a movie rental database using Python, Pandas, Matplotlib, and Seaborn.

---

## 📌 Project Overview

This project analyzes a movie rental dataset consisting of **15 relational CSV tables** (actor, address, category, city, country, customer, film, film_actor, film_category, inventory, language, payment, rental, staff, store). The analysis covers the full data pipeline — from loading and cleaning to merging, computing KPIs, and visualizing insights.

---

## 🗂️ Dataset

All data files are located in the `movie_dataset/` directory:

| Table           | Rows    | Description                        |
|-----------------|---------|------------------------------------|
| actor           | 200     | Actor information                  |
| address         | 603     | Address details                    |
| category        | 16      | Film genre categories              |
| city            | 600     | City names                         |
| country         | 109     | Country names                      |
| customer        | 599     | Customer profiles                  |
| film            | 1,000   | Film metadata (title, rating, etc.)|
| film_actor      | 5,462   | Film ↔ actor mapping               |
| film_category   | 1,000   | Film ↔ category mapping            |
| inventory       | 4,581   | Inventory items per store          |
| language        | 6       | Language options                   |
| payment         | 16,049  | Payment transactions               |
| rental          | 16,044  | Rental records                     |
| staff           | 2       | Staff members                      |
| store           | 2       | Store locations                    |

---

## 🔧 Technologies Used

- **Python 3**
- **Pandas** — data manipulation and analysis
- **Matplotlib** — static visualizations
- **Seaborn** — statistical data visualization
- **Jupyter Notebook** — interactive development environment

---

## 📊 Analysis Workflow

### 1. Data Loading
All 15 CSV files are loaded into individual DataFrames and a quick row-count summary is printed.

### 2. Data Exploration
Preview key tables (`payment`, `rental`, `film`) and check for duplicate primary keys.

### 3. Data Cleaning & Preparation
- Convert date columns (`payment_date`, `rental_date`, `return_date`) to `datetime` dtype.
- Identify 183 rentals with missing return dates.
- Drop the entirely-null `original_language_id` column from the film table.

### 4. Feature Engineering
- **`payment_month`** — extract the month/year period from each payment.
- **`rental_days`** — compute the rental duration in days.
- **`rental_day_of_week`** — extract the weekday name from each rental.

### 5. Table Merging
Build a master DataFrame through 5 sequential merges:

1. `payment` + `rental` → add rental details  
2. + `customer` → add customer name & email  
3. + `inventory` → link to `film_id`  
4. + `film` → add title, rating, rental rate, etc.  
5. + `film_category` + `category` → add genre name  

**Final master table:** 16,049 rows × 24 columns.

### 6. Business KPIs

| KPI                    | Value         |
|------------------------|---------------|
| Total Revenue          | $67,416.51    |
| Total Rental Records   | 16,049        |
| Average Payment        | $4.20         |
| Unique Customers       | 599           |
| Unique Films Rented    | 958           |
| Avg Rental Duration    | 4.5 days      |

### 7. Visualizations

- **Distribution of Payment Amounts** — histogram  
- **Total Revenue by Month** — bar chart  
- **Number of Rentals by Movie Rating** — count plot  
- **Top 10 Genres by Revenue** — horizontal bar chart  
- **Rentals by Day of the Week** — bar chart  

---

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/dhanushprasad2003/Movie_Rental_Analysis.git
   cd study
   ```

2. **Install dependencies:**
   ```bash
   pip install pandas matplotlib seaborn jupyter
   ```

3. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook Movie_Rental_Analysis_Project.ipynb
   ```

4. **Run all cells** to reproduce the analysis and visualizations.

---

## 📁 Project Structure

```
study/
├── movie_dataset/          # 15 CSV data files
│   ├── actor.csv
│   ├── address.csv
│   ├── category.csv
│   ├── city.csv
│   ├── country.csv
│   ├── customer.csv
│   ├── film.csv
│   ├── film_actor.csv
│   ├── film_category.csv
│   ├── inventory.csv
│   ├── language.csv
│   ├── payment.csv
│   ├── rental.csv
│   ├── staff.csv
│   └── store.csv
├── Movie_Rental_Analysis_Project.ipynb   # Main analysis notebook
└── README.md               # This file
```

---

## 📝 Key Insights

- **Sports** is the top-grossing genre ($5,314), followed by **Sci-Fi** and **Animation**.
- **PG-13** is the most rented rating category.
- **Karl Seal** is the highest-spending customer ($221.55).
- **Bucket Brotherhood** is the most-rented movie (34 rentals).
- Rental activity is fairly consistent across all days of the week.

---

## 👤 Author

**Dhanush Prasad**  
[GitHub](https://github.com/dhanushprasad2003)

---

## 📄 License

This project is for educational purposes.
