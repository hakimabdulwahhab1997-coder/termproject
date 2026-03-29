document.addEventListener('DOMContentLoaded', () => {
    const orderForm = document.getElementById('orderForm');
    
    if (orderForm) {
        orderForm.addEventListener('submit', function(e) {
            e.preventDefault();
            let isValid = true;
            
            // Clear previous errors
            document.querySelectorAll('.error-msg').forEach(el => el.textContent = '');

            // Name Validation
            const name = document.getElementById('name');
            if (name.value.trim() === '') {
                showError('name', 'Name is required.'); /* cite: 294, 296 */
                isValid = false;
            }

            // Email Pattern Validation [cite: 295]
            const email = document.getElementById('email');
            const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
            if (!email.value.match(emailPattern)) {
                showError('email', 'Please enter a valid email address.');
                isValid = false;
            }

            if (isValid) {
                alert('Success! Your request has been sent.'); /* cite: 347 */
                orderForm.reset();
            }
        });
    }
});

function showError(id, message) {
    const errorDisplay = document.getElementById(id + '-error');
    if (errorDisplay) errorDisplay.textContent = message;
}