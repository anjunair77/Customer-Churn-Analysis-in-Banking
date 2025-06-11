
CREATE TABLE customers (
    customer_id INTEGER PRIMARY KEY,
    age INTEGER,
    gender TEXT,
    tenure_years INTEGER,
    account_balance REAL,
    num_products INTEGER,
    has_credit_card INTEGER,
    is_active_member INTEGER,
    estimated_salary REAL,
    churn INTEGER
);

-- 1. Overall churn rate
SELECT 
    COUNT(*) AS total_customers,
    SUM(churn) AS total_churned,
    ROUND(AVG(churn) * 100, 2) AS churn_rate_percent
FROM customers;

-- 2. Churn by gender
SELECT 
    gender,
    COUNT(*) AS total,
    SUM(churn) AS churned,
    ROUND(AVG(churn) * 100, 2) AS churn_rate_percent
FROM customers
GROUP BY gender;

-- 3. Churn by tenure
SELECT 
    tenure_years,
    COUNT(*) AS total,
    SUM(churn) AS churned,
    ROUND(AVG(churn) * 100, 2) AS churn_rate_percent
FROM customers
GROUP BY tenure_years
ORDER BY tenure_years;

-- 4. Churn by active membership
SELECT 
    is_active_member,
    COUNT(*) AS total,
    SUM(churn) AS churned,
    ROUND(AVG(churn) * 100, 2) AS churn_rate_percent
FROM customers
GROUP BY is_active_member;

-- 5. Churn by number of products
SELECT 
    num_products,
    COUNT(*) AS total,
    SUM(churn) AS churned,
    ROUND(AVG(churn) * 100, 2) AS churn_rate_percent
FROM customers
GROUP BY num_products
ORDER BY num_products;


