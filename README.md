# LegacyLauncher - Connect alpha/classic version on a Minecraft server !
Hacky code to launch old versions of Minecraft from the new launcher (or not) !

This particular fork is useful for launching alpha/classic versions of minecraft with server parameters such as the IP address and the port. <b>Allowing players to connect to alpha/classic servers</b> (there is not connexion menu in game, the server parameters need to be passed as Applet arguments).

Only tested for alpha versions of the game, compatibility with modern versions of the game is not guaranteed.

## Build

Use
`gradle build`

## Guide to use this launcher

You can use this launcher to launch an alpha/classic version and play it in single player (not relay useful, already possible in the official launcher).

But the most important part is to use this launcher to connect an alpha/classic version to a Minecraft server.

## Download an alpha/classic version of Minecraft
You need to have an alpha version of Minecraft launchable in the official launcher.

### Play an alpha version of Minecraft from the official launcher

First start the Minecraft official launcher, edit the settings and enable "Show historical versions of Minecraft: Java Edition in the launcher".

[IMG TO ADD ON GITHUB]

Then create a new "installation" of Minecraft with an alpha version for example v0.30

[IMG TO ADD ON GITHUB]


### Download an archived version of Minecraft alpha

Use a list of old version of Minecraft from Omniarchive Wiki for example :
[http://omniarchive.shoutwiki.com/wiki/Classic]()

You can also download servers from this list.

Many archived version redirect to Minecraft Fandom Wiki when you can sometimes download the needed files :

[IMG TO ADD ON GITHUB]

Once the zip file is downloaded, copy it's content to the `version` folder of your `.minecraft` folder.
Now you should be able to follow the steps described in "Play an alpha version of Minecraft from the official launcher".

## Launch an alpha/classic version of Minecraft

The methods given need to use the official Minecraft launcher (tested for version 2.2.2311).

### Add Minecraft alpha server capability to the official launcher (using this launcher)

Download or build the launcher and copy it to the library folder of your Minecraft path. For the default path copy the jar file to
`%APPDATA%\.minecraft\libraries\net\minecraft\launchwrapper\1.12.99.1\launchwrapper-1.12.99.1.jar`

Then go to the `versions` folder at `%APPDATA%\.minecraft\versions` and copy the version folder you want and rename it `<version>-connect` for example.

[IMG TO ADD LATER]

Then rename the `.jar` and `.json` with the same of the folder.

Edit the `.json` file to remove the following sections :
- assetIndex
- assets
- downloads

Then replace the content of the `id` section with the new version name (ex : `<version>-connect`).
Remove the object with name starting with `net.minecraft:launchwrapper` from the libraries section.
And add the following in the `librearies` section :
```json
{
    "name":"net.minecraft:launchwrapper:1.12.99.1"
},
```

To add a server ip address and port edit the attribute `minecraftArguments` like that :
```json
"minecraftArguments":"${auth_player_name} ${auth_session} [SERVER_ADDRESS] [SERVER_PORT] --gameDir ${game_directory} --assetsDir ${game_assets} --tweakClass net.minecraft.launchwrapper.AlphaVanillaTweaker"
```

The obtained file should look like this one :

This json file is configured to connect to a server with address `localhost` and port `25565`.

<details>
  <summary>c0.30_01c-connect.json</summary>


  ```json
  {
  "id":"c0.30_01c-connect",
  "libraries":[
    {
      "name":"net.minecraft:launchwrapper:1.12.99.1"
    },
    {
      "downloads":{
        "artifact":{
          "path":"net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar",
          "sha1":"6065cc95c661255349c1d0756657be17c29a4fd3",
          "size":61311,
          "url":"https://libraries.minecraft.net/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar"
        }
      },
      "name":"net.sf.jopt-simple:jopt-simple:4.5"
    },
    {
      "downloads":{
        "artifact":{
          "path":"org/ow2/asm/asm-all/4.1/asm-all-4.1.jar",
          "sha1":"054986e962b88d8660ae4566475658469595ef58",
          "size":214592,
          "url":"https://libraries.minecraft.net/org/ow2/asm/asm-all/4.1/asm-all-4.1.jar"
        }
      },
      "name":"org.ow2.asm:asm-all:4.1"
    },
    {
      "downloads":{
        "artifact":{
          "path":"net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar",
          "sha1":"39c7796b469a600f72380316f6b1f11db6c2c7c4",
          "size":208338,
          "url":"https://libraries.minecraft.net/net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar"
        }
      },
      "name":"net.java.jinput:jinput:2.0.5"
    },
    {
      "downloads":{
        "artifact":{
          "path":"net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar",
          "sha1":"e12fe1fda814bd348c1579329c86943d2cd3c6a6",
          "size":7508,
          "url":"https://libraries.minecraft.net/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar"
        }
      },
      "name":"net.java.jutils:jutils:1.0.0"
    },
    {
      "downloads":{
        "artifact":{
          "path":"org/lwjgl/lwjgl/lwjgl/2.9.0/lwjgl-2.9.0.jar",
          "sha1":"5654d06e61a1bba7ae1e7f5233e1106be64c91cd",
          "size":994633,
          "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl/2.9.0/lwjgl-2.9.0.jar"
        }
      },
      "name":"org.lwjgl.lwjgl:lwjgl:2.9.0",
      "rules":[
        {
          "action":"allow"
        },
        {
          "action":"disallow",
          "os":{
            "name":"osx",
            "version":"^10\\.5\\.\\d$"
          }
        }
      ]
    },
    {
      "downloads":{
        "artifact":{
          "path":"org/lwjgl/lwjgl/lwjgl_util/2.9.0/lwjgl_util-2.9.0.jar",
          "sha1":"a778846b64008fc7f48ead2377f034e547991699",
          "size":173360,
          "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl_util/2.9.0/lwjgl_util-2.9.0.jar"
        }
      },
      "name":"org.lwjgl.lwjgl:lwjgl_util:2.9.0",
      "rules":[
        {
          "action":"allow"
        },
        {
          "action":"disallow",
          "os":{
            "name":"osx",
            "version":"^10\\.5\\.\\d$"
          }
        }
      ]
    },
    {
      "downloads":{
        "classifiers":{
          "natives-linux":{
            "path":"org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-linux.jar",
            "sha1":"2ba5dcb11048147f1a74eff2deb192c001321f77",
            "size":569061,
            "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-linux.jar"
          },
          "natives-osx":{
            "path":"org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-osx.jar",
            "sha1":"6621b382cb14cc409b041d8d72829156a87c31aa",
            "size":518924,
            "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-osx.jar"
          },
          "natives-windows":{
            "path":"org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-windows.jar",
            "sha1":"3f11873dc8e84c854ec7c5a8fd2e869f8aaef764",
            "size":609967,
            "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-windows.jar"
          }
        }
      },
      "extract":{
        "exclude":[
          "META-INF/"
        ]
      },
      "name":"org.lwjgl.lwjgl:lwjgl-platform:2.9.0",
      "natives":{
        "linux":"natives-linux",
        "osx":"natives-osx",
        "windows":"natives-windows"
      },
      "rules":[
        {
          "action":"allow"
        },
        {
          "action":"disallow",
          "os":{
            "name":"osx",
            "version":"^10\\.5\\.\\d$"
          }
        }
      ]
    },
    {
      "downloads":{
        "artifact":{
          "path":"org/lwjgl/lwjgl/lwjgl/2.9.1-nightly-20130708-debug3/lwjgl-2.9.1-nightly-20130708-debug3.jar",
          "sha1":"884511652c756fac16b37236f863f346bd1ea121",
          "size":996625,
          "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl/2.9.1-nightly-20130708-debug3/lwjgl-2.9.1-nightly-20130708-debug3.jar"
        }
      },
      "name":"org.lwjgl.lwjgl:lwjgl:2.9.1-nightly-20130708-debug3",
      "rules":[
        {
          "action":"allow",
          "os":{
            "name":"osx",
            "version":"^10\\.5\\.\\d$"
          }
        }
      ]
    },
    {
      "downloads":{
        "artifact":{
          "path":"org/lwjgl/lwjgl/lwjgl_util/2.9.1-nightly-20130708-debug3/lwjgl_util-2.9.1-nightly-20130708-debug3.jar",
          "sha1":"fb693ba4e22a85432a32e8a048893dc7a92f42ac",
          "size":173338,
          "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl_util/2.9.1-nightly-20130708-debug3/lwjgl_util-2.9.1-nightly-20130708-debug3.jar"
        }
      },
      "name":"org.lwjgl.lwjgl:lwjgl_util:2.9.1-nightly-20130708-debug3",
      "rules":[
        {
          "action":"allow",
          "os":{
            "name":"osx",
            "version":"^10\\.5\\.\\d$"
          }
        }
      ]
    },
    {
      "downloads":{
        "classifiers":{
          "natives-osx":{
            "path":"org/lwjgl/lwjgl/lwjgl-platform/2.9.1-nightly-20130708-debug3/lwjgl-platform-2.9.1-nightly-20130708-debug3-natives-osx.jar",
            "sha1":"a9b83ad85742cad09c3574a91b0423bac3f7a0f5",
            "size":458181,
            "url":"https://libraries.minecraft.net/org/lwjgl/lwjgl/lwjgl-platform/2.9.1-nightly-20130708-debug3/lwjgl-platform-2.9.1-nightly-20130708-debug3-natives-osx.jar"
          }
        }
      },
      "extract":{
        "exclude":[
          "META-INF/"
        ]
      },
      "name":"org.lwjgl.lwjgl:lwjgl-platform:2.9.1-nightly-20130708-debug3",
      "natives":{
        "linux":"natives-linux",
        "osx":"natives-osx",
        "windows":"natives-windows"
      },
      "rules":[
        {
          "action":"allow",
          "os":{
            "name":"osx",
            "version":"^10\\.5\\.\\d$"
          }
        }
      ]
    },
    {
      "downloads":{
        "classifiers":{
          "natives-linux":{
            "path":"net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-linux.jar",
            "sha1":"7ff832a6eb9ab6a767f1ade2b548092d0fa64795",
            "size":10362,
            "url":"https://libraries.minecraft.net/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-linux.jar"
          },
          "natives-osx":{
            "path":"net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-osx.jar",
            "sha1":"53f9c919f34d2ca9de8c51fc4e1e8282029a9232",
            "size":12186,
            "url":"https://libraries.minecraft.net/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-osx.jar"
          },
          "natives-windows":{
            "path":"net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-windows.jar",
            "sha1":"385ee093e01f587f30ee1c8a2ee7d408fd732e16",
            "size":155179,
            "url":"https://libraries.minecraft.net/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-windows.jar"
          }
        }
      },
      "extract":{
        "exclude":[
          "META-INF/"
        ]
      },
      "name":"net.java.jinput:jinput-platform:2.0.5",
      "natives":{
        "linux":"natives-linux",
        "osx":"natives-osx",
        "windows":"natives-windows"
      }
    },
    {
      "downloads":{
        "classifiers":{
          "natives-linux":{
            "path":"net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-linux.jar",
            "sha1":"7ff832a6eb9ab6a767f1ade2b548092d0fa64795",
            "size":10362,
            "url":"https://libraries.minecraft.net/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-linux.jar"
          },
          "natives-osx":{
            "path":"net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-osx.jar",
            "sha1":"53f9c919f34d2ca9de8c51fc4e1e8282029a9232",
            "size":12186,
            "url":"https://libraries.minecraft.net/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-osx.jar"
          },
          "natives-windows":{
            "path":"net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-windows.jar",
            "sha1":"385ee093e01f587f30ee1c8a2ee7d408fd732e16",
            "size":155179,
            "url":"https://libraries.minecraft.net/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-windows.jar"
          }
        }
      },
      "extract":{
        "exclude":[
          "META-INF/"
        ]
      },
      "name":"net.java.jinput:jinput-platform:2.0.5",
      "natives":{
        "linux":"natives-linux",
        "osx":"natives-osx",
        "windows":"natives-windows"
      }
    }
  ],
  "mainClass":"net.minecraft.launchwrapper.Launch",
  "minecraftArguments":"${auth_player_name} ${auth_session} --gameDir ${game_directory} --assetsDir ${game_assets} --tweakClass net.minecraft.launchwrapper.AlphaVanillaTweaker",
  "minimumLauncherVersion":7,
  "releaseTime":"2009-12-21T22:00:00+00:00",
  "time":"2009-12-21T22:00:00+00:00",
  "type":"old_alpha"
}
  ```

</details>

Now you can select the new version in the official launcher.

If you set an IP address, the game will automatically connect to the server.

### Launch Minecraft alpha without the official launcher after setup

<b>Tested only with Windows 10 and default minecraft path</b>

Start an alpha version of Minecraft from the official launcher.

While the game is still open (important) go to `%APPDATA%\.minecraft\bin\` and copy the repertory with the more recent date of cration.

[IMG TO ADD ON GITHUB]

Now you can start the game using the launcher

Download or build the launcher and copy it somewhere (ex: `%APPDATA%\.minecraft\launchwrapper-1.12.99.1.jar`)

```shell
"C:\Program Files (x86)\Minecraft\runtime\jre-legacy\windows-x64\jre-legacy\bin\javaw.exe" ^
-Djava.library.path=<PATH OF THE COPY OF THE BIN REP> ^
-Dminecraft.client.jar=%APPDATA%\.minecraft\versions\<VERSION>\<VERSION>.jar ^
-cp <PATH TO launchwrapper-1.12.99.1.jar>;^%APPDATA%\.minecraft\libraries\net\sf\jopt-simple\jopt-simple\4.5\jopt-simple-4.5.jar;%APPDATA%\.minecraft\libraries\org\ow2\asm\asm-all\4.1\asm-all-4.1.jar;%APPDATA%\.minecraft\libraries\net\java\jinput\jinput\2.0.5\jinput-2.0.5.jar;%APPDATA%\.minecraft\libraries\net\java\jutils\jutils\1.0.0\jutils-1.0.0.jar;%APPDATA%\.minecraft\libraries\org\lwjgl\lwjgl\lwjgl\2.9.0\lwjgl-2.9.0.jar;%APPDATA%\.minecraft\libraries\org\lwjgl\lwjgl\lwjgl_util\2.9.0\lwjgl_util-2.9.0.jar;%APPDATA%\.minecraft\versions\<VERSION>\<VERSION>.jar ^
-Xmx2G -XX:+UseG1GC ^
net.minecraft.launchwrapper.Launch <USERNAME> <TOKEN> [OPTIONAL SERVER IP] [OPTIONAL SERVER PORT] ^
--gameDir %APPDATA%\.minecraft ^
--assetsDir %APPDATA%\.minecraft\assets\virtual\legacy ^
--tweakClass net.minecraft.launchwrapper.AlphaVanillaTweaker
```

You can enter any token you want, the verification servers are down anyway.

Examples :

- Single player :

```shell
"C:\Program Files (x86)\Minecraft\runtime\jre-legacy\windows-x64\jre-legacy\bin\javaw.exe" ^
-Djava.library.path=%APPDATA%\.minecraft\bin\ALPHA ^
-Dminecraft.client.jar=%APPDATA%\.minecraft\versions\c0.30_01c\c0.30_01c.jar ^
-cp %APPDATA%\.minecraft\launchwrapper-1.12.99.1.jar;%APPDATA%\.minecraft\libraries\net\sf\jopt-simple\jopt-simple\4.5\jopt-simple-4.5.jar;%APPDATA%\.minecraft\libraries\org\ow2\asm\asm-all\4.1\asm-all-4.1.jar;%APPDATA%\.minecraft\libraries\net\java\jinput\jinput\2.0.5\jinput-2.0.5.jar;%APPDATA%\.minecraft\libraries\net\java\jutils\jutils\1.0.0\jutils-1.0.0.jar;%APPDATA%\.minecraft\libraries\org\lwjgl\lwjgl\lwjgl\2.9.0\lwjgl-2.9.0.jar;%APPDATA%\.minecraft\libraries\org\lwjgl\lwjgl\lwjgl_util\2.9.0\lwjgl_util-2.9.0.jar;%APPDATA%\.minecraft\versions\c0.30_01c\c0.30_01c.jar ^
-Xmx2G -XX:+UseG1GC ^
net.minecraft.launchwrapper.Launch Azuxul token ^
--gameDir %APPDATA%\.minecraft ^
--assetsDir %APPDATA%\.minecraft\assets\virtual\legacy ^
--tweakClass net.minecraft.launchwrapper.AlphaVanillaTweaker
```

- Connexion to a server on ip localhost with port 25565 :

```shell
"C:\Program Files (x86)\Minecraft\runtime\jre-legacy\windows-x64\jre-legacy\bin\javaw.exe" ^
-Djava.library.path=%APPDATA%\.minecraft\bin\ALPHA ^
-Dminecraft.client.jar=%APPDATA%\.minecraft\versions\c0.30_01c\c0.30_01c.jar ^
-cp %APPDATA%\.minecraft\launchwrapper-1.12.jar;%APPDATA%\.minecraft\libraries\net\sf\jopt-simple\jopt-simple\4.5\jopt-simple-4.5.jar;%APPDATA%\.minecraft\libraries\org\ow2\asm\asm-all\4.1\asm-all-4.1.jar;%APPDATA%\.minecraft\libraries\net\java\jinput\jinput\2.0.5\jinput-2.0.5.jar;%APPDATA%\.minecraft\libraries\net\java\jutils\jutils\1.0.0\jutils-1.0.0.jar;%APPDATA%\.minecraft\libraries\org\lwjgl\lwjgl\lwjgl\2.9.0\lwjgl-2.9.0.jar;%APPDATA%\.minecraft\libraries\org\lwjgl\lwjgl\lwjgl_util\2.9.0\lwjgl_util-2.9.0.jar;%APPDATA%\.minecraft\versions\c0.30_01c\c0.30_01c.jar ^
-Xmx2G -XX:+UseG1GC ^
net.minecraft.launchwrapper.Launch Azuxul token localhost 25565 ^
--gameDir %APPDATA%\.minecraft ^
--assetsDir %APPDATA%\.minecraft\assets\virtual\legacy ^
--tweakClass net.minecraft.launchwrapper.AlphaVanillaTweaker
```

