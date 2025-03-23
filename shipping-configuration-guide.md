# CarryYourShit Shipping Configuration Guide

This guide provides step-by-step instructions for configuring shipping methods in the CarryYourShit e-commerce platform.

## Setting Shipping Origin

First, set up your shipping origin to ensure accurate shipping calculations:

1. Log in to the admin panel (http://localhost:8001/admin)
2. Navigate to **Configuration → Sales → Shipping Settings → Origin**
3. Fill in the following details:
   - **Country**: India
   - **State**: [Your warehouse state]
   - **City**: [Your warehouse city]
   - **Street Address**: [Your warehouse address]
   - **Zipcode**: [Your warehouse PIN code]
   - **Store Contact Number**: [Your business phone]
4. Click **Save Config**

## Configuring Shiprocket Shipping

Set up Shiprocket as your primary shipping method:

1. Navigate to **Configuration → Sales → Shipping Methods → Shiprocket**
2. Configure the following:
   - **Title**: "Shiprocket"
   - **Description**: "Fast shipping across India with Shiprocket"
   - **Status**: Enabled
   - **Rate Type**: Fixed
   - **Shiprocket Email**: Your Shiprocket account email
   - **Shiprocket Password**: Your Shiprocket account password
   - **Pickup Location**: Primary (or your custom pickup location name)
   - **Shiprocket Channel ID**: Your Shiprocket channel ID (optional)
   - **Free Shipping Threshold**: 5000 (for orders above ₹5000)
   - **Metro Cities Rate (₹)**: 150
   - **Tier 2 Cities Rate (₹)**: 200
   - **Other Regions Rate (₹)**: 250
   - **Heavy Weight Threshold (kg)**: 5
   - **Heavy Weight Rate Multiplier**: 2
3. Click **Save Config**

## Configuring Alternative Shipping Methods

You can also set up the built-in shipping methods as alternatives:

### Free Shipping

Set up free shipping for orders above ₹5000:

1. Navigate to **Configuration → Sales → Shipping Methods → Free Shipping**
2. Configure the following:
   - **Title**: "Free Shipping"
   - **Description**: "Free shipping on orders above ₹5000"
   - **Status**: Enabled
3. Click **Save Config**

### Flat Rate Shipping

Configure flat rate shipping as a backup:

1. Navigate to **Configuration → Sales → Shipping Methods → Flat Rate Shipping**
2. Configure the following:
   - **Title**: "Standard Shipping"
   - **Description**: "Delivery within 3-7 business days"
   - **Rate**: ₹150 (base rate)
   - **Type**: Per Order (or Per Unit for larger items)
   - **Status**: Enabled
3. Click **Save Config**

## Region-Specific Shipping Rates

Shiprocket shipping is configured with region-specific rates:

### Metro Cities (1-3 days delivery)
- Delhi, Mumbai, Bangalore, Chennai, Kolkata, Hyderabad
- Rate: ₹150 for orders under 5kg
- Rate: ₹300 for orders above 5kg

### Tier 2 Cities (2-5 days delivery)
- Pune, Ahmedabad, Jaipur, Lucknow, etc.
- Rate: ₹200 for orders under 5kg
- Rate: ₹400 for orders above 5kg

### Other Regions (4-7 days delivery)
- All other areas
- Rate: ₹250 for orders under 5kg
- Rate: ₹500 for orders above 5kg

## Testing Shipping Configuration

After setting up shipping methods, test them thoroughly:

1. Add products to cart from the frontend
2. Proceed to checkout
3. Enter different shipping addresses to test region-specific rates
4. Verify that free shipping appears for orders above ₹5000
5. Test with different product weights to ensure weight-based pricing works correctly

## Managing Shiprocket Shipments in Admin Panel

Once an order is placed with Shiprocket shipping:

1. Go to **Sales → Orders** in the admin panel
2. Create a shipment for the order
3. The shipment will be automatically registered with Shiprocket
4. You can track, cancel, or generate labels for the shipment using the Shiprocket options in the shipment view

## Shiprocket Integration Features

Our Shiprocket integration provides the following features:

1. **Automated Order Creation**: When you create a shipment, the order is automatically created in Shiprocket
2. **Shipment Tracking**: Track shipments directly from the admin panel
3. **Label Generation**: Generate shipping labels with one click
4. **Shipment Cancellation**: Cancel shipments if needed
5. **Region-Based Pricing**: Different rates for metro, tier 2, and other regions
6. **Weight-Based Pricing**: Higher rates for heavier items
7. **Free Shipping Threshold**: Automatic free shipping for orders above the threshold

## Setting Up a Shiprocket Account

To use the Shiprocket integration, you need to:

1. Register for a Shiprocket account at [shiprocket.in](https://www.shiprocket.in/)
2. Verify your business details
3. Add pickup addresses
4. Create a channel for your store
5. Get your channel ID (optional)
6. Use your Shiprocket email and password in the Bagisto configuration 