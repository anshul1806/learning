#Following is impure and againsts functional programming paradigm. 

```decimal RecomputeTotal(Order order, List<OrderLine> linesToDelete)
{
   var result = 0m;
   foreach (var line in order.OrderLines)
      if (line.Quantity == 0) linesToDelete.Add(line);
      else result += line.Product.Price * line.Quantity;
   return result;
}
```
You can convert this to pure by returning the values that don't modify the state of input variables.

```
(decimal, IEnumerable<OrderLine>) RecomputeTotal(Order order)
  => (order.OrderLines.Sum(l => l.Product.Price * l.Quantity)
    , order.OrderLines.Where(l => l.Quantity == 0));
 ```
    
 ### this is first line of the code
 
 Basic doctrine for FP
 Avoid mutating outside state in a function.
 
