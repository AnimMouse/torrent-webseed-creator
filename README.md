# Torrent Webseed Creator
Webseeded Torrent Creator using GitHub Actions.

Inspired by [BurnBit †](https://web.archive.org/web/20160304022643/http://burnbit.com/) and [URLHash](http://www.urlhash.com).

Powered by these programs to create a torrent file.
* [torrenttools](https://github.com/fbdtemme/torrenttools)
* [mktorrent](https://github.com/pobrn/mktorrent)
* [py3createtorrent](https://github.com/rsnitsch/py3createtorrent)
* [torf-cli](https://github.com/rndusr/torf-cli)
* [dottorrent-cli](https://github.com/kz26/dottorrent-cli)

An alternative to BurnBit and URLHash.

Convert direct HTTP link to .torrent

Your file is then burned into a torrent.

Torrents created are trackerless, relying on Distributed Hash Table and Peer EXchange, to help reduce the burden of torrent trackers.

For people that have unstable internet.\
Can be paused because it is a torrent.\
Utilizes the power of peer to peer downloads and the client-server downloads.\
Combines the best of both worlds (P2P and Direct HTTP Link).

## How to use
1. Create a repository on GitHub using this template by clicking "Use this template" and then click "Create a new repository".
2. Go to the Actions tab.
3. Choose a program to use by clicking the name of the program under "All workflows". [Comparison of torrent creators](https://github.com/AnimMouse/torrent-webseed-creator/wiki/Comparison-of-torrent-creators)
4. Besides the "This workflow has a workflow_dispatch event trigger.", click "Run workflow".
4. Input the required information at the dropdown box. (Example inputs are predefined.)
   * Name: The name of the torrent file.
   * Comment: The comment inside the torrent file.
   * URL: The URL of the file to download and create a torrent from.
   * File name: The file name of the file you will create a torrent from.
   * Piece size:
     * For mktorrent: The size of the torrent pieces in power of 2 (2^n).
     * For py3createtorrent: The size of the torrent pieces in kilobyte (KB) or 0 for automatic calculation.
     * For torrenttools: The size of the torrent pieces in power of 2 (2^n) or in kilobyte (KB) or auto for automatic calculation.
	 * For torf-cli & dottorrent-cli: The piece size is set automatically.
   * Protocol Version: The version of BitTorrent protocol to use. Either [v1](https://www.bittorrent.org/beps/bep_0003.html), [v2, or hybrid](https://www.bittorrent.org/beps/bep_0052.html) (For torrenttools only).
5. Click "Run workflow" at the bottom of the dropdown box.
5. Wait for it to finish downloading and hashing.
6. After it says passing on GitHub Actions, click the workflow run that has been created and download the torrent file on Artifacts.

For a step by step instruction with screenshots, go to my [website](https://www.animmouse.com/p/how-to-use-torrent-webseed-creator/).\
You can also commission me on [Ko-fi](https://ko-fi.com/animmouse/commissions) so I'll do the work for you.

## URL requirements
1. URL must be accessible without cookies. [Source](http://www.urlhash.com)
2. The URL should not expire, or it will stop working sometime if there is not enough seeders. [Source](https://web.archive.org/web/20160310075751/http://burnbit.com/faq#httpseeds)

## Recommend piece size
| Piece Size | mktorrent      | py3createtorrent | torrenttools | for filesizes      |
|------------|----------------|------------------|--------------|--------------------|
| Automatic  | No support yet | 0                | auto         | Any                |
| 512 KiB    | 19             | 512              | 19 or 512K   | 512 MiB - 1024 MiB |
| 1024 KiB   | 20             | 1024             | 20 or 1024K  | 1 GiB - 2 GiB      |
| 2048 KiB   | 21             | 2048             | 21 or 2048K  | 2 GiB - 4 GiB      |
| 4096 KiB   | 22             | 4096             | 22 or 4096K  | 4 GiB - 8 GiB      |
| 8192 KiB   | 23             | 8192             | 23 or  8192K | 8 GiB - 16 GiB     |
| 16384 KiB  | 24             | 16384            | 24 or 16384K | 16 GiB - 512 GiB   |
| 32768 KiB  | 25             | 32768            | 25 or 32768K | >512 GiB           |

Source: [Seedboxes.cc](https://community.seedboxes.cc/articles/how-to-create-a-torrent-via-the-command-line)

## Increase disk space
GitHub Actions has a soft limit of ≈25 GB, to increase disk space to ≈64 GB, check maximize disk space.

## Difference on Google Colaboratory version
This GitHub Actions version of this program has a soft limit of ≈25 GB (or ≈64 GB), the [Google Colaboratory](https://github.com/AnimMouse/torrent-webseed-creator-colab) version has a soft limit of ≈100 GB.