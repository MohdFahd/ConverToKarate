<script setup>
import { ref } from "vue";
import axios from "axios"; // Import axios to make API requests

// Data references for input and output
const curlCommand = ref(""); // The cURL command input
const karateTest = ref(""); // The Karate test output
const isloading = ref(false); // The Karate test output

// Function to handle the conversion when the "Convert" button is clicked
const convertCurlToKarate = async () => {
  console.log(curlCommand.value); // Check what input is being passed
  isloading.value = true;
  try {
    // Making a POST request to the API
    const response = await axios.post(
      "https://api.qa.fastn.ai/api/v1/ConvertToKarate",
      {
        input: { crulCommand: curlCommand.value }, // Pass the cURL command as input
      },
      {
        headers: {
          "x-fastn-api-key": "2e53d60c-0a0a-485d-a8e0-171da7b75e7e", // API Key
          "Content-Type": "application/json",
          "x-fastn-space-id": "1bace0da-fcc9-4889-ac1c-d5467703371d",
          "x-fastn-space-tenantid": "",
          stage: "LIVE",
        },
      }
    );

    // Set the converted Karate test result in the second textarea
    karateTest.value = response.data.karateTest;
    isloading.value = false;
  } catch (error) {
    console.error("Error converting cURL to Karate test:", error);
    karateTest.value =
      "Conversion failed. Please check the input and try again.";
  }
};
</script>

<template>
  <div style="display: flex; justify-content: center; gap: 12px">
    <div>
      <textarea
        v-model="curlCommand"
        cols="60"
        rows="20"
        placeholder="cURL command"
      ></textarea>
    </div>
    <div>
      <textarea
        v-model="karateTest"
        cols="60"
        rows="20"
        placeholder="Karate test"
        readonly
      ></textarea>
    </div>
  </div>
  <button @click="convertCurlToKarate" :disabled="isloading">
    {{ isloading ? "Converting..." : "Convert" }}
  </button>
</template>
