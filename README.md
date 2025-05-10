# khqr-php-composer-setup

> 💡
> Only Silver Membership can access this private repo - let's our join <a href="https://discord.com/invite/ySCGdyArHb" >discord server</a>

![image](https://github.com/user-attachments/assets/5470ded5-b424-4c79-8125-03b658a4291f)
<table>
  <tr>
    <td>
      <a href="https://www.ikhode.site/">
        <img width="550" src="https://github.com/user-attachments/assets/8aead125-14da-4205-a01f-eb5eb9b8da5b" alt="Profile Image">
      </a>
    </td>
    <td>
      I'm a <strong>Software Developer</strong> who passionate about <strong>coding</strong> and building tools that help people with their daily tasks.
      I'm currently exploring <strong>AI solutions</strong> and working with <strong>modern tech stacks</strong>. I'm also on a journey to level up my 
      <strong>Spaghetti Code</strong> skills. Support us by make some donate and I really appricate that.
      <br><br>
      Got a question? Feel free to <a href="https://bio.ikhode.site/">contact me anytime</a>.
    </td>
  </tr>
</table>


# Bakong KHQR Payment Integration

This project implements a payment gateway for the Bakong KHQR system (Cambodia's QR code-based payment system). It allows merchants to generate KHQR codes and verify payment status through the Bakong API.

## Features

- Generate KHQR codes for payments
- Display QR codes for customer scanning
- Poll payment status in real-time
- Simple user interface for payment processing

## Prerequisites

- PHP 8.0 or higher
- Composer for PHP dependency management
- A Bakong merchant account with API access
- Web server (Apache, Nginx, etc.)


<p>
     <img width="400" src="https://github.com/user-attachments/assets/6fa05e7f-251d-491c-ab64-8fe230d40641" alt="Profile Image" title="screenshot image of khqr php composer setup with simple ui">
</p>
<p><em>screenshot image of khqr php composer setup with simple ui</em></p>
 
## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ikhode-technologies/private-repo.git
   cd private-repo
   ```

2. Install PHP dependencies using Composer:
   ```bash
   composer require khqr-gateway/bakong-khqr-php endroid/qr-code guzzlehttp/guzzle
   ```

3. Configure your Bakong API credentials:
   - Open `khqr_api.php` and replace `'bakong api key'` with your actual Bakong API key
   - Update the Bakong account ID in the `$individualInfo` object:
     ```php
     $individualInfo = new IndividualInfo(
         bakongAccountID: 'your_bakong_account@domain',
         // ... other settings
     );
     ```

## Configuration

### Merchant Information

Modify the merchant details in the `khqr_api.php` file:

```php
$individualInfo = new IndividualInfo(
    bakongAccountID: 'your_bakong_account@domain',  // Your Bakong ID
    merchantName: 'Your Business Name',            // Your business name
    merchantCity: 'Your City',                     // Your business city
    currency: KHQRData::CURRENCY_USD,              // Currency (USD or KHR)
    amount: floatval($amount),                     // Amount from request
    billNumber: $transactionId,                    // Transaction ID
    purposeOfTransaction: 'Payment'                // Purpose description
);
```

### Payment Settings

You can modify the payment amount in `index.html`:

```javascript
body: JSON.stringify({
    amount: 0.1,  // Change to your desired default amount
    transactionId: 'TEST' + Date.now()
})
```

## Usage

1. Start your web server pointing to the project directory
2. Access the application through your browser (e.g., http://localhost/index.html)
3. Click "Generate QR Code" to create a new payment request
4. The customer scans the QR code using their Bakong app
5. The system automatically checks for payment confirmation
6. Once payment is confirmed, the status will update to "Successfully Paid!"

## File Structure

- `khqr_api.php` - Main PHP backend for KHQR generation and payment verification
- `index.html` - Frontend interface for payment processing
- `payment.log` - Log file for transaction records
- `vendor/` - Composer dependencies

## Troubleshooting

### Common Issues

1. **QR Code Not Generating**
   - Check if all required PHP extensions are installed
   - Verify your Bakong API key is correct
   - Check the PHP error logs

2. **Payment Status Not Updating**
   - Ensure the Bakong API is accessible from your server
   - Check if the polling interval is working correctly
   - Verify your Bakong account has the correct permissions

3. **CORS Issues**
   - The application includes CORS headers, but if you're running on a different domain, you may need to adjust the `Access-Control-Allow-Origin` header

### Logging

The application logs important events to `payment.log`. Check this file for debugging information:

```bash
tail -f payment.log
```


## License

MIT - See the LICENSE file for details

## Support

For support, please contact with this <a href="https://bio.ikhode.site/" >contact list</a> or create an issue in the repository.
