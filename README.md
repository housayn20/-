<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>موقع التعارف</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>مرحبًا بك في موقع التعارف!</h1>
        <p>أنشئ حسابك وابدأ التواصل مع الآخرين</p>
    </header>

    <section class="form-section">
        <form id="signupForm">
            <label for="name">الاسم:</label>
            <input type="text" id="name" name="name" required>

            <label for="email">البريد الإلكتروني:</label>
            <input type="email" id="email" name="email" required>

            <label for="gender">الجنس:</label>
            <select id="gender" name="gender">
                <option value="male">ذكر</option>
                <option value="female">أنثى</option>
            </select>

            <label for="age">العمر:</label>
            <input type="number" id="age" name="age" required>

            <button type="submit">إنشاء حساب</button>
        </form>
    </section>

    <script src="scripts.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    text-align: center;
}

header {
    background-color: #4CAF50;
    color: white;
    padding: 20px;
}

.form-section {
    margin: 20px auto;
    width: 50%;
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin-bottom: 5px;
    font-weight: bold;
}

input, select {
    margin-bottom: 10px;
    padding: 8px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

button {
    padding: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}
document.getElementById('signupForm').addEventListener('submit', function(event) {
    event.preventDefault(); // منع إعادة تحميل الصفحة

    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const gender = document.getElementById('gender').value;
    const age = document.getElementById('age').value;

    // إرسال البيانات إلى الخادم
    fetch('/signup', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            name: name,
            email: email,
            gender: gender,
            age: age
        }),
    })
    .then(response => response.json())
    .then(data => {
        alert('تم إنشاء الحساب بنجاح!');
    })
    .catch(error => {
        console.error('حدث خطأ:', error);
    });
});
