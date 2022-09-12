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
