# Container Images
Container Images represent a potential vulnerability if they contain information that they should not. Running `docker save -o` and extracting the file with `tar -xvf` will expose the various layers in the container image that instruct the image creation process
## Contents
> Use the `jq` tool to print the `JSON` in a manageable way. 
- `manifest.json` &mdash; The "manifest" is a list of container image layers that compose the final container image. !
- `Config` &mdash; represents the underlying configuration commands used to build the image. 

![](../../TryHackMe/events/AoC-2021/AoC-2021_Photos/Day_18/04_AoC_Day_18_01-06-22-extract-and-manifest-print.png)

These files represent the various container image layers. Inspecting the layers of a `config` file will tell us how the image was built. 

![](../../TryHackMe/events/AoC-2021/AoC-2021_Photos/Day_18/05_AoC_Day_18_01-06-22-github-repo-clone.png)

The first layer of the manifest configuration file details the final image configuration as it is intended to run on the host booting the container. However, the next section of curly braces has much more robust information. 

The image above, for example contains `"empty_layer": true` lines, meaning those layers are not retained in the overall container image as one of the layers in `manifest.json`. 