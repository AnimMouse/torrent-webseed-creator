# Torrent Webseed Creator
Webseeded Torrent Creator using GitHub Actions.

Inspired by [BurnBit †](https://web.archive.org/web/20160304022643/http://burnbit.com/) and [URLHash](http://www.urlhash.com/).

Powered by [mktorrent](https://github.com/Rudde/mktorrent) to create a torrent file.

Convert direct HTTP link to .torrent

Your file is then burned into a torrent.

## How to use
1. Create a repository on GitHub using this template.

2. Open the torrent.yml file on the .github folder.

3. Edit the environment variables inside the yaml file.

Name: The name of the torrent file.

Comment: The comment inside the torrent file.

URL: The URL of the file to download and create a torrent from.

File name: The file name of the file you will create a torrent from.

Piece size: The size of the torrent pieces in potency of 2 (2^n)

4. Push it to your repository

5. Wait for it to finish downloading and hashing.

6. After it says passing on the GitHub Actions, download the torrent file on Artifacts.

## URL requirements
1. URL must be accessible without cookies. [Source](http://www.urlhash.com/)

2. The URL should not expire, or it will stop working sometime if there is not enough seeders. [Source](https://web.archive.org/web/20160310075751/http://burnbit.com/faq#httpseeds)

## Recommend piece size
2^n where n is the value you will input on the piece size variable.

2^19 = 524 288 = 512 KiB for filesizes between 512 MiB - 1024 MiB

2^20 = 1 048 576 = 1024 KiB for filesizes between 1 GiB - 2 GiB

2^21 = 2 097 152 = 2048 KiB for filesizes between 2 GiB - 4 GiB

2^22 = 4 194 304 = 4096 KiB for filesizes between 4 GiB - 8 GiB

2^23 = 8 388 608 = 8192 KiB for filesizes between 8 GiB - 16 GiB

2^24 = 16 777 216 = 16384 KiB for filesizes between 16 GiB - 512 GiB This is the max you should ever have to use.

2^25 = 33 554 432 = 32768 KiB (note that utorrent versions before 3.x CANNOT load torrents with this or higher piece-size)

Source: [Seedboxes.cc](https://seedboxes.helpjuice.com/How-to/128173-how-to-create-a-torrent-via-the-command-line)