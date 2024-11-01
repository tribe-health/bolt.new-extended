[![Bolt.new: AI-Powered Full-Stack Web Development in the Browser](./public/social_preview_index.jpg)](https://bolt.new)

# Bolt.new Fork for Extended Features

A feature-rich fork of [bolt.new](https://github.com/stackblitz/bolt.new) that extends the original project with multiple LLM integrations and enhanced development capabilities. Build, deploy, and debug full-stack web applications through an intuitive chat interface powered by various AI providers.

## Key Features

- **Multi-LLM Support**: Interact with your choice of AI providers including:
  - OpenAI
  - Google Generative AI (Gemini)
  - Mistral
  - Groq
  - OpenRouter
  - DeepSeek
  - Together AI
  - Ollama
  - LMStudio

- **Enhanced Development Experience**:
  - File/Image upload support in chat interface
  - Fixed file editor scrollbar functionality
  - Intelligent error detection with one-click fixes via toast notifications
  - Project export as ZIP
  - Direct GitHub project publishing with auto-generated README

## Feature Status

### Added Features ✅
- [x] Multi-LLM provider support
- [x] File/Image upload capability in chat
- [x] Fixed file editor scrollbar functionality
- [x] Smart error detection and fix suggestions
- [x] Project export as ZIP
- [x] GitHub project publishing
- [x] Auto-generated README for GitHub projects

### Planned Features 🚧
- [ ] Improved prompts for consistent WebContainer triggering across LLMs
- [ ] Project templates support
- [ ] Project import functionality
- [ ] Deployment integrations:
  - [ ] Vercel
  - [ ] Netlify
  - [ ] Heroku
- [ ] Additional language support (PHP, etc.)
- [ ] Per-chat deployment parameter persistence

# Bolt.new: AI-Powered Full-Stack Web Development in the Browser

Bolt.new is an AI-powered web development agent that allows you to prompt, run, edit, and deploy full-stack applications directly from your browser—no local setup required. If you're here to build your own AI-powered web dev agent using the Bolt open source codebase, [click here to get started!](./CONTRIBUTING.md)

## What Makes Bolt.new Different

Claude, v0, etc are incredible- but you can't install packages, run backends or edit code. That’s where Bolt.new stands out:

- **Full-Stack in the Browser**: Bolt.new integrates cutting-edge AI models with an in-browser development environment powered by **StackBlitz’s WebContainers**. This allows you to:
  - Install and run npm tools and libraries (like Vite, Next.js, and more)
  - Run Node.js servers
  - Interact with third-party APIs
  - Deploy to production from chat
  - Share your work via a URL

- **AI with Environment Control**: Unlike traditional dev environments where the AI can only assist in code generation, Bolt.new gives AI models **complete control** over the entire  environment including the filesystem, node server, package manager, terminal, and browser console. This empowers AI agents to handle the entire app lifecycle—from creation to deployment.

Whether you’re an experienced developer, a PM or designer, Bolt.new allows you to build production-grade full-stack applications with ease.

For developers interested in building their own AI-powered development tools with WebContainers, check out the open-source Bolt codebase in this repo!

## Tips and Tricks

Here are some tips to get the most out of Bolt.new:


- **Use the enhance prompt icon**: Before sending your prompt, try clicking the 'enhance' icon to have the AI model help you refine your prompt, then edit the results before submitting.

- **Scaffold the basics first, then add features**: Make sure the basic structure of your application is in place before diving into more advanced functionality. This helps Bolt understand the foundation of your project and ensure everything is wired up right before building out more advanced functionality.

- **Batch simple instructions**: Save time by combining simple instructions into one message. For example, you can ask Bolt to change the color scheme, add mobile responsiveness, and restart the dev server, all in one go saving you time and reducing API credit consumption significantly.

## FAQs

**Where do I sign up for a paid plan?**  
Bolt.new is free to get started. If you need more AI tokens or want private projects, you can purchase a paid subscription in your [Bolt.new](https://bolt.new) settings, in the lower-left hand corner of the application. 

**What happens if I hit the free usage limit?**  
Once your free daily token limit is reached, AI interactions are paused until the next day or until you upgrade your plan.

**Is Bolt in beta?**  
Yes, Bolt.new is in beta, and we are actively improving it based on feedback.

**How can I report Bolt.new issues?**  
Check out the [Issues section](https://github.com/stackblitz/bolt.new/issues) to report an issue or request a new feature. Please use the search feature to check if someone else has already submitted the same issue/request.

**What frameworks/libraries currently work on Bolt?**  
Bolt.new supports most popular JavaScript frameworks and libraries. If it runs on StackBlitz, it will run on Bolt.new as well.

**How can I add make sure my framework/project works well in bolt?**  
We are excited to work with the JavaScript ecosystem to improve functionality in Bolt. Reach out to us via [hello@stackblitz.com](mailto:hello@stackblitz.com) to discuss how we can partner!
