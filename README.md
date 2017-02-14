# is218_1-1
<body>
    <main>
          <h1>Product Discount Calculator</h1>
          <form action="display discount.php" method="post">
        
          <div id ="data">
            <label>Product Description:</label>
            <input type="text" name="product_description"><br>
          
            <label>List Price:</label>
            <input type="text" name="list_price"><br>

            <label>Standard Discount:</label>
            <input type="text" name="discount_percent"><span>%</span><br>
          </div>

          <div id ="buttons">
            <label>&nbsp</label>
            <input type="submit" value="Calculate Discount"><br>
          </div>

      </form>    
    </main>
</body>
</html>

body {
    font-family: Arial, Helvetcica,sans-serif;
    margin: 1em;
    padding: 0;
}

main {
    width: 450px;
    margin: 0 auto;
    padding: 1.5em;
    background: white;
    border: 2px solid navy;
 }
 
 h1 {
    color: navy;
 }
 
 label {
    width: 10em;
    padding-right: 1em;
    float: left;
 }
 
 #data input {
    float: left;
    width: 15em;
    margin-bottom: .5em;
 }
 
 #data span {
    paddding-left: .25em;
 }
 
 #buttons input {
    float: left;
    margin-bottom: .5em;
 }
 
 br {
    clear: left;
 }

<?php
    // get the data from the form
    $product_description = $_POST['product_description'];
    $list_price = $_POST['list_price'];
    $discount_percent = $_POST['discount_percent'];
    
    // calculate the discount
    $discount = $list_price * $discount_percent * .01;
    $discount_price = $list_price - $discount;
    
    // apply currency formatting to the dollar and percent amounts
    $list_price_formatted = "$".number_format($list_price, 2);
    $discount_percent_formatted = $discount_percent."%";
    $discount_formatted = "$".number_format($discount, 2);
    $discount_price_formatted = "$".number_format($discount_price, 2);            
    
    // escape the unformatted input
    $product_description_escaped = htmlspecialchars($product_description);
?>
<!DOCTYPE html>
<html>
<head>
    <title>Product Discount Calculator</title>
    <link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
    <main>
        <h1>Product Discount Calculator</h1>

        <label>Product Description:</label>
        <span><?php echo $product_description_escaped; ?></span><br>

        <label>List Price:</label>
        <span><?php echo $list_price_formatted; ?></span><br>

        <label>Standard Discount:</label>
        <span><?php echo $discount_percent_formatted; ?></span><br>

        <label>Discount Amount:</label>
        <span><?php echo $discount_formatted; ?></span><br>

        <label>Discount Price:</label>
        <span><?php echo $discount_price_formatted; ?></span><br>
    </main>
</body>
</html>
