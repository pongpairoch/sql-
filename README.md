"# sql-"

-- <h1> 2.3 ระบุหมายเลขคำสั่งซื้อและยอดรวมของยอดขายสำหรับคำสั่งซื้อทั้งหมด ตั้งชื่อคอลัมน์ยอดขายทั้งหมดเป็น "total_amount </h1>
2.3 List the order number and the total amount of sales for all orders. Name the total amount of sales column to “total_amount”.

<h3>
select orderNumber, sum(quantityOrdered * priceEach) as total_amount
from orderdetails 
group by orderNumber ;
</h3>

 <h1>2.4 ระบุหมายเลขคำสั่งซื้อและยอดรวมของยอดขายของคำสั่งซื้อทั้งหมดที่ยอดรวมของยอดขายมากกว่า 55000 ตั้งชื่อคอลัมน์ยอดรวมของยอดขายเป็น "total_amount" </h1>
 2.4 List the order number and the total amount of sales of all orders that their total amount of sales is more than 55000. Name the total amount of sales column to “total_amount”.

<h3>
select orderNumber, sum(quantityOrdered * priceEach) as total_amount
from orderdetails 
group by orderNumber
having total_amount > 55000
  </h3>


<h1> 2.5 ระบุชื่อลูกค้าและ  (จำนวน คือ count)  คำสั่งขายของลูกค้าทั้งหมดที่มีชื่อขึ้นต้นด้วยตัวอักษร 'D' ตั้งชื่อจำนวนคอลัมน์ใบสั่งขายเป็น “num_orders” </h1>
2.5 List the customer name and the number of sales orders of all customers whose name start with the letter ‘D’. Name the number of sales orders column to “num_orders”.

<h3>
select c.customerName, count(o.orderNumber) as num_orders
from customers c join orders o on c.customerNumber = o.customerNumber
where customerName like 'D%'
group by customerName;
 </h3>


<h1>ระบุชื่อลูกค้าและจำนวนใบสั่งขายของลูกค้าทั้งหมดที่อาศัยอยู่ในประเทศที่ชื่อว่า USA และจำนวนใบสั่งขายมากกว่า 10 ตั้งชื่อคอลัมน์จำนวนใบสั่งขายเป็น "num_orders"    ใช้ where กับ having</h1>
<h3>List the customer name and the number of sales orders of all customers who live in the country named USA and the number of sales orders is greater than 10. Name the number of sales orders column to “num_orders”.</h3>
<h3>
select c.customerName, count(o.orderNumber) as num_orders
from customers c join orders o on c.customerNumber = o.customerNumber
where country = 'USA' 
group by customerName
having num_orders > 10;
 </h3>


<h1>ระบุชื่อผลิตภัณฑ์ ราคา และปริมาณการสั่งซื้อของหมายเลขคำสั่งซื้อ 10124 จัดเรียงผลลัพธ์ตามลำดับจากน้อยไปมากตามชื่อผลิตภัณฑ์</h1>
\
select p.productname,o.priceEach,o.quantityOrdered
from orderdetails o join products p on o.productCode = p.productCode
where orderNumber = '10124'
group by productname 
order by productName asc;

--Ans1select productname,  priceeach, quantityordered
from products p join orderdetails od on p.productcode = od.productcode
join orders o on od.ordernumber = o.ordernumber
where o.ordernumber = 10124
order by productname;\
