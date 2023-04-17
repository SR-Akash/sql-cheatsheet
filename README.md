# List Last record of each item in mysql

select s.* from pos.ItemSellingPriceRow s
join pos.ItemSellingPriceHeader h on s.HeaderId = h.HeaderId
where s.RowId = (
   select max(s2.RowId) 
   from pos.ItemSellingPriceRow s2 
   join pos.ItemSellingPriceHeader h2 on s2.HeaderId = h2.HeaderId
   where s2.ItemId = s.ItemId and h2.WarehouseId = h.WarehouseId 
);
