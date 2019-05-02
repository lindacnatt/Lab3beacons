<template>
<head>
    <meta charset="UTF-8">
    <title>title</title>
  </head>
  <body>
    <script src="https://cdn.pubnub.com/sdk/javascript/pubnub.4.21.7.js"></script>
    <!-- Instantiate PubNub -->
    <script type="text/javascript">
    var pubnubDemo = new PubNub({
    
    publishKey: 'pub-c-7ab40221-08ea-4c9e-a5ed-8de98c8d5253',
    
    subscribeKey: 'sub-c-40c01cfe-6c46-11e9-81d5-56c3556875f9'
    
    });
    pubnubDemo.addListener({
        message: function(message){
        console.log(message)
        }
    })

    pubnubDemo.subscribe({
    channels: ['demo_tutorial']
    });

    pubnubDemo.publish({ message: { "color" : "blue" }, channel: 'demo_tutorial' });
    </script>
    <script>
        // Get event data
        function deviceOrientationListener(event) {
            var alpha   = event.alpha; //z axis rotation [0,360)
            var beta     = event.beta; //x axis rotation [-180, 180]
            var gamma   = event.gamma; //y axis rotation [-90, 90]
        
        
        
        
            //Check if absolute values have been sent
            if (typeof event.webkitCompassHeading !== "undefined") {
            alpha = event.webkitCompassHeading; //for iOS devices
            var heading = alpha
            document.getElementById("heading").innerHTML = heading.toFixed([0]);
            }
            else {
            alert("Your device is reporting relative alpha values, so this compass won't point north :(");
            var heading = 360 - alpha; //heading [0, 360)
            document.getElementById("heading").innerHTML = heading.toFixed([0]);
            }
        }
    </script>
    <p id=”heading”></p>
    
  </body>
    
</template>
<script>
export default {
    
}
</script>
