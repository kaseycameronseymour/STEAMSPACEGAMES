<?php

    require_once "vendor/autoload.php";
    use Twilio\Rest\Client;
    
    // Step 2: set our AccountSid and AuthToken from https://twilio.com/console
    $AccountSid = "AC653c68afd3a74df7c00307fc7f2e8ab9";
    $AuthToken = "47e334d3d282c1bb5d3befa2a3ff743b";
    // Step 3: instantiate a new Twilio Rest Client
    $client = new Client($AccountSid, $AuthToken);
    // Step 4: make an array of people we know, to send them a message. 
    // Feel free to change/add your own phone number and name here.
    $people = array(
        "+16232951474" => "Kasey Seymour",
       
    );
    // Step 5: Loop over all our friends. $number is a phone number above, and 
    // $name is the name next to it
    foreach ($people as $number => $name) {
        $sms = $client->account->messages->create(
            // the number we are sending to - Any phone number
            $number,
            array(
                // Step 6: Change the 'From' number below to be a valid Twilio number 
                // that you've purchased
                'from' => "+17082610204 ", 
                
                // the sms body
                'body' => "Hey $name, Monkey Party at 6PM. Bring Bananas!"
            )
        );
        // Display a confirmation message on the screen
        echo "Sent message to $name";
    }
