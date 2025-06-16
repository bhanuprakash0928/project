<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>APSRTC Ticket Booking</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  margin: 0;
  background: linear-gradient(135deg, #a8e6ff, #d0efff);
  color: #333;
  
}

    

    h1, h2, h3 {
      text-align: center;
    }

    h1 {
      font-size: 42px;
      color: #0d4345;
      background-color: #95d0d2;
      padding: 20px 0;
      margin: 0;
    }

    .container {
      width: 90%;
      max-width: 1000px;
      margin: 30px auto;
      padding: 25px;
      background-color: #ffffffee;
      border-radius: 12px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
      cursor: default;
    }

    .rules {
      background-color: #f1f9f8;
      padding: 20px;
      margin-bottom: 25px;
      border-left: 5px solid #0d4345;
    }

    label {
      font-weight: bold;
      margin-top: 10px;
      display: block;
    }

    input[type="text"],
    input[type="number"],
    input[type="email"],
    input[type="tel"],
    input[type="month"],
    select {
      width: 100%;
      padding: 10px;
      border: 1px solid #aaa;
      border-radius: 6px;
      margin-top: 5px;
      font-size: 16px;
      cursor: pointer;
    }

    .passenger-section {
      border: 1px solid #ccc;
      border-radius: 10px;
      padding: 15px;
      background-color: #f0faff;
      margin-bottom: 20px;
    }

    .radio-group {
      margin: 10px 0;
    }

    .button {
      background: linear-gradient(to right, #0d4345, #128a8f);
      color: white;
      padding: 14px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 16px;
      width: 250px;
      margin: 20px auto;
      display: block;
      /* transition: all 0.3s ease; */
    }

    .button:hover {
      transform: scale(1.05);
      background-color: #10a2a9;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    .payment-methods label {
      margin-right: 20px;
    }

    a {
      color: #0d4345;
      text-decoration: underline;
    }

    a:hover {
      text-decoration: none;
    }
  </style>
</head>
<body>
<div id="max" class="max">
  <h1>APSRTC Ticket Booking</h1>

  <div class="container">
    <div class="rules">
      <h2>📋 Booking Rules</h2>
      <ul>
        <li>Book via <a href="https://www.apsrtconline.in" target="_blank">www.apsrtconline.in</a></li>
        <li>Mobile App, Counters & Authorized Agents available</li>
        <li>Advance booking allowed up to 30 days</li>
        <li>Accepted Payments: UPI, Credit/Debit Cards, Net Banking</li>
      </ul>
    </div>

    <form id="bookingForm">
      <h2>🧾 Passenger Details</h2>

      <label for="numPassengers">Select Number of Tickets:</label>
      <select id="numPassengers" name="numPassengers" required>
        <option value="">-- Select --</option>
        <option value="1">1 Ticket</option>
        <option value="2">2 Tickets</option>
        <option value="3">3 Tickets</option>
        <option value="4">4 Tickets</option>
        <option value="5">5 Tickets</option>
        <option value="6">6 Tickets</option>
      </select>

      <div id="passengerFields"></div>

      <label for="phoneNumber">Common Phone Number:</label>
      <input type="tel" id="phoneNumber" name="phoneNumber" placeholder="Enter Phone Number" required>

      <button type="submit" class="button">Submit Ticket Booking</button>
    </form>
  </div>


</div>

<script>
  const numPassengersSelect = document.getElementById("numPassengers");
  const passengerFields = document.getElementById("passengerFields");

  numPassengersSelect.addEventListener("change", () => {
    const count = parseInt(numPassengersSelect.value);
    passengerFields.innerHTML = "";

    for (let i = 1; i <= count; i++) {
      passengerFields.innerHTML += `
        <div class="passenger-section">
          <h3>Passenger ${i}</h3>
          <label for="pas${i}">Name:</label>
          <input type="text" name="pas${i}" placeholder="Enter name" required />
          <div class="radio-group">
            <label><input type="radio" name="gender${i}" value="male" required /> Male</label>
            <label><input type="radio" name="gender${i}" value="female" required /> Female</label>
          </div>
          <label for="age${i}">Age:</label>
          <input type="number" name="age${i}" placeholder="Enter age" required />
        </div>
      `;
    }
  });
</script>

</body>
</html>
