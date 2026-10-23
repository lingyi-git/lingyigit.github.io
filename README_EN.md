Simplified Chinese | English

[!IMPORTANT]

To Strangers

This is a homepage made by a big shot; I took it and modified it a bit [doge]

<p>
<strong><h2>Lingyi's Homepage</h2></strong>
A simple little homepage; I got tired of the old one and made a new one
</p>

/screenshots/main.jpg

The homepage Logo font has been compressed. If letters other than the site Logo are used, they will revert to the default font. Here is the full font. If it cannot be downloaded, you can replace it with Pacifico-Regular-all.ttf in the font directory.

👀 Demo

Due to CDN caching, viewing the latest effect may require Ctrl + F5 to force refresh the browser cache

· Lingyi's Homepage

🎉 Features

· Loading animation
· Site introduction
· Hitokoto quote
· Date and time
· Real-time weather
· Time progress bar
· Music player
· Mobile adaptation

⚙️ Automatic Deployment

If you encounter errors in the build environment or packaging process, you can use GitHub Actions for automatic building

· After successfully forking the repository, go to the Actions page. If this is your first time enabling it, the prompt below will appear; click to enable
  /screenshots/step1.jpg
· Then any modification in the repository will trigger the workflow. After the workflow completes, a downloadable archive will be generated below; these are the built static files, which you can upload to your server yourself
  /screenshots/step2.jpg

⚙️ Manual Deployment

· Install node.js environment
  node > 16.16.0
  npm > 8.15.0
· Then run the cmd terminal as administrator, and cd to the project root directory
· Enter the following in the terminal:

```bash
# Install pnpm
npm install -g pnpm

# Install dependencies
pnpm install

# Preview
pnpm dev

# Build
pnpm build
```

After the build completes, static assets will be generated in the dist directory. You can upload the files in the dist folder to your server, or use hosting platforms such as Vercel to import and automatically deploy with one click

⚙️ Docker Deployment

Installation and configuration of Docker will not be explained here; please handle it yourself

```bash
# Build
docker build -t home .
# Run
docker run -p 12445:12445 -d home
```

⚙️ Vercel Deployment

Other deployment platforms are roughly the same and are not covered here

1. Click Fork in the upper right corner of this repository to copy this repository to your GitHub account
2. Copy the /.env.example file and rename it to /.env ( important )
3. Modify the configuration in /.env as needed
4. Click Deploy to deploy successfully

Website Links

You can customize website links in src/assets/siteLinks.json (to point to your own website):

```json
{
  "icon": "Blog",
  "name": "Blog",
  "link": "https://blog.imsyy.top/"
},
```

The icon for the website link can be added in src/components/Links/index.vue:

```js
// You can go to https://www.xicons.org to choose and import here
// The fa type is imported here
import {
  Link,
  Blog,
  CompactDisc,
  Cloud,
  Compass,
  Book,
  Fire,
  LaptopCode,
} from "@vicons/fa";

...

// Website link icons
const siteIcon = {
  Blog,
  Cloud,
  CompactDisc,
  Compass,
  Book,
  Fire,
  LaptopCode,
};
```

Social Links

You can customize social links in src/assets/socialLinks.json.

Weather

Weather and location retrieval require the relevant API from Amap Open Platform

· Go to the Amap Open Platform Console to create a Key of type Web Service, and fill the Key into VITE_WEATHER_KEY in .env

You can also replace it with other methods yourself

Music

This project uses the Aplayer music player based on MetingJS, allowing quick customization of playlists
\*Only supports Mainland China

Please change the song-related parameters in the .env file to customize the playlist

```bash
# Song API address
VITE_SONG_API = "https://api-meting.imsyy.top"
# Song server ( netease-NetEase Cloud Music, tencent-QQ Music )
VITE_SONG_SERVER = "netease"
# Play type ( song-song, playlist-playlist, album-album, search-search, artist-artist )
VITE_SONG_TYPE = "playlist"
# Play ID
VITE_SONG_ID = "7452421335"
```

Font

Currently uses the HarmonyOS Sans open-source font, with font splitting to improve loading speed

Because this site's CDN has hotlink protection enabled, non-site domains cannot access it. Please change the font import link to the following content, otherwise the custom font will fail

https://s1.hdslb.com/bfs/static/jinkela/long/font/regular.css

<details>
<summary>Old method</summary>

Because this project introduces Chinese fonts, Chinese fonts need to be compressed to improve webpage loading speed ( you can also stop using Chinese fonts )

Remove Traditional Chinese from Chinese font

· Install Python 3.7 and pip
· Run pip install fonttools
· Download sc_unicode.txt
· Run pyftsubset FontName.ttf --unicodes-file=sc_unicode.txt

Further font compression

· Compile and install Google woff2

```bash
sudo apt-get install -y git g++ make
git clone --recursive https://github.com/google/woff2.git
cd woff2
make clean all
```

· Compress the font again

```
./woff2_compress ./FontName.ttf
```

· Finally, the original font can be lazy-loaded, loading the compressed font first

For details, go to Hongmo Space Station to view the original article

</details>

Website Icon and Website Background

Website Background

You can modify the website background in public/images

If you want to add more local images as website backgrounds, rename the images in the form background+number and modify src/components/Background/index.vue:

```js
if (type == 0) {
  // Modify the first number after Math.random() here to the number of images
  bgUrl.value = `/images/background${Math.floor(Math.random() * 10 + 1)}.webp`;
}
```

Website Icon

You can modify the website icon in public/images/icon.

Tech Stack

· Vue
· Vite
· Pinia
· IconPark
· xicons
· Aplayer

API

· Han Xiaohan WebAPI
· Botian API
· Teacher API
· Amap Open Platform
· Hitokoto

Star History

https://api.star-history.com/svg?repos=imsyy/home&type=Date

<a title="SSL" target="_blank" href="https://myssl.com/seal/detail?domain=blog.imsyy.top"><img src="https://img.shields.io/badge/MySSL-Security%20Certification-brightgreen"></a>&nbsp;<a title="CDN" target="_blank" href="https://cdnjs.com/"><img src="https://img.shields.io/badge/CDN-Cloudflare-blue"></a>&nbsp;<a title="Copyright" target="_blank" href="https://imsyy.top/"><img src="https://img.shields.io/badge/Copyright%20%C2%A9%202020--2023-Nameless-red"></a>