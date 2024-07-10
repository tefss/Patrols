<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Patrol Check</title>
    <script>
        // Function to get the current date and time
        function getCurrentDateTime() {
            const now = new Date();
            return now.toLocaleString();
        }

        // Function to get URL parameters
        function getUrlParameter(name) {
            name = name.replace(/[\[]/, '\\[').replace(/[\]]/, '\\]');
            const regex = new RegExp('[\\?&]' + name + '=([^&#]*)');
            const results = regex.exec(location.search);
            return results === null ? '' : decodeURIComponent(results[1].replace(/\+/g, ' '));
        }

        // Function to update the WhatsApp link with form information
        function updateWhatsAppLink() {
            const place = document.getElementById('place').value;
            const name = document.getElementById('name').value;
            const datetime = document.getElementById('datetime').value;

            const message = `Place: ${place}%0AName: ${name}%0ADTG: ${datetime}`;
            const phoneNumber = '+9647861708695';
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

        // Set the current date and time and the place on page load
        window.onload = function() {
            const place = getUrlParameter('place');
            if (place) {
                document.getElementById('place').value = place;
            }
            document.getElementById('datetime').value = getCurrentDateTime();
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
