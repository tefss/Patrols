<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Patrol Check - Location 1</title>
    <script>
        // Function to get the current date and time
        function getCurrentDateTime() {
            const now = new Date();
            return now.toLocaleString();
        }

        // Function to update the WhatsApp link with form information
        function updateWhatsAppLink() {
            const place = document.getElementById('place').value;
            const name = document.getElementById('name').value;
            const datetime = document.getElementById('datetime').value;

            const message = `Place: ${place}%0AName: ${name}%0ADTG: ${datetime}`;
            const phoneNumber = '+9647864006507';
            const whatsappURL = `https://api.whatsapp.com/send?phone=${phoneNumber}&text=${message}`;

            // Update the WhatsApp link
            document.getElementById('whatsappLink').href = whatsappURL;
        }

        // Function to be called when the form is submitted
        function sendWhatsAppMessage() {
            const name = document.getElementById('name').value;
            if (!name) {
                alert('Please enter your name.');
                return;
            }

            // Update the WhatsApp link with the form information
            updateWhatsAppLink();

            // Open the WhatsApp link in a new tab
            window.open(document.getElementById('whatsappLink').href, '_blank');
        }

        // Set the current date and time on page load
        window.onload = function() {
            document.getElementById('datetime').value = getCurrentDateTime();
            document.getElementById('place').value = "Location 1";
        };
    </script>
</head>
<body>
    <form onsubmit="return false;">
        <label for="place">Place:</label><br>
        <input type="text" id="place" name="place" readonly><br><br>
        
        <label for="name">Name:</label><br>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="datetime">Date & Time:</label><br>
        <input type="text" id="datetime" name="datetime" readonly><br><br>
        
        <a id="whatsappLink" href="#" onclick="sendWhatsAppMessage()">Check</a>
    </form>
</body>
</html>
