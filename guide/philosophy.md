# vite理念

## 精简可扩展的核心

Vite不打算覆盖每个用户的每种用例。Vite旨在支持构建Web应用程序的最常见模式，但[Vite核心](https://github.com/vitejs/vite)必须保持精简的API表面以确保项目的可维护性长期保持。这一目标得益于[Vite的基于Rollup的插件系统](./api-plugin.md)。可以作为外部插件实现的功能通常不会添加到Vite核心中。[vite-plugin-pwa](https://vite-pwa-org.netlify.app/)是Vite核心的一个很好的示例，还有许多[得到良好维护的插件](https://github.com/vitejs/awesome-vite#plugins)可以满足您的需求。Vite与Rollup项目密切合作，以确保插件在纯Rollup和Vite项目中尽可能多地使用，并在可能的情况下将所需的扩展推送到插件API上游。

## 推动现代Web

Vite提供了倡导编写现代代码的功能，例如：

- 源代码只能使用ESM编写，非ESM依赖关系需要[预先打包为ESM](./dep-pre-bundling)才能正常工作。
- 鼓励使用[`new Worker`语法](./features#web-workers)编写Web workers，以遵循现代标准。
- 不能在浏览器中使用Node.js模块。

在添加新功能时，遵循这些模式以创建一个具有未来可靠性的API，这可能并不总是与其他构建工具兼容。

## 对性能的务实处理

Vite自其[起源](./why.md)以来一直专注于性能。其开发服务器架构允许在项目规模扩大时保持快速的HMR。Vite使用像[esbuild](https://esbuild.github.io/)和[SWC](https://github.com/vitejs/vite-plugin-react-swc)这样的本地工具来执行密集任务，但将其余的代码保持为JS以在速度和灵活性之间保持平衡。在需要时，框架插件将借助[Babel](https://babeljs.io/)来编译用户代码。在构建时，Vite当前使用[Rollup](https://rollupjs.org/)，其中捆绑大小和可以访问各种插件生态系统更重要，而不是纯速度。Vite将在内部不断发展，使用新库来改善DX，同时保持其API的稳定性。

## 在Vite之上构建框架

尽管用户可以直接使用Vite，但它在创建框架的工具方面表现出色。Vite核心是与框架无关的，但对于每个UI框架都有经过精心打磨的插件。其[JS API](./api-javascript.md)允许应用框架作者使用Vite功能来为其用户创建定制体验。Vite包括对[SSR基元](./ssr.md)的支持，通常存在于更高级工具中，但对于构建现代Web框架至关重要。而Vite插件则通过提供一种在不同框架之间共享的方式来完成整体。当与[后端框架](./backend-integration.md)（如[Ruby](https://vite-ruby.netlify.app/)和[Laravel](https://laravel.com/docs/10.x/vite)）配对使用时，Vite也非常适合。

## 活跃的生态系统

Vite的演进是框架和插件维护者、用户以及Vite团队之间的合作。一旦项目采用Vite，我们鼓励积极参与Vite核心的开发。我们与生态系统中的主要项目密切合作，以尽量减少每个发布版本的回归，辅助工具如[vite-ecosystem-ci](https://github.com/vitejs/vite-ecosystem-ci)帮助我们在选定的PR上运行使用Vite的主要项目的CI，并为我们提供了生态系统对发布的反应状态。我们努力在问题影响用户之前解决它们，并允许项目尽快更新到下一个版本。如果您正在使用Vite，欢迎您加入[Vite的Discord](https://chat.vitejs.dev)并参与项目。
