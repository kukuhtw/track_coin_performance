
<?php

$key_botmantul="xxxxxxxxxxxxxxxxxxxxx"; // isi dengan data key botmantul.id anda
$secretKey_botmantul="zzzzzzzzzzzzzzzzzzzzzz"; // isi dengan data secretkey botmantul anda
$API_HOST="https://botmantul.id/crypto/API_getInfoPerformanceCoin.php";

$base64encdode = base64_encode($key_botmantul.$secretKey_botmantul);

   $headers = array();
    $headers[] = 'Content-Type: application/json';
    $headers[] = 'Accept: application/json';
    $headers[] = 'Client-ID: '.$key_botmantul;
    $headers[] = 'Pass-Key: '.$secretKey_botmantul;

     $ch = curl_init($API_HOST);
    //echo "<br>API_HOST=".$API_HOST;
    
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
  //  curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($postData));
    
    $content = curl_exec($ch);
    //$content = preg_replace('/[\x00-\x1F\x80-\xFF]/', '', $content);
    curl_close($ch);
   
    $json = json_decode($content, true);

    //echo "<br>json: ".$json;
    //echo "<br>content results = ".$content;
  	//echo "<br>jumlah_data  = ".  $jumlah_data;
    
      $status = $json["status"];
   // echo "<br>status  = ".  $status;
     if ($status!="200") {
      $messages = $json["messages"];
      echo "<br>".$messages;
      exit;
    }
     $hits = $json["hits"];
     $maxhits = $json["maxhits"];
    $jumlah_data = count($json["detail"]);
	  
      echo "<h1>Performance coin 2 jam terakhir !</h1>";
      for ($i=0;$i<$jumlah_data;$i++) {
 		$rank = $json["detail"][$i]["rank"];
 		$symbol = $json["detail"][$i]["symbol"];
 		$harga_updated = $json["detail"][$i]["harga_updated"];
 		$harga_updated_f = number_format($harga_updated);
 		$harga_last2hour = $json["detail"][$i]["harga_last2hour"];
 		$harga_last2hour_f = number_format($harga_last2hour);
 		$waktu_updated = $json["detail"][$i]["waktu_updated"];
 		$waktu_updated_desc = $json["detail"][$i]["waktu_updated_desc"];
 		
 		$waktu_last2hour = $json["detail"][$i]["waktu_last2hour"];
 		$waktu_last2hour_desc = $json["detail"][$i]["waktu_last2hour_desc"];
 		$profitloss = $json["detail"][$i]["profitloss"];

 		echo "<br>".$rank." . ".$symbol. " growth : ".$profitloss. " %";
		echo "<br>harga Rp ".$harga_updated_f." -> ".$waktu_updated_desc;
		echo "<br>harga Rp ".$harga_last2hour_f." -> ".$waktu_last2hour_desc;
		echo "<br>";		



      }

   echo "<br>hits : =".$hits;
   echo "<br>maxhits : =".$maxhits;
  
 ?>
