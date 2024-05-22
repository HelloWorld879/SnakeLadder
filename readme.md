/* Add this CSS to your existing styles.css file */

.container {
    max-width: none; /* Remove max-width */
    width: 100%; /* Set width to 100% */
    margin: 50px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

textarea,
input[type="text"],
button {
    width: calc(100% - 22px); /* Subtract padding and border width */
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

#response {
    margin-top: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: #f9f9f9;
    color: #333;
    white-space: pre-wrap;
    width: calc(100% - 22px); /* Subtract padding and border width */
}
