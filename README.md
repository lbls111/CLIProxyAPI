# WebSocket Proxy Logger

A minimal web application to connect to a WebSocket proxy service and view real-time logs of its activity.

## Configuration

Before running the application locally or deploying, you must configure the connection settings in `config.ts`.

1.  **Open `config.ts`:**
    ```ts
    // config.ts

    /**
     * The JWT token required for authenticating with the WebSocket Proxy service.
     * Set to `null` if your WebSocket proxy does not require JWT authentication.
     */
    export const JWT_TOKEN: string | null = "your-jwt-token-here"; // <--- UPDATE THIS

    /**
     * The full URL of your WebSocket Proxy service.
     */
    export const WEBSOCKET_PROXY_URL: string = "wss://your-proxy-url/v1/ws"; // <--- UPDATE THIS
    ```

2.  **Update `JWT_TOKEN`**: Replace `"your-jwt-token-here"` with your actual JWT, or set it to `null` if no authentication is needed.
3.  **Update `WEBSOCKET_PROXY_URL`**: Replace the example URL with the correct WebSocket URL for your proxy service.

## Local Development

To run the application on your local machine:

1.  **Install dependencies:**
    ```bash
    npm install
    ```

2.  **Start the development server:**
    ```bash
    npm run dev
    ```

    The application will be available at `http://localhost:3000`.

## Deployment to Cloudflare Pages

This project is configured to be deployed as a static site on Cloudflare Pages.

### Build Settings

When setting up your project on Cloudflare Pages, use the following build configuration:

*   **Framework preset**: `Vite`
*   **Build command**: `npm run build`
*   **Build output directory**: `/dist`

### **IMPORTANT: Root Directory Configuration**

The deployment error you are seeing (`Could not read package.json`) is almost always caused by an incorrect **Root directory** setting in Cloudflare Pages.

*   **If your `package.json` file is at the very top level of your Git repository:**
    *   Leave the **Root directory** field **blank**.

*   **If your project is inside a subfolder in your Git repository (e.g., `my-repo/frontend/package.json`):**
    *   You **must** set the **Root directory** to match that subfolder path. For the example above, you would set it to `frontend`.

Please check this setting in your Cloudflare Pages dashboard under **Settings > Builds & deployments**. This is the most likely cause of the issue.
