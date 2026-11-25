# Privacy Policy

This plugin does not collect, store, or log any user data itself.

When you use an onomeo model in Dify, the plugin sends your prompt messages, model parameters, any images in the conversation, tool definitions, and the API key you configured to the onomeo API at `https://onomeo.com/v1` to generate a response. It does not contact any other endpoint. Your API key is stored by your Dify instance as an encrypted credential, not by this plugin.

On the onomeo side, each request is forwarded to the third-party provider that serves the chosen model, whose processing location and retention can differ per model. For each call made with an API key, onomeo keeps an excerpt under your account (the first 1,000 characters of the system prompt, the first 4,000 characters of the last user message and the first 4,000 characters of the reply) with the time, model, calling tool name, result and amount used. At most the latest 100 calls are kept, nothing older than 30 days, and the record is erased when the account is deleted. onomeo does not use them to train models. See the onomeo privacy policy at https://onomeo.com/privacy.
