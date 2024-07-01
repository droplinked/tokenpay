##Getting Started with Tokenpay on droplinked##

Tokenpay by droplinked empowers token issuers and holders to use minted digital assets as a seamless token payment gateway. The functionality enables buyers to use these tokens to purchase both physical and digital goods. This helps to foster community support with a reward system while boosting token adoption and engagement.


Demo Usecase:

To showcase how Tokenpay works, droplinked has launched BediCoin ($BDC) on Base. Visit the default shop at droplinked.io/Cipher to see how $BDC token can be used to purchase goods on droplinked.
For a detailed demonstration, you can check out the video here: https://drive.google.com/file/d/1HnoeEBMFxYu7lGUUIUO_L5Tnyfl-nH5i/view?usp=sharing


Here's a quick guide on how to get started with Tokenpay yourself:

1. Setting up a new custom store with droplinked

Head over to droplinked.com and click on Start Selling.
Create an account with an email and password, then click 'Sign Up' or continue with your Google account.

<img width="458" alt="Screenshot 2024-06-30 at 4 26 27 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/7a394edc-27c6-4eea-9cdc-0c9e1be84924">

Verify your email and log in.

<img width="368" alt="Screenshot 2024-06-30 at 4 27 09 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/9f1175a6-76e8-4ab9-a6d4-fdbda29d67f2">


Enter an username to generate the store link and click Continue. A default store will quickly be created for you to customize.

<img width="495" alt="Screenshot 2024-06-30 at 4 27 53 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/2b6b92f3-e68c-420f-b567-eafcee35113d">

From the dashboard, you can navigate to Settings to update the Store Info, Store Design, and Login and Payment Options.

<img width="630" alt="Screenshot 2024-06-30 at 4 28 31 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/9ff2f84c-d521-4bb7-8351-a309317015d5">

2. Activating Tokenpay

To initiate Tokenpay you will need to provide details about the tokens identifier and a pegged value or DEX that determines the real-time value.

Activation Steps:

Once the token is integrated, follow these steps to activate Tokenpay:
Navigate to your Droplinked dashboard.
Go to Settings > Payment Options section.
Under Payment Method, toggle on the token named button.
Enter your wallet address and Save it.

<img width="409" alt="Screenshot 2024-06-30 at 4 30 10 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/ab2e08f7-8587-44d8-84fe-4c445cb9b066">
<img width="384" alt="Screenshot 2024-06-30 at 4 30 18 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/8c2feed7-4643-4014-b624-5d619ecbd4c1">


3. Customizing storefronts

Droplinked offers two main ways to customize your storefront:

No-code tools: In the droplinked dashboard, navigate to the Settings > Store Design section. On the right side you can expand each dropdown to customize the store template, color schemes, upload site logo, hero banner, profile logo, add social media and footer links.


<img width="765" alt="Screenshot 2024-06-30 at 4 32 21 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/39558ba9-307e-48e8-a8a7-66959f1222d3">


Technical libraries: For more intricate experiences, you can use the droplinked APIs to create custom storefronts with the technology of your choice. A NextJS boiler-template project is also available for use. The open source repo and library can be found here: https://github.com/droplinked/Next-ShopFront

<img width="757" alt="Screenshot 2024-06-30 at 4 32 33 PM" src="https://github.com/droplinked/tokenpay/assets/8434893/bbce9eb1-0573-47b1-b941-03d6cb9d2260">


4. Inquiry form for Tokenpay

Are you interested in launching or expanding with tokenpay? 
Fill out the inquiry form here to get started: https://docs.google.com/forms/d/e/1FAIpQLSccVUM0VFImXsmJeY_xP1evmR2JuWuYL0tsDMrtWzB9487hwA/viewform?usp=sharing


5. Getting started with your own NextJS instance of a customizable shop or marketplace:


# Next.js Front-End Project

## Technologies Used

- NextJs
- ReactJs
- Typescript
- Tailwindcss

## Installation

To install and run the project locally, follow these steps:

1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Run `npm install` to install dependencies.
4. Run `npm run dev` to start the development server.

```bash
git clone https://github.com/droplinked/Next-ShopFront.git
cd Next-ShopFront
npm install
npm run dev
```

# Environment Variables

1. Create a `.env` file in the root directory of your project.
2. Add the required environment variables along with their values to this file.
3. Ensure that the `.env` file is included in your `.gitignore` to prevent sensitive information from being committed to version control.
#

- `NEXT_PUBLIC_BASE_API_URL`: This variable specifies the base URL for the API endpoints. It should be set to `https://apiv3.droplinked.com/v1/`

- `NEXT_PUBLIC_API_KEY`: This variable should be obtained from the dashboard. It represents the API key required to authenticate requests to the backend API.

- `NEXT_PUBLIC_APP_DEVELOPMENT`: This variable should be set to either `"true"` or `"false"`. It determines whether the application is running in development mode or not. Setting it to `"true"` indicates a development environment, while setting it to `"false"` indicates a production environment.
#
Here's an example of how the `.env` file should look:
```plaintext
NEXT_PUBLIC_BASE_API_URL=https://apiv3.droplinked.com/v1/
NEXT_PUBLIC_API_KEY="your_api_key_goes_here"
NEXT_PUBLIC_APP_DEVELOPMENT="true"
```


## Landing Page Documentation

The landing page is designed to display shop data followed by a list of products, dynamically fetched from separate APIs.

### Fetching Data

#### Shop Data
- **API Call**: Data about the shop is fetched from the `get_shop_service` API.

```typescript
export const get_shop_service = () ⇒ fetchInstance(`shop`, { cache: "force-cache" })
```

#### Product Data

- **API Call**: Product data is fetched from the **`get_products_service`** API, which supports pagination, filtering, and a limit on the number of items per fetch.

```typescript
export const get_products_service = ({ page, limit, filter }: IGetProductsService) =>
	fetchInstance(`products?page=${page}${limit && `&limit=${limit}`}${filter && `&filter=title:${filter}`}`, { next: { revalidate: 3600 } });
	
export interface IGetProductsService{
    page: number;
    limit?: number;
    filter?: string
}
```

## Managing shopping cart operations:

### **2. Services**

These functions interact with a backend API to perform CRUD operations on a shopping cart.

- **`create_cart_service()`**: Initializes a new cart session by making a POST request to the /cart endpoint.
```typescript
export const create_cart_service = () => fetchInstance(`cart`, { method: "POST" });
```


- **`add_to_cart_service`**: Adds an item to a specified cart by sending a POST request to cart/${cartId} with the item details.
```typescript
export const add_to_cart_service = ({ cartId, ...body }: IAddToCartService) => fetchInstance(`cart/${cartId}`, { method: "POST", body: JSON.stringify(body) });
export interface IAddToCartService {
    cartId: string;
    shopID: string;
    skuID: string;
    quantity: number;
    m2m_data?: IM2MProps;
}

export interface IM2MProps {
    m2m_position: string;
    print_url: string;
}
```

- **`change_quantity_service`**: Updates the quantity of an item in the cart by sending a PATCH request to /cart/${cartId}.

```typescript
export const change_quantity_service = ({ cartId, ...body }: ICahngeQuantityService) => fetchInstance(`cart/${cartId}`, { method: "PATCH", body: JSON.stringify(body) });

export interface ICahngeQuantityService extends Omit<IAddToCartService, "m2m_data"> {
    itemId: string;
}
```


- **`get_cart_service`**: Retrieves the cart's current state by making a GET request to /cart/${cartId}.
```typescript
export const get_cart_service = ({ cartId }: IGetCartService) => fetchInstance(`cart/${cartId}`);

export interface IGetCartService {
    cartId: string;
}
```

### **2. Hook (`useAppCart`)**

This custom hook integrates the services, managing the state of the shopping cart using a store.

### **Functions:**

- **`_update()`**: A helper function that updates the cart state and returns the updated data.
- **`_create()`**: Creates a new cart by calling an asynchronous service and updates the global cart state upon successful creation.
- **`_add_params({ skuID, quantity, m2m_data })`**: Prepares and returns the parameters needed for the **`add_to_cart_service`** function by ensuring a cart ID is available, either from the existing state or by creating a new cart.
- **`add()`**: Adds an item to the cart using the **`add_to_cart_service`**. It handles both the addition of the item and updating the global cart state.
- **`change({ cartId, skuID, quantity, itemId })`**: Changes the quantity of an existing item in the cart and updates the state.
- **`get(_id)`**: Retrieves a cart's details based on cart ID and updates the app state.
- **`_add_email(params)`**: Adds an email to the cart as part of the checkout process and updates the state.
- **`add_address(params, email)`**: First adds an email to the cart and then an address, updating the state after each operation.
- **`add_shipping({ cartId, rates })`**: Adds shipping information to the cart and updates the state.
- **`add_gift(params)`**: Applies a gift card to the cart and updates the state.


# Managing Crypto Payment

## useWeb3 Hook

- **`payment`**: An array of type **`IPaymentDroplinked[]`** which lists all available payment options along with details like labels, descriptions, and icons for both light and dark themes. Each option include a token type and an enum number.

```typescript
export type IPaymentDroplinked = {
    type: string;
    options: { [propname in keyof Partialize<PaymentTypes>]: PaymentDroplinkedOptions }[];
};
```

## usePayment Hook

- **`crypto_payment`**: A function intended to handle cryptocurrency payments. It uses the **`selected_method`** from the checkout state to determine the payment method and processes the payment accordingly. It includes obtaining wallet addresses, initiating transactions, and managing the checkout and submission of orders.

- install the @droplinked/wallet-connection package in your project.
  ```bash
  npm install @droplinked/wallet-connection
  ```
  After installing the package, import the necessary utilities into your file where you're defining the crypto_payment function. Import getNetworkProvider and Network from @droplinked/wallet-connection. You can do this as follows:
  ```typescript
  import { getNetworkProvider, Network } from "@droplinked/wallet-connection";
  ```
    ```typescript
    const crypto_payment = async ({selected_method: {name: paymentType, enum_number, token}}: Pick<ICheckoutState, "selected_method">) => {
        if(paymentType === "" || paymentType === "STRIPE") return
        const sender: string = await (await getNetworkProvider(enum_number, APP_DEVELOPMENT ? Network.TESTNET : Network.MAINNET, "").walletLogin())?.address;
        let checkout = await (await checkout_crypto_payment_service({ cartId: _id, paymentType, token, email, walletAddress: sender }));
        if (checkout) {
            const paymentResult = getNetworkProvider(enum_number, APP_DEVELOPMENT ? Network.TESTNET : Network.MAINNET, sender);
            const payment = await paymentResult?.payment(checkout?.paymentData);
            await submit_order_service({
                chain: paymentType?.toLowerCase(),
                deploy_hash: payment?.deploy_hash,
                orderID: checkout?.orderID,
                cryptoAmount: parseInt(payment?.cryptoAmount),
            }).finally(() => {
                transition("submitting", false);
                router.push(`/checkout/${checkout?.orderID}`);
            });
        }
       
    };
    ```


### **Detailed Function Description**

**`crypto_payment`:** This asynchronous function handles the payment process when cryptocurrency is chosen as the payment method.

### Parameters:

- **`selected_method`**: An object from **`ICheckoutState`** containing:
    - **`name`**: The name of the payment method.
    - **`enum_number`**: An integer representing an identifier for the payment method.
    - **`token`**: A token type associated with the payment.
        
        ```typescript
        selected_method: {
        	name: keyof Partialize<PaymentTypes> | "",
        	token: keyof Partialize<TokenTypes> | "",
        	enum_number: number
        }
        ```
        

### Process:

1. Retrieves the wallet address or public key from a blockchain network provider based on the **`enum_number`** and whether the app is in development mode (determines if it connects to a testnet or mainnet).
    
    ```typescript
    const sender: string = await (await getNetworkProvider(enum_number, APP_DEVELOPMENT ? Network.TESTNET : Network.MAINNET, "").walletLogin())[paymentType === "CASPER" ? "publicKey" : "address"];
    ```
    
2. Initiates a payment through a checkout service and then proceeds with blockchain-specific payment processing.
    
    ```typescript
    export const checkout_crypto_payment_service = ({ cartId, paymentType, token, ...body }: ICheckoutCryptoPaymentService) =>
        fetchInstance(`checkout/${cartId}/payment/${paymentType}/${token}`, { method: "POST", body: JSON.stringify(body) });
    
    let checkout = await (await checkout_crypto_payment_service({ cartId: _id, paymentType, token, email, walletAddress: sender }));
    ```
    
3. Submits the completed order to the order service, capturing essential transaction details like the deploy hash and order ID.
    
    ```typescript
    const paymentResult = getNetworkProvider(enum_number, APP_DEVELOPMENT ? Network.TESTNET : Network.MAINNET, sender);
    const payment = await paymentResult?.payment(checkout?.paymentData);
    await submit_order_service({ chain: paymentType?.toLowerCase(), deploy_hash: payment?.deploy_hash, orderID: checkout?.orderID, cryptoAmount: parseInt(payment?.cryptoAmount)}
    ```
    
4. Handles the transaction completion or failure, updating the application state and routing the user accordingly.
    
    ```typescript
    transition("submitting", false);
    router.push(`/checkout/${checkout?.orderID}`);
    ```
