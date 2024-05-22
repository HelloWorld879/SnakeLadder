body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f2f2f2;
}

.container {
    max-width: 600px;
    margin: 50px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 5px;
}

textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}

#response {
    margin-top: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: #f9f9f9;
    white-space: pre-wrap;
}



const apiBaseUrl = 'http://localhost:8080/api';

async function verify() {
    const template = document.getElementById('template').value;
    const user = 'default_user'; // Predefined user value
    const response = await callApi('verify', template, user);
    displayResponse(response);
}

async function post() {
    const template = document.getElementById('template').value;
    const user = 'default_user'; // Predefined user value
    const response = await callApi('post', template, user);
    displayResponse(response);
}

async function callApi(action, template, user) {
    const url = `${apiBaseUrl}/${action}?user=${encodeURIComponent(user)}`;
    const options = {
        method: 'POST',
        headers: {
            'Content-Type': 'text/plain'
        },
        body: template
    };
    try {
        const response = await fetch(url, options);
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return await response.json();
    } catch (error) {
        console.error('Error:', error);
        return `Error: ${error.message}`;
    }
}

function displayResponse(response) {
    const responseDiv = document.getElementById('response');
    responseDiv.textContent = JSON.stringify(response, null, 2);
}
