<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
***
-->
<div align="center">

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![CERN OHL W v2 License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]
</div>

<!-- PROJECT LOGO -->
<div align="center">
  <a href="https://github.com/dubpixel/dpx_kicad">
    <img src="images/logo.png" alt="Logo" height="120">
  </a>
<h1 align="center">DPX_KICAD</h1>
<h3 align="center"><i>Personal KiCad library — symbols, footprints, 3D models, and design rules</i></h3>
  <p align="center">
    A personal KiCad component library maintained by a single designer, built up over time. Not a general-purpose public library, but shared openly.
    <br />
     »  
     <a href="https://github.com/dubpixel/dpx_kicad"><strong>Project Here!</strong></a>
     »  
     <br />
    <a href="https://github.com/dubpixel/dpx_kicad/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/dubpixel/dpx_kicad/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
    </p>
</div>

<br />

<!-- TABLE OF CONTENTS -->
<!-- ABOUT THE PROJECT -->
<h3>About The Project</h3>

This is a personal KiCad component library that's been built up over years of PCB design work. It lives on Google Drive and stays synced across all my machines. The library contains custom symbols, footprints, and 3D models that have been cleaned up, renamed, and migrated from various sources — SnapEDA, SamacSys, random CAD downloads, you name it.

The `zusr_automatic` folder is basically a staging area where parts from SamacSys and ImpartGUI imports land before I clean them up and move them into the permanent libraries. Don't add this folder to your global KiCad library paths — it's intentionally messy intake space. Same goes for `zzz_other_peoples_libs`, which I keep around purely as reference material and a copy-source when I need something specific.

**Key features:**
- Custom symbols organized in `zusr_sym`
- Custom footprints in `zusr_foot`
- Large collection of 3D models in `zusr_3D`
- Design rules and board setups in `zusr_dru`
- KiCad preference backups in `zusr_preferences`, including library tables for easy machine-to-machine porting

<details>
<summary>Images</summary>

### FRONT
![FRONT][product-front]

</details>

### Built With

- [![KiCad][kicad-shield]][kicad-url]
- [![Google Drive][gdrive-shield]][gdrive-url]
- [![Git][git-shield]][git-url]
- [![Git LFS][git-lfs-shield]][git-lfs-url]


<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

### Prerequisites

- KiCad 9
- Google Drive synced locally
- Git with Git LFS installed

**KiCad Plugins (via PCM):**

*Critical KiCad Plugins*
- marbastlib
- KiKit
- Interactive HTML BOM
- KiBuzzard
- pcb2blender
- ImpartGUI
- Bouni's JLCPCB Tools


*General workflow tools:*
- PCB Action Tools
- Place Footprints
- Stretch
- Bulk Hide Silkscreen
- Round Tracks
- Connect Traces
- Component Search Engine

*Libraries and themes:*
- Generic Keyswitch Lib
- Generic Symbol Lib
- Elektruur Style Symbols
- Simple Libraries
- 4ms Libraries
- Solarized Dark Theme

### Installation

1. Clone the repo
2. Copy `sym-lib-table` and `fp-lib-table` from `zusr_preferences` into your KiCad config directory (`~/Library/Preferences/kicad/9.0/` on Mac)
3. Update the paths in those files to match where Google Drive syncs on your machine

**Recommended approach:** Create a `~/gdrive` symlink pointing to your Google Drive "My Drive" folder so paths stay consistent across machines:

```bash
ln -s "/Users/USERNAME/Library/CloudStorage/GoogleDrive-EMAIL/My Drive" ~/gdrive
```

Then update the library table paths to use `~/gdrive/_.DUBPIXEL/_...CIRCUIT_PROJECTS/DPX_KICAD/...` — this way you never need to edit paths again when setting up a new machine.

<!-- USAGE EXAMPLES -->
## Usage

**Folder structure and workflow:**

- `zusr_sym` / `zusr_foot` / `zusr_3D` — The main libraries. These are what you should add to your global KiCad paths.
- `zusr_automatic` — Staging area only. Parts imported from SamacSys/ImpartGUI land here. I clean them up, rename them, and promote them to the permanent libs. Do not reference this in your KiCad library tables.
- `zzz_other_peoples_libs` — Reference shelf. Downloaded libraries from other projects that I pull from occasionally. Also not wired into KiCad paths.
- `zusr_dru` — Design rule presets and board setup templates.
- `zusr_preferences` — Backup copies of my KiCad config files (library tables, hotkeys, etc.) for quick machine setup.

When you need a new part: import it to `zusr_automatic`, clean it up, test it, then move it to the appropriate permanent library folder.

### Using zusr_preferences

This folder contains manual snapshots of KiCad's config directory. Use it to get a new machine fully configured without starting from scratch.

**Backing up:**

When your KiCad setup is in a good state, copy the contents of your KiCad config directory into `zusr_preferences`:

```bash
cp -r ~/Library/Preferences/kicad/9.0/ ~/gdrive/DPX_KICAD/zusr_preferences/
```

Commit and push. Do this any time you make significant changes — new lib paths, hotkey changes, plugin installs, etc.

**Restoring on a new machine:**

1. Clone the repo / confirm Google Drive is synced
2. Copy the saved config into KiCad's preferences directory:

```bash
cp -r ~/gdrive/DPX_KICAD/zusr_preferences/ ~/Library/Preferences/kicad/9.0/
```

3. Open the `sym-lib-table` and `fp-lib-table` files and update any paths that don't match where Google Drive syncs on this machine
4. Launch KiCad — libraries and hotkeys should be intact, PCM will show your previously installed packages ready to reinstall

**Notes:**

- Do this *before* first launch on a new machine, otherwise KiCad generates fresh default configs and you'd be overwriting them anyway
- The path editing in step 3 goes away if you set up the `~/gdrive` symlink first — then paths are identical across all Macs and no editing is needed

<!-- ROADMAP -->
## Roadmap

- [ ] Standardize the `~/gdrive` symlink approach across all my machines so I never have to edit library table paths on fresh installs again
- [ ] Improve 3D model attribution in `zusr_3D` — track down original sources and add proper credits as I identify them
- [ ] Add direct PCM plugin identifiers to this README so I can quickly reinstall my full plugin stack on new machines without hunting through the plugin manager

See the [open issues](https://github.com/dubpixel/dpx_kicad/issues) for a full list of proposed features (and known issues).

<!-- CONTRIBUTING -->
## Contributing

_Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**._

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Top contributors:
<a href="https://github.com/dubpixel/dpx_kicad/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=dubpixel/dpx_kicad" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## License

Distributed under the CERN OHL W v2 License. See `LICENSE.txt` for more information.

<!-- CONTACT -->
## Contact

### dubpixel - i@dubpixel.tv

Project Link: [https://github.com/dubpixel/dpx_kicad](https://github.com/dubpixel/dpx_kicad)

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

**3D Models:** The models in `zusr_3D` were collected from various open source KiCad and CAD libraries over the years. Attribution is a work in progress — if you recognize your work and want credit or removal, please open an issue. Known sources include SnapEDA, GrabCAD, and various GitHub KiCad community repos.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/dubpixel/dpx_kicad.svg?style=flat-square
[contributors-url]: https://github.com/dubpixel/dpx_kicad/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/dubpixel/dpx_kicad.svg?style=flat-square
[forks-url]: https://github.com/dubpixel/dpx_kicad/network/members
[stars-shield]: https://img.shields.io/github/stars/dubpixel/dpx_kicad.svg?style=flat-square
[stars-url]: https://github.com/dubpixel/dpx_kicad/stargazers
[issues-shield]: https://img.shields.io/github/issues/dubpixel/dpx_kicad.svg?style=flat-square
[issues-url]: https://github.com/dubpixel/dpx_kicad/issues
[license-shield]: https://img.shields.io/github/license/dubpixel/dpx_kicad.svg?style=flat-square
[license-url]: https://github.com/dubpixel/dpx_kicad/blob/main/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/jfleitell
[product-front]: images/front.png
[product-rear]: images/rear.png
[kicad-shield]: https://img.shields.io/badge/KiCad-9-blue?style=flat-square&logo=kicad
[kicad-url]: https://kicad.org
[gdrive-shield]: https://img.shields.io/badge/Google_Drive-Sync-4285F4?style=flat-square&logo=googledrive&logoColor=white
[gdrive-url]: https://drive.google.com
[git-shield]: https://img.shields.io/badge/Git-Version_Control-F05032?style=flat-square&logo=git&logoColor=white
[git-url]: https://git-scm.com
[git-lfs-shield]: https://img.shields.io/badge/Git_LFS-Large_Files-F05032?style=flat-square&logo=git&logoColor=white
[git-lfs-url]: https://git-lfs.github.com 