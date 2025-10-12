#2FA

*User Requests OTP
React frontend sends a request to /api/send-otp with the user's identifier (email or phone).
Backend generates a random OTP and stores it in H2 with:
User ID
OTP code
Expiry timestamp
Status (e.g., unused)

*Send OTP
Backend sends the OTP:

Email: Use JavaMailSender or an external service like SendGrid.
SMS: Use Twilio or any SMS gateway API.
Respond to frontend with success/failure.

*User Enters OTP
React frontend shows an input field for OTP.
On submit, it sends the OTP to /api/verify-otp.

*Verify OTP
Backend checks:
Is the OTP correct?
Is it within expiry?
Has it already been used?
If valid, mark it as used and proceed with login or action.

*Security & UX Enhancements
Limit OTP requests per user (rate limiting).
Add resend OTP with cooldown.
Show countdown timer on frontend.
Encrypt OTP in DB if needed.
