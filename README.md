<!DOCTYPE html>
<html>
<head>
    <title>MQTT Subscriber</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/paho-mqtt/1.1.0/mqttws31.min.js"></script>
</head>
<body>
    <h1>MQTT Subscriber</h1>

    <script>
        var broker = 'mqtt://178.232.251.168:1883';
        var client = new Paho.MQTT.Client(broker, 'clientId');

        client.connect({
            onSuccess: onConnect,
            onFailure: onFailure
        });

        function onConnect() {
            console.log("Connected to MQTT broker");
            client.subscribe("your/topic");
        }

        function onFailure(err) {
            console.error("Failed to connect to MQTT broker", err);
        }

        client.onMessageArrived = function(message) {
            console.log("Received message: " + message.payloadString);
            // Handle the incoming message here
        };
    </script>
</body>
</html>

