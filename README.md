# database
## Запрос sql material
```sql
insert into Material(Title,MaterialTypeID,CountInPack,Unit,CountInStock,MinCount,Cost)
Select  pk.[Наименование материала],pt.ID,pk.[ Количество в упаковке],pk.[ Единица измерения],pk.[ Количество на складе],pk.[ Минимальный возможный остаток],pk.[ Стоимость]
from
MaterialType pt,
Лист1$materials_short_k_import pk
where pt.Title=pk.[ Тип материала]
```
   
   
## Запрос sql MaterialType
```sql
Insert into MaterialType(Title)
select distinct [ Тип материала] from Лист1$materials_short_k_import
```

## Запрос sql Product
```sql
insert into [dbo].[Product]([Title],[ProductTypeID],[ArticleNumber],[Image],[ProductionPersonCount],[ProductionWorkshopNumber],[MinCostForAgent])
select [Наименование продукции],PT.ID,[Артикул],[Изображение],[Количество человек для производства],[Номер а для производства],[Минимальная стоимость для агента]
from [dbo].[products_k_import] PAI,
ProductType PT
Where PT.Title=PAI.[Тип продукции]
```


## Запрос sql productmaterial
```sql
insert into [dbo].[ProductMaterial]([ProductID],[MaterialID],Count)
select p.id,m.id,[Необходимое количество материала]
FROM [dbo].[productmaterial_k_import] pm,
Material M,
Product P
Where p.Title=pm.Продукция and m.Title=pm.[Наименование материала]
```

## Запрос sql  ProductType
``` sql
insert into  ProductType(Title) 
    select distinct [Тип продукции] from products_k_import
    ```
