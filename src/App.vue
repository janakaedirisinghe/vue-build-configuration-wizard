<template>
  <div class="min-h-screen bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="text-center mb-12">
        <h1 class="text-4xl font-extrabold text-indigo-600 tracking-tight sm:text-5xl">Vue Build Configuration Wizard</h1>
        <p class="mt-3 max-w-3xl mx-auto text-xl text-gray-500 sm:mt-4">Generate optimal Webpack/Vite configurations for your Vue 3 projects</p>
      </div>

      <div class="bg-white shadow overflow-hidden rounded-lg">
        <div class="px-4 py-5 sm:px-6 bg-indigo-700">
          <h2 class="text-lg font-medium text-white">Project Configuration</h2>
          <p class="mt-1 max-w-2xl text-sm text-indigo-100">Select your project preferences below.</p>
        </div>

        <div class="border-t border-gray-200 px-4 py-5 sm:p-6">
          <div class="grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6">
            <!-- Project Name -->
            <div class="sm:col-span-3">
              <label for="project-name" class="block text-sm font-medium text-gray-700">Project Name</label>
              <div class="mt-1">
                <input type="text" v-model="config.projectName" id="project-name" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border" placeholder="my-vue-app">
              </div>
            </div>

            <!-- Framework -->
            <div class="sm:col-span-3">
              <label for="framework" class="block text-sm font-medium text-gray-700">Framework</label>
              <div class="mt-1">
                <select v-model="config.framework" id="framework" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="vite">Vite</option>
                  <option value="webpack">Webpack</option>
                </select>
              </div>
            </div>

            <!-- Vue Version -->
            <div class="sm:col-span-3">
              <label for="vue-version" class="block text-sm font-medium text-gray-700">Vue Version</label>
              <div class="mt-1">
                <select v-model="config.vueVersion" id="vue-version" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="3">Vue 3</option>
                  <option value="2">Vue 2</option>
                </select>
              </div>
            </div>

            <!-- TypeScript -->
            <div class="sm:col-span-3">
              <label for="typescript" class="block text-sm font-medium text-gray-700">TypeScript</label>
              <div class="mt-1">
                <select v-model="config.typescript" id="typescript" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="yes">Yes</option>
                  <option value="no">No</option>
                </select>
              </div>
            </div>

            <!-- CSS Framework -->
            <div class="sm:col-span-3">
              <label for="css-framework" class="block text-sm font-medium text-gray-700">CSS Framework</label>
              <div class="mt-1">
                <select v-model="config.cssFramework" id="css-framework" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="tailwind">Tailwind CSS</option>
                  <option value="none">None</option>
                  <option value="bootstrap">Bootstrap</option>
                  <option value="vuetify">Vuetify</option>
                </select>
              </div>
            </div>

            <!-- Linting -->
            <div class="sm:col-span-3">
              <label for="linting" class="block text-sm font-medium text-gray-700">Linting</label>
              <div class="mt-1">
                <select v-model="config.linting" id="linting" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="eslint">ESLint</option>
                  <option value="none">None</option>
                </select>
              </div>
            </div>

            <!-- Features -->
            <div class="sm:col-span-6">
              <label class="block text-sm font-medium text-gray-700 mb-2">Features</label>
              <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                <div class="flex items-center">
                  <input id="router" v-model="config.features.router" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
                  <label for="router" class="ml-2 block text-sm text-gray-700">Vue Router</label>
                </div>
                <div class="flex items-center">
                  <input id="pinia" v-model="config.features.pinia" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
                  <label for="pinia" class="ml-2 block text-sm text-gray-700">Pinia (State Management)</label>
                </div>
                <div class="flex items-center">
                  <input id="testing" v-model="config.features.testing" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
                  <label for="testing" class="ml-2 block text-sm text-gray-700">Testing (Vitest/Jest)</label>
                </div>
                <div class="flex items-center">
                  <input id="pwa" v-model="config.features.pwa" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
                  <label for="pwa" class="ml-2 block text-sm text-gray-700">PWA Support</label>
                </div>
                <div class="flex items-center">
                  <input id="i18n" v-model="config.features.i18n" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
                  <label for="i18n" class="ml-2 block text-sm text-gray-700">I18n</label>
                </div>
                <div class="flex items-center">
                  <input id="axios" v-model="config.features.axios" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
                  <label for="axios" class="ml-2 block text-sm text-gray-700">Axios</label>
                </div>
              </div>
            </div>

            <!-- Deployment -->
            <div class="sm:col-span-3">
              <label for="deployment" class="block text-sm font-medium text-gray-700">Deployment Target</label>
              <div class="mt-1">
                <select v-model="config.deployment" id="deployment" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="static">Static (Netlify, Vercel)</option>
                  <option value="ssr">SSR (Server-Side Rendering)</option>
                  <option value="docker">Docker Container</option>
                </select>
              </div>
            </div>

            <!-- Environment -->
            <div class="sm:col-span-3">
              <label for="environment" class="block text-sm font-medium text-gray-700">Development Environment</label>
              <div class="mt-1">
                <select v-model="config.environment" id="environment" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md p-2 border">
                  <option value="node">Node.js</option>
                  <option value="docker">Docker Dev Container</option>
                </select>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Generate button -->
      <div class="flex justify-center mt-8">
        <button @click="generateConfig" class="inline-flex items-center px-6 py-3 border border-transparent text-base font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          Generate Configuration
        </button>
      </div>

      <!-- Config Output -->
      <div v-if="showOutput" class="mt-10">
        <div class="bg-white shadow overflow-hidden rounded-lg">
          <div class="px-4 py-5 sm:px-6 bg-indigo-700">
            <div class="flex justify-between">
              <h2 class="text-lg font-medium text-white">Configuration Output</h2>
              <button @click="copyToClipboard" class="px-3 py-1 bg-indigo-500 text-white text-sm rounded-md hover:bg-indigo-400 focus:outline-none focus:ring-2 focus:ring-indigo-300">
                Copy to Clipboard
              </button>
            </div>
          </div>
          <div class="border-t border-gray-200">
            <div class="px-4 py-5 sm:p-6 bg-gray-800 rounded-b-lg">
              <!-- Fixed: Added text-left class for left alignment -->
              <pre class="text-left text-green-400 overflow-x-auto text-sm p-4 max-h-96"><code>{{ configOutput }}</code></pre>
            </div>
          </div>
        </div>

        <!-- CLI Command -->
        <div class="mt-6 bg-white shadow overflow-hidden rounded-lg">
          <div class="px-4 py-5 sm:px-6 bg-indigo-700">
            <h2 class="text-lg font-medium text-white">Installation Commands</h2>
          </div>
          <div class="border-t border-gray-200">
            <div class="px-4 py-5 sm:p-6">
              <!-- Fixed: Changed bg-gray-100 to bg-gray-100 and added text-gray-800 for contrast -->
              <div class="bg-gray-100 p-4 rounded-md">
                <!-- Fixed: Added text-left class for left alignment and text-gray-800 for visibility -->
                <pre class="text-left whitespace-pre-wrap text-sm text-gray-800"><code>{{ installCommands }}</code></pre>
              </div>
              <button @click="copyCommands" class="mt-3 px-3 py-1 bg-indigo-600 text-white text-sm rounded-md hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-indigo-300">
                Copy Commands
              </button>
            </div>
          </div>
        </div>

        <!-- Next Steps -->
        <div class="mt-6 bg-white shadow overflow-hidden rounded-lg">
          <div class="px-4 py-5 sm:px-6 bg-indigo-700">
            <h2 class="text-lg font-medium text-white">Next Steps</h2>
          </div>
          <div class="border-t border-gray-200 text-gray-800">
            <div class="px-4 py-5 sm:p-6">
              <ol class="list-decimal pl-5 space-y-2 text-left">
                <li>Create a new directory for your project: <code class="bg-gray-100 px-2 py-1 rounded">mkdir {{ config.projectName }}</code></li>
                <li>Navigate to the project directory: <code class="bg-gray-100 px-2 py-1 rounded">cd {{ config.projectName }}</code></li>
                <li>Create the configuration files shown above</li>
                <li>Run the installation commands</li>
                <li>Start your development server with: <code class="bg-gray-100 px-2 py-1 rounded">{{ config.framework === 'vite' ? 'npm run dev' : 'npm run serve' }}</code></li>
              </ol>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      config: {
        projectName: 'my-vue-app',
        framework: 'vite',
        vueVersion: '3',
        typescript: 'yes',
        cssFramework: 'tailwind',
        linting: 'eslint',
        features: {
          router: true,
          pinia: true,
          testing: false,
          pwa: false,
          i18n: false,
          axios: true
        },
        deployment: 'static',
        environment: 'node'
      },
      showOutput: false
    }
  },
  computed: {
    configOutput() {
      if (this.config.framework === 'vite') {
        return this.generateViteConfig(this.config);
      } else {
        return this.generateWebpackConfig(this.config);
      }
    },
    installCommands() {
      let commands = `# Create project directory\nmkdir ${this.config.projectName} && cd ${this.config.projectName}\n\n`;
      
      // Base installation
      if (this.config.framework === 'vite') {
        commands += `# Initialize project with Vite\nnpm create vite@latest . -- --template ${this.config.typescript === 'yes' ? 'vue-ts' : 'vue'}\n\n`;
      } else {
        commands += `# Initialize project with Vue CLI\nnpm install -g @vue/cli\nvue create . --preset ${this.config.typescript === 'yes' ? 'ts' : 'default'}\n\n`;
      }
      
      commands += "# Install dependencies\nnpm install";
      
      // Add feature-specific packages
      const packages = [];
      
      if (this.config.features.router) {
        packages.push("vue-router@4");
      }
      
      if (this.config.features.pinia) {
        packages.push("pinia");
      }
      
      if (this.config.features.axios) {
        packages.push("axios");
      }
      
      if (this.config.features.i18n) {
        packages.push("vue-i18n@9");
      }
      
      if (this.config.cssFramework === 'tailwind') {
        commands += "\n\n# Install Tailwind CSS\nnpm install -D tailwindcss postcss autoprefixer\nnpx tailwindcss init -p";
      } else if (this.config.cssFramework === 'bootstrap') {
        packages.push("bootstrap @popperjs/core");
      } else if (this.config.cssFramework === 'vuetify') {
        packages.push("vuetify@next");
      }
      
      if (this.config.features.testing) {
        if (this.config.framework === 'vite') {
          commands += "\n\n# Install testing libraries\nnpm install -D vitest jsdom @vue/test-utils";
        } else {
          commands += "\n\n# Install testing libraries\nvue add unit-jest";
        }
      }
      
      if (this.config.features.pwa) {
        if (this.config.framework === 'vite') {
          commands += "\n\n# Install PWA plugin\nnpm install -D vite-plugin-pwa";
        } else {
          commands += "\n\n# Add PWA support\nvue add pwa";
        }
      }
      
      if (packages.length > 0) {
        commands += " " + packages.join(" ");
      }
      
      commands += "\n\n# Start development server\nnpm run dev";
      
      return commands;
    }
  },
  methods: {
    generateConfig() {
      this.showOutput = true;
      // Scroll down to show output after a brief delay
      setTimeout(() => {
        const outputElement = document.querySelector('.mt-10');
        if (outputElement) {
          outputElement.scrollIntoView({ behavior: 'smooth' });
        }
      }, 100);
    },
    copyToClipboard() {
      navigator.clipboard.writeText(this.configOutput)
        .then(() => {
          alert('Configuration copied to clipboard!');
        })
        .catch(err => {
          console.error('Failed to copy: ', err);
        });
    },
    copyCommands() {
      navigator.clipboard.writeText(this.installCommands)
        .then(() => {
          alert('Commands copied to clipboard!');
        })
        .catch(err => {
          console.error('Failed to copy: ', err);
        });
    },
    generateViteConfig(config) {
      let viteConfig = `// vite.config.js${config.typescript === 'yes' ? 'ts' : ''}\n`;
      viteConfig += `import { defineConfig } from 'vite'\n`;
      viteConfig += `import vue from '@vitejs/plugin-vue'\n`;
      
      if (config.features.pwa) {
        viteConfig += `import { VitePWA } from 'vite-plugin-pwa'\n`;
      }
      
      viteConfig += `\nexport default defineConfig({\n`;
      viteConfig += `  plugins: [\n    vue()`;
      
      if (config.features.pwa) {
        viteConfig += `,\n    VitePWA({\n`;
        viteConfig += `      registerType: 'autoUpdate',\n`;
        viteConfig += `      includeAssets: ['favicon.ico', 'robots.txt', 'apple-touch-icon.png'],\n`;
        viteConfig += `      manifest: {\n`;
        viteConfig += `        name: '${config.projectName}',\n`;
        viteConfig += `        short_name: '${config.projectName}',\n`;
        viteConfig += `        theme_color: '#4f46e5',\n`;
        viteConfig += `        icons: [\n`;
        viteConfig += `          {\n`;
        viteConfig += `            src: 'pwa-192x192.png',\n`;
        viteConfig += `            sizes: '192x192',\n`;
        viteConfig += `            type: 'image/png'\n`;
        viteConfig += `          },\n`;
        viteConfig += `          {\n`;
        viteConfig += `            src: 'pwa-512x512.png',\n`;
        viteConfig += `            sizes: '512x512',\n`;
        viteConfig += `            type: 'image/png'\n`;
        viteConfig += `          }\n`;
        viteConfig += `        ]\n`;
        viteConfig += `      }\n`;
        viteConfig += `    })`;
      }
      
      viteConfig += `\n  ],\n`;
      
      // Resolve aliases
      viteConfig += `  resolve: {\n`;
      viteConfig += `    alias: {\n`;
      viteConfig += `      '@': '/src'\n`;
      viteConfig += `    }\n`;
      viteConfig += `  },\n`;
      
      // Server settings
      viteConfig += `  server: {\n`;
      viteConfig += `    port: 3000,\n`;
      viteConfig += `    open: true\n`;
      viteConfig += `  },\n`;
      
      // Build settings
      viteConfig += `  build: {\n`;
      viteConfig += `    outDir: 'dist',\n`;
      viteConfig += `    assetsDir: 'assets'\n`;
      viteConfig += `  }`;
      
      // Test config
      if (config.features.testing) {
        viteConfig += `,\n  test: {\n`;
        viteConfig += `    globals: true,\n`;
        viteConfig += `    environment: 'jsdom'\n`;
        viteConfig += `  }`;
      }
      
      viteConfig += `\n})\n`;

      return viteConfig;
    },
    generateWebpackConfig(config) {
      let webpackConfig = `// vue.config.js\n`;
      webpackConfig += `const { defineConfig } = require('@vue/cli-service')\n`;
      
      webpackConfig += `\nmodule.exports = defineConfig({\n`;
      webpackConfig += `  transpileDependencies: true,\n`;
      
      // Output directory
      webpackConfig += `  outputDir: 'dist',\n`;
      
      // Dev server settings
      webpackConfig += `  devServer: {\n`;
      webpackConfig += `    port: 8080,\n`;
      webpackConfig += `    open: true,\n`;
      webpackConfig += `    historyApiFallback: true\n`;
      webpackConfig += `  },\n`;
      
      // Chain webpack
      webpackConfig += `  chainWebpack: config => {\n`;
      webpackConfig += `    config.resolve.alias.set('@', require('path').join(__dirname, 'src'))\n`;
      
      if (config.cssFramework === 'tailwind') {
        webpackConfig += `    config.module\n`;
        webpackConfig += `      .rule('css')\n`;
        webpackConfig += `      .oneOf('vue')\n`;
        webpackConfig += `      .use('postcss-loader')\n`;
        webpackConfig += `      .tap(options => {\n`;
        webpackConfig += `        return {\n`;
        webpackConfig += `          ...options,\n`;
        webpackConfig += `          postcssOptions: {\n`;
        webpackConfig += `            plugins: [\n`;
        webpackConfig += `              require('tailwindcss'),\n`;
        webpackConfig += `              require('autoprefixer')\n`;
        webpackConfig += `            ]\n`;
        webpackConfig += `          }\n`;
        webpackConfig += `        }\n`;
        webpackConfig += `      })\n`;
      }
      
      webpackConfig += `  }`;
      
      if (config.deployment === 'ssr') {
        webpackConfig += `,\n  // Enable SSR\n`;
        webpackConfig += `  ssr: {\n`;
        webpackConfig += `    entry: './src/main-server.js',\n`;
        webpackConfig += `    directives: {\n`;
        webpackConfig += `      // Handle server-side directives\n`;
        webpackConfig += `    }\n`;
        webpackConfig += `  }`;
      }
      
      webpackConfig += `\n})\n`;

      return webpackConfig;
    }
  }
}
</script>