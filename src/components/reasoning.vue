<template>
  <section>
    <h2>Reasoning:</h2>
    <p><em>Why not use a bundler, like WebPack/Browserify/Parcel/StealJS/Fuse-Box/Etc?</em></p>
    <ul>
      <li>Because bundlers are designed around the limitations of the web. We are working with a different medium, Cross-Platform Desktop Apps (XPDAs).</li>
      <li>The purpose of a bundler is to bundle our code. Features like concatenating, tree-shaking, uglifying, and minifying our code doesn't really offer any benefit. Nor does reducing the number of simultaneous network requests for assets. All assets are local, because desktop apps should follow the best practice of "offline-first".</li>
      <li>Ultimately you are shipping an 80+ MB app to your end user, so the tiny optimizations made for the medium of web are quite arbitrary here.</li>
      <li>A much greater concern for desktop apps would be the amount of dependencies in your node_modules folder, since all dependencies, and their dependencies are shipped to the end user (this excludes devDependencies).</li>
      <li>If you wish to use additional features for development (linting, HMR, Sass, etc), I would recommend adding those features via a task runner, like Gulp, or just via simple npm scripts.</li>
    </ul>
    <p><em>Why not use a CDN for Vue/Vue-Router/Vuex/Etc instead of adding them as dependencies?</em></p>
    <ul>
      <li>Because for desktop apps you should always be designing with an "offline-first" mentality. Your app should still run if the user is in Airplane mode.</li>
      <li>Keeping them as dependencies allows you to easily handle version management.</li>
      <li>An alternative option would be to create a script that downloads the desired versions of these libraries into an untracked folder. This would mean you would have the desired versions, and no additional files or dependencies. Then run that script as a <code>postinstall</code> npm script. The downside to this is that it would be less familiar to other developers. Though technically more efficient, it is also slightly less maintable and requires documentation for future maintainers/contributors.</li>
    </ul>
  </section>
</template>

<script>
  module.exports = {
    name: 'reasoning'
  };
</script>
