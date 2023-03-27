# Kotlin-xclangspec

Xcode Syntax Highlighting for Kotlin

This adds syntax highlighting for Kotlin source files to Xcode. 

## Installation

To checkout the repository and run the setup script, open Terminal.app and run:

```
git clone https://github.com/skiptools/Kotlin-xclangspec
cd Kotlin-xclangspec
./setup.sh
```

When you next launch Xcode 14, you should be greeted with a dialog
such as:

```
Unexpected code bundle "Kotlin.ideplugin"

The "Kotlin.ideplugin" code bundle is not provided by Apple. Loading code not provided by Apple can have a negative effect on the safety and stability of Xcode or related tools.
```

Select "Load Bundle" to proceed, or "Skip Bundle" to cancel.

Once loaded, any Kotlin files with the ".kt" or ".kts" will
have the Kotlin syntax highlighting applied in the Xcode editor window.


## Manual installation

Due to the aforementioned broken APIs, manual installation works slightly differently for Xcode 11 vs. other versions. 

Please note that the `Plug-ins` and `Specifications` directories might not exist, and if they don't, you'll need to create them.

- Copy the `Kotlin.ideplugin` directory to `~/Library/Developer/Xcode/Plug-ins/`:

```
cp -r Kotlin.ideplugin ~/Library/Developer/Xcode/Plug-ins/
```
- Copy the `Kotlin.xclangspec` file to `~/Library/Developer/Xcode/Specifications`:

```
cp Kotlin.xclangspec ~/Library/Developer/Xcode/Specifications/
```


## How to update this plugin for new versions of Xcode

1. Install the new version of Xcode. 
2. Get the UUID of the version using the following command in Terminal: 
    
    `defaults read /Applications/Xcode.app/Contents/Info DVTPlugInCompatibilityUUID`
    
    or, for beta versions,
    
    `defaults read /Applications/Xcode-beta.app/Contents/Info DVTPlugInCompatibilityUUID`
3. Copy the UUID. 
4. Paste the UUID into the list of `DVTPlugInCompatibilityUUIDs` in `Kotlin.ideplugin/Contents/Info.plist`. Do not remove any old IDs, just add the new one. 
5. Reinstall the plugin using whatever method you were using above. You will need to restart Xcode to validate that your changes worked. 
6. If it worked, submit a pull request with this change. If it didn't work, please file an issue. 
   
Note that most UUIDs change from the beta to the final version, so we do not recommend adding UUIDs for betas except during "beta season" of an upcoming major release. 


## History

This is adapted from https://github.com/erica/TypeScript-xclangspec which was packaged for Xcode 10.1 from original repo at https://github.com/steventroughtonsmith/lua-xclangspec, which in turn was packaged for Xcode 9.2 from original repo at https://github.com/bastos/lua-xcode-coloring. Also uses code and docs from https://github.com/apollographql/xcode-graphql/blob/main/README.md

Kotlin Syntax definition is taken from: https://github.com/touchlab/xcode-kotlin

See also: https://github.com/bebrws/rust-xcode-plugin

