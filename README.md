# Unity Android StreamingAssets
Sometimes, you may want to use `File.ReadAllText`, `File.Exists` etc. functions on files that are located at `Application.streamingAssetsPath`. However, on Android platform, these files are located inside the application file (*.apk* or *.jar*, not sure) and can only be accessed via **WWW** class.

This script extracts the contents of StreamingAssets to local file system (**Application.temporaryCachePath/assets/**, to be precise) using **SharpZibLib** library so that you can perform regular file operations on these files. 

- Use `AndroidStreamingAssets.Path` to access the root directory of the extracted StreamingAssets. This property internally calls the `AndroidStreamingAssets.Extract()` function the first time you access it. 

- `AndroidStreamingAssets.Extract()` function extracts the StreamingAssets from the application and can optionally be called manually to avoid any stutters when you first call *AndroidStreamingAssets.Path*. Be aware that each call to AndroidStreamingAssets.Extract() function extracts the StreamingAssets over and over again; so it is sufficient and recommended to call this function just once when your application starts. 

This script requires **SharpZipLib** to extract the StreamingAssets (you can just import the *.dll* file to your project): https://github.com/icsharpcode/SharpZipLib/releases
