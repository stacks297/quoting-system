<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Instant Plumbing Quote</title>
  <style>
    body { font-family: Arial, sans-serif; background:#f6f7f9; padding:40px; }
    .card { max-width:520px; margin:auto; background:#fff; border-radius:16px; box-shadow:0 10px 30px rgba(0,0,0,.08); padding:28px; }
    h1 { font-size:22px; margin-bottom:10px; }
    p { color:#555; margin-bottom:20px; }
    label { display:block; font-weight:600; margin-top:14px; }
    select, input { width:100%; padding:10px; margin-top:6px; border-radius:8px; border:1px solid #ddd; }
    button { margin-top:22px; width:100%; padding:14px; border:none; border-radius:12px; background:#0f172a; color:#fff; font-size:16px; cursor:pointer; }
    .result { margin-top:20px; padding:16px; background:#f1f5f9; border-radius:12px; font-size:18px; }
    .small { font-size:12px; color:#666; margin-top:8px; }
  </style>
</head>
<body>
  <div class="card">
    <h1>Instant Plumbing Quote</h1>
    <p>Answer a few questions to get a price range instantly.</p>

    <label>Service Type</label>
    <select id="service">
      <option value="0">Select a service</option>
      <option value="150">Drain Cleaning</option>
      <option value="220">Leak Repair</option>
      <option value="350">Water Heater Repair</option>
      <option value="1200">Water Heater Install</option>
    </select>

    <label>Urgency</label>
    <select id="urgency">
      <option value="1">Standard (1–2 days)</option>
      <option value="1.25">Same Day</option>
      <option value="1.5">Emergency</option>
    </select>

    <label>Property Type</label>
    <select id="property">
      <option value="1">Residential</option>
      <option value="1.3">Commercial</option>
    </select>

    <button onclick="calculate()">Get My Quote</button>

    <div id="output" class="result" style="display:none"></div>
    <div class="small">*Final price confirmed after onsite inspection</div>
  </div>

  <script>
    function calculate() {
      const base = Number(document.getElementById('service').value);
      const urgency = Number(document.getElementById('urgency').value);
      const property = Number(document.getElementById('property').value);

      if (base === 0) {
        alert('Please select a service');
        return;
      }

      const estimate = Math.round(base * urgency * property);
      const low = estimate - 40;
      const high = estimate + 60;

      const output = document.getElementById('output');
      output.style.display = 'block';
      output.innerHTML = `Estimated Price Range:<br><strong>$${low} – $${high}</strong>`;
    }
  </script>
</body>
</html>
