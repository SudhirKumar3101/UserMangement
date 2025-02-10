# UserMangement

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Management</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <style>
        .container {
            min-height: 100vh;
        }

        .login-container,
        .signup-container {
            display: none;
        }

        .form-label {
            font-weight: bold;
        }

        .form-control {
            margin-bottom: 10px;
        }

        .error-message {
            color: red;
            font-size: 12px;
        }

        #Datatables {
            margin-top: -700px;
            /* margin-top: -400px; */
            margin-left: 100px;
            border-collapse: collapse;
        }
    </style>
</head>

<body>
    <div class="container d-flex justify-content-center align-items-center">
        <div class="col-12 col-md-6 col-lg-4">
            <!-- Login Form -->
            <div class="login-container">
                <form id="loginForm">
                    <h1 class="text-center mb-4 text-primary">Login Form</h1>
                    <div class="mb-3">
                        <label for="Email" class="form-label">Email or Username <span
                                class="text-danger">*</span></label>
                        <input type="email" class="form-control" id="loginEmail" required>
                        <div class="error-message" id="UserNameError"></div>
                    </div>

                    <div class="mb-3">
                        <label for="Password" class="form-label">Password <span class="text-danger">*</span></label>
                        <input type="password" class="form-control" id="loginPassword" required>
                        <div class="error-message" id="loginPasswordError"></div>
                    </div>

                    <div class="mb-3 form-check">
                        <input type="checkbox" class="form-check-input" id="rememberMe">
                        <label class="form-check-label" for="rememberMe">Remember me</label>
                    </div>
                    <div class="text-center mt-3">
                        <button type="button" class="btn btn-outline-primary" id="loginBtn">Login</button>
                        <button type="button" class="btn btn-outline-success " onclick="forgetfunction()">Forget
                            Password</button>
                    </div>
                    <div class="text-center mt-3">
                        <p>Don't have an account?<button type="button" class="btn btn-link"
                                id="showSignupBtn">SignUp</button></p>
                    </div>
                </form>
            </div>

            <!-- Signup Form -->
            <div class="signup-container">
                <form id="signupForm">
                    <h1 class="text-center mb-4 text-primary">Sign Up</h1>
            
                    <div class="row">
                        <div class="col-md-6 mb-3">
                            <label for="name" class="form-label">Full Name <span class="text-danger">*</span></label>
                            <input type="text" class="form-control" id="name" required>
                            <div class="error-message" id="nameError"></div>
                        </div>
            
                        <div class="col-md-6 mb-3">
                            <label for="fatherName" class="form-label">Father's Name <span class="text-danger">*</span></label>
                            <input type="text" class="form-control" id="fatherName" required>
                            <div class="error-message" id="fatherNameError"></div>
                        </div>
                    </div>
            
                    <div class="row">
                        <div class="col-md-6 mb-3">
                            <label for="signupEmail" class="form-label">Email <span class="text-danger">*</span></label>
                            <input type="email" class="form-control" id="signupEmail" required>
                            <div class="error-message" id="emailError"></div>
                        </div>
            
                        <div class="col-md-6 mb-3">
                            <label for="age" class="form-label">Age <span class="text-danger">*</span></label>
                            <input type="number" class="form-control" id="age" required>
                            <div class="error-message" id="ageError"></div>
                        </div>
                    </div>
            
                    <div class="row">
                        <div class="col-md-6 mb-3">
                            <label class="form-label">Gender <span class="text-danger">*</span></label>
                            <select class="form-control" id="gender" required>
                                <option value="">Select Gender</option>
                                <option value="male">Male</option>
                                <option value="female">Female</option>
                                <option value="other">Other</option>
                            </select>
                            <div class="error-message" id="genderError"></div>
                        </div>
            
                        <div class="col-md-6 mb-3">
                            <label for="mobileNo" class="form-label">Mobile Number <span class="text-danger">*</span></label>
                            <input type="tel" class="form-control" id="mobileNo" required>
                            <div class="error-message" id="mobileError"></div>
                        </div>
                    </div>
            
                    <div class="row">
                        <div class="col-md-6 mb-3">
                            <label for="dob" class="form-label">Date of Birth <span class="text-danger">*</span></label>
                            <input type="date" class="form-control" id="dob" required>
                            <div class="error-message" id="dobError"></div>
                        </div>
            
                        <div class="col-md-6 mb-3">
                            <label for="address" class="form-label">Address <span class="text-danger">*</span></label>
                            <textarea class="form-control" id="address" rows="3" required></textarea>
                            <div class="error-message" id="addressError"></div>
                        </div>
                    </div>
            
                    <button type="button" class="btn btn-primary form-control" id="signupBtn">Sign Up</button>
            
                    <div class="text-center mt-3">
                        <p>Already have an account? <button type="button" class="btn btn-link" id="showLoginBtn">Login here</button></p>
                    </div>
                </form>
            </div>

        </div>
    </div>

    <!-- table -->
    <div class="container" id="Datatables">
        <h2 class="text-center text-primary">UserList</h2><br>
        <table id="dataTable" class="table table-hover table-border">
            <thead>
                <tr>
                    <th>Id</th>
                    <th>FullName</th>
                    <th>Email</th>
                    <th>Gender</th>
                    <th>Mobile No.</th>
                    <th>Address</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody id="DataEnter"></tbody>
        </table>
    </div>

    <script>
        // Toggle between login and signup forms
        document.querySelector('.login-container').style.display = 'block';
        document.querySelector('.signup-container').style.display = 'none';

        document.addEventListener('DOMContentLoaded', function () {
            document.getElementById("Datatables").style.display = 'none';
        })

        document.getElementById('showSignupBtn').addEventListener('click', function () {
            document.querySelector('.login-container').style.display = 'none';
            document.querySelector('.signup-container').style.display = 'block';
        });

        document.getElementById('showLoginBtn').addEventListener('click', function () {
            document.querySelector('.signup-container').style.display = 'none';
            document.querySelector('.login-container').style.display = 'block';
        });

        // Function to validate email format
        function validateEmail(email) {
            const re = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
            return re.test(email);
        }

        // Login Button functionality
        document.getElementById('loginBtn').addEventListener('click', function () {
            debugger;
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            // Retrieve users from local storage
            const users = JSON.parse(localStorage.getItem('users')) || [];

            // Find matching user
            const user = users.find(u => u.email === email && u.password === password);

            if (user) {
                alert('Login Successful!');
                document.getElementById("Datatables").style.display = 'block';
                document.querySelector('.login-container').style.display = 'none';
                ShowDataInTable();
            } else {
                alert('Invalid credentials. Please check your email and password.');
            }
            document.getElementById('loginForm').reset();
        });

        // Handle the "Sign Up" button click
        document.getElementById('signupBtn').addEventListener('click', function () {
            const name = document.getElementById('name').value;
            const fatherName = document.getElementById('fatherName').value;
            const email = document.getElementById('signupEmail').value;
            const age = document.getElementById('age').value;
            const gender = document.getElementById('gender').value;
            const mobile = document.getElementById('mobileNo').value;
            const dob = document.getElementById('dob').value;
            const address = document.getElementById('address').value;
            document.getElementById("Datatables").style.display = 'none';
            // Clear previous error messages
            document.querySelectorAll('.error-message').forEach(el => el.textContent = '');

            let isValid = true;

            // Validate each field and show error message if empty
            if (!name) {
                document.getElementById('nameError').textContent = 'Please fill out this field.';
                isValid = false;
            }
            if (!fatherName) {
                document.getElementById('fatherNameError').textContent = 'Please fill out this field.';
                isValid = false;
            }
            if (!email) {
                document.getElementById('emailError').textContent = 'Please fill out this field.';
                isValid = false;
            } else if (!validateEmail(email)) {
                document.getElementById('emailError').textContent = 'Please enter a valid email address.';
                isValid = false;
            }
            if (!age) {
                document.getElementById('ageError').textContent = 'Please fill out this field.';
                isValid = false;
            }
            if (!gender) {
                document.getElementById('genderError').textContent = 'Please select your gender.';
                isValid = false;
            }
            if (!mobile) {
                document.getElementById('mobileError').textContent = 'Please fill out this field.';
                isValid = false;
            }
            if (!dob) {
                document.getElementById('dobError').textContent = 'Please fill out this field.';
                isValid = false;
            }
            if (!address) {
                document.getElementById('addressError').textContent = 'Please fill out this field.';
                isValid = false;
            }

            // If all fields are valid, proceed with signup or update
            if (isValid) {
                const users = JSON.parse(localStorage.getItem('users')) || [];

                // If we're updating an existing user, find their index
                const userId = document.getElementById('signupBtn').dataset.userId;

                if (userId) {
                    // Update existing user
                    const user = users.find(u => u.id == userId);
                    if (user) {
                        // Update user data
                        user.name = name;
                        user.fatherName = fatherName;
                        user.email = email;
                        user.age = age;
                        user.gender = gender;
                        user.mobile = mobile;
                        user.dob = dob;
                        user.address = address;

                        // Save updated user data to localStorage
                        localStorage.setItem('users', JSON.stringify(users));

                        // Show success message and reset the form
                        alert('User details updated successfully!');
                        document.getElementById('signupForm').reset();
                        document.querySelector('.signup-container').style.display = 'none';
                        document.getElementById("Datatables").style.display = 'block';

                        // Refresh the table with updated data
                        ShowDataInTable();
                    }
                } else {
                    // Add a new user
                    const newId = users.length ? users[users.length - 1].id + 1 : 1;
                    const newUser = {
                        name: name,
                        fatherName: fatherName,
                        email: email,
                        age: age,
                        gender: gender,
                        mobile: mobile,
                        dob: dob,
                        address: address,
                        id: newId,
                        password: `tempPassword_${newId}`
                    };

                    // Add the new user to the array and save to localStorage
                    users.push(newUser);
                    localStorage.setItem('users', JSON.stringify(users));

                    // Show success message and reset the form
                    alert(`Sign Up Successful!\n\n Your credentials:\nEmail: ${newUser.email}\nPassword: ${newUser.password}`);
                    document.getElementById('signupForm').reset();
                    document.querySelector('.signup-container').style.display = 'none';
                    document.querySelector('.login-container').style.display = 'block';
                }
            }
        });

        // Function to show data in the table
        function ShowDataInTable() {
            const users = JSON.parse(localStorage.getItem('users'));
            let store = document.getElementById("DataEnter");
            store.innerHTML = "";

            if (users) {
                users.forEach((element, index) => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                <td>${element.id}</td>
                <td>${element.name}</td>
                <td>${element.email}</td>
                <td>${element.gender}</td>
                <td>${element.mobile}</td>
                <td>${element.address}</td>
                <td>
                    <button class="btn-primary" onclick="EditFunction(${element.id})">Edit</button>
                    <button class="btn-danger" onclick="DeleteFunction(${index})">Delete</button>
                    <button class="btn-success" onclick="DetailFunction(${element.id})">Details</button>
                </td>
            `;
                    store.append(row);
                });
            }
        }

        // Edit function to pre-fill the form for updating user data
        function EditFunction(userId) {
            const users = JSON.parse(localStorage.getItem('users')) || [];
            const user = users.find(u => u.id == userId);

            if (user) {
                // Pre-fill the form with the user's current data
                document.getElementById('name').value = user.name;
                document.getElementById('fatherName').value = user.fatherName;
                document.getElementById('signupEmail').value = user.email;
                document.getElementById('age').value = user.age;
                document.getElementById('gender').value = user.gender;
                document.getElementById('mobileNo').value = user.mobile;
                document.getElementById('dob').value = user.dob;
                document.getElementById('address').value = user.address;

                // Change the button text to "Update" and store userId in the button's dataset
                document.querySelector('#signupForm h1').textContent = "Update Page";
                document.getElementById('signupBtn').textContent = "Update";
                document.getElementById('signupBtn').dataset.userId = user.id; // Store user ID

                // Hide the table and show the signup form
                document.getElementById("Datatables").style.display = 'none';
                document.querySelector('.signup-container').style.display = 'block';
                document.querySelector('.login-container').style.display = 'none';
            }
        }
        function DeleteFunction(index) {
            debugger;
            let ConfirmData=confirm("Do You Want to Delete Data");
            if(ConfirmData){
                const users = JSON.parse(localStorage.getItem('users'));  // Retrieve the users array from localStorage
                // const Id_User= users.find(u => u.id === userId);
                // const user_index = users.indexOf(Id_User);
                // console.log(user_index);
                const RemoveUser = users.splice(index, 1);
                localStorage.setItem('users', JSON.stringify(users))
                ShowDataInTable();
            }
            else {
                alert("Data Not Delete");
            }
        }

        function DetailFunction(userId) {
            const users = JSON.parse(localStorage.getItem('users'));  // Retrieve the users array from localStorage
            // Find the user by the provided userId
            const user = users.find(u => u.id === userId);
            if (user) {
                // If the user is found, show an alert with all user details
                alert(`User Details:\nID: ${user.id}\nName: ${user.name}\nFather's Name: ${user.fatherName}\nEmail: ${user.email}\nAge: ${user.age}\nGender: ${user.gender}\nMobile: ${user.mobile}\nDOB: ${user.dob}\nAddress: ${user.address}\nPassword: ${user.password}`);
            } else {
                // If the user is not found, alert an error message
                alert("User not found!");
            }
        }

        function forgetfunction() {
            const users = JSON.parse(localStorage.getItem('users')) || [];  // Retrieve users from localStorage or set it to an empty array if not found
            let User_Email = prompt("Please Enter Your Email");
            const user = users.find(u => u.email === User_Email);  // Find the user by email
            debugger;
            if (user) {
                let EnterPassword = prompt("Please enter Your new password");
                user.password = EnterPassword;  // Update the user's password
                // Save the updated users array back to localStorage
                localStorage.setItem('users', JSON.stringify(users));
                alert(`Your Password Change Successful!\n\n Your credentials:\nEmail: ${user.email}\nPassword: ${user.password}`);
            } else {
                alert("Your Email not Found And Can't Change Password");
            }
            document.getElementById('loginForm').reset();
        }

    </script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js"
        integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p"
        crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js"
        integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF"
        crossorigin="anonymous"></script>
</body>

</html>


<!-- <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UserManagement</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
</head>
<body>
<div class="container" style="display: flex; justify-content: center; align-items: center;">
    <div class="col">
        <form>
            <h1 class="text-center">Login Form</h1>
           <div class="form-group"> 
               <div class="mb-3">
                   <label for="Email" class="form-label">Email Or Username <span class="text-danger">*</span></label>
                   <input type="email" class="form-control" id="Email" aria-describedby="emailHelp">
                   <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
               </div>
           </div>
            <div class="mb-3">
                <label for="Password" class="form-label">Password <span class="text-danger">*</span></label>
                <input type="password" class="form-control" id="Password">
            </div>
            <div class="mb-3 form-check">
                <input type="checkbox" class="form-check-input" id="exampleCheck1">
                <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>
            <button type="button" class="btn btn-primary form-control text-center">Submit</button>
        </form>
    </div>
</div>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js"
        integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r"
        crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.min.js"
        integrity="sha384-0pUGZvbkm6XF6gxjEnlmuGrJXVbNuzT9qBBavbLwCsOGabYfZo0T0to5eqruptLy"
        crossorigin="anonymous"></script>
</body>
</html> -->
