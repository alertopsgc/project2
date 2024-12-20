<script lang="ts">
  const rightImage = "./imgs/3.png";
  let showSuccessMessage = false;

  function handleSubmit(event: Event) {
    event.preventDefault(); // Prevent page refresh on form submission

    // Display the success message
    showSuccessMessage = true;

    // Hide success message after 3 seconds
    setTimeout(() => {
      showSuccessMessage = false;
    }, 3000);

    // Clear all input fields in the form
    const form = event.target as HTMLFormElement;
    form.reset();
  }
</script>


<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: Arial, sans-serif;
    background-color: #f9f9f9;
    color: #333;
  }

  /* Flex container for image and form */
  .flex-container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 2rem;
    padding: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  /* Image section styling */
  .image-section {
    flex: 1;
    display: flex;
    align-items: center;
    justify-content: left;
  }

  .image-section img {
    width: 500px;
    height: auto;
    border-radius: 8px;
    object-fit: contain;
  }

  /* Container for form */
  .container {
    flex: 1;
    max-width: 500px;
    padding: 2rem;
    background-color: #ffffff;
    border-radius: 8px;
    font-style: inherit;
  }

  h1 {
    color: #d9534f; /* Red color */
    font-size: 30px;
    text-align: center;
    margin-bottom: 1.5rem;
    font-weight: bolder;
    font-style: inherit;
  }

  label {
    display: block;
    font-size: 0.9rem;
    margin-bottom: 0.5rem;
  }

  input[type="text"],
  input[type="tel"],
  input[type="number"],
  input[type="datetime-local"],
  select {
    width: 100%;
    padding: 0.8rem;
    margin-bottom: 1.5rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
  }

  input[type="file"] {
    margin-top: 0px;
    margin-bottom: 1rem;
  }

  .button-container {
    display: flex;
    justify-content: center;
    margin-top: 1rem;
  }

  button {
    background-color: #020a2c;
    color: white;
    padding: 0.8rem 2.5rem;
    font-size: 1rem;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.3s;
  }

  button:hover {
    background-color: #29384B;
  }

  /* Responsive styling */
  @media (max-width: 768px) {
    .flex-container {
      flex-direction: column;
      padding: 1rem;
    }

    .image-section {
      margin-bottom: 1.5rem;
    }

    h1 {
      font-size: 2rem;
    }

    input[type="text"],
    input[type="tel"],
    input[type="number"],
    input[type="datetime-local"],
    select {
      font-size: 1.1rem;
    }

    .button-container {
      margin-top: 2rem;
    }

    button {
      font-size: 1.1rem;
    }

    .image-section {
      display: none;
    }
  }

  @media (max-width: 480px) {
    h1 {
      font-size: 1.8rem;
    }

    .container {
      padding: 1.5rem;
    }

    input[type="text"],
    input[type="tel"],
    input[type="number"],
    input[type="datetime-local"],
    select {
      font-size: 1rem;
    }

    button {
      font-size: 1rem;
      padding: 0.8rem 2rem;
    }
  }

  .success-message {
    background-color: #d4edda;
    color: #155724;
    border: 1px solid #c3e6cb;
    padding: 0.5rem 1rem;
    border-radius: 5px;
    margin-top: 1rem;
    text-align: center;
    font-weight: bold;
  }

  /* Modal styling */
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
  }

  .modal-content {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    max-width: 500px;
    text-align: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }

  .modal-content h2 {
    color: #d9534f;
    margin-bottom: 1rem;
  }

  .modal-content p {
    margin-bottom: 1.5rem;
  }

  .modal-content button {
    background-color: #020a2c;
    color: white;
    padding: 0.8rem 2.5rem;
    font-size: 1rem;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.3s;
  }

  .modal-content button:hover {
    background-color: #29384B;
  }
</style>

<div class="flex-container">
  <div class="image-section">
    <img src={rightImage} alt="Illustration">
  </div>

  <div class="container">
    <h1>What's your Emergency?</h1>

    <form on:submit={handleSubmit}>
      <!-- <form> -->
      <div style="display: flex; gap: 1rem;">
        <div style="flex: 1;">
          <label for="first-name">First Name</label>
          <input id="first-name" type="text" placeholder="Enter first name" required />
        </div>
        <div style="flex: 1;">
          <label for="last-name">Last Name</label>
          <input id="last-name" type="text" placeholder="Enter last name" required />
        </div>
      </div>

      <label for="contact">Contact</label>
      <input id="contact" type="tel" placeholder="Enter contact number" pattern="[0-9]*" inputmode="numeric" required />

      <label for="address">Address</label>
      <input id="address" type="text" placeholder="Enter current location" required />

      <div style="display: flex; gap: 1rem;">
        <div style="flex: 1;">
          <label for="type">Type of Emergency</label>
          <select id="type" required>
            <option value="">Select type</option>
            <option value="fire">Fire</option>
            <option value="medical">Medical</option>
            <option value="police">Police</option>
            <option value="disaster">Natural Disaster</option>
          </select>
        </div>
        <div style="flex: 1;">
          <label for="assistance">Assistance Needed</label>
          <select id="assistance" required>
            <option value="">Select assistance</option>
            <option value="ambulance">Ambulance</option>
            <option value="rescue">Rescue</option>
            <option value="police">Police</option>
          </select>
        </div>
      </div>

      <div style="display: flex; gap: 1rem;">
        <div style="flex: 1;">
          <label for="urgency">Level of Urgency</label>
          <select id="urgency" required>
            <option value="">Select urgency</option>
            <option value="high">High</option>
            <option value="medium">Medium</option>
            <option value="low">Low</option>
          </select>
        </div>
        <div style="flex: 1;">
          <label for="people">No. of People Affected</label>
          <input id="people" type="number" min="1" placeholder="Enter number" required />
        </div>
      </div>

      <label for="datetime">Date and Time of Incident</label>
      <input id="datetime" type="datetime-local" required />

      <label for="image">Attach Image</label>
      <input id="image" type="file" />

      <div class="button-container">
        <button type="submit">Submit</button>
      </div>


      {#if showSuccessMessage}
        <div class="success-message">
          Your emergency report has been submitted successfully!
        </div>
      {/if}

    </form>
  </div>
</div>
<!-- 
{#if showModal}
  <Modal on:close={() => (showModal = false)}>
    <h3 slot="header" class="text-xl font-semibold text-gray-900">Emergency Submitted</h3>
    <div slot="default" class="text-base leading-relaxed text-gray-500">
      Your emergency report has been submitted successfully. Help is on the way!
    </div>
    <div slot="footer" class="flex justify-end">
      <button on:click={() => (showModal = false)} class="btn btn-primary">Close</button>
    </div>
  </Modal>
{/if} -->

