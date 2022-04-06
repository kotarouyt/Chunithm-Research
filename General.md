このファイルは、Chunithmのファイル形式、およびこの文書に関して知っておくべき一般的な情報です。

# Tips

* このガイドは、現在のCHUNITHMの、バージョンに対応していない可能性があります。多分後継のバージョンでも引き続き有効ではあると思っているけれど、NEWとか、NEW PLUSとかだとわからないよ。(このガイドはParadiseを念頭に研究されています。)また、NEWで登場した、エアースライドや、エアークラッシュ
ノーツにはまだ解説がありません。今後追加される可能性があります。
* このガイドは、CHUNITHMのいわゆる"シミュレーター"でカスタム曲を作成するためのガイドではありません。(SUSPlayer,Laverita,Seaurchinとかね。)これとかのシミュレーターっていうのは、異なる譜面形式をしてるから、カスタム曲の実装方法もぜんぜん違うよ。
* CHUNITHMでは、よく"XML"ファイルフォーマットを使用するよ。このガイドはあなたがXMLについての知識があることを前提にして話を進めます。
* "music"、"song"はどっちも、Music.xmlを含むmusicフォルダー内のファイル、または譜面ファイルを指すよ。audioはcueFileフォルダー内のファイルを指すよ。
* この文書で説明されているプロセスを効率化するツールを作る人がいれば、この文書へのクレジット表記は当然必要ありませんが[UNLICENSE](https://github.com/Suprnova123/Chunithm-Research/blob/main/UNLICENSE))参照）、それでもやってくれたら嬉しいよね。




# 曲の終わり方。

CHUNITHMで曲をプレイすると、最後のノーツの後に譜面が終了するよ。やったあ。この時上部のプログレスバーと「フルコンボッ！」と「おーるじゃすてぃす」のアニメーションが出てきます。(まあ取ってないと出てこないけど。)その後にリザルト画面が表示されるよ。

# MASTER譜面とWORLD'S END譜面とUltima譜面について。

楽曲のMASTER譜面は、次の2つの条件を満たさないと遊べないよ。

* EXPERT譜面(または下の方法で遊んだMASTER譜面)でS以上を取る。

* MASTER譜面が遊べるチケットを使う。

カスタム譜面を作成するんだったらこの点に注意する必要があるよ。もしMASTER譜面をやるんだったらEXPERT譜面を作らないとこまるかもね...まあEXPERTとか他3つに設定すればいいんだけどさ。

WORLD'S END譜面：
チケットを買わないと絶対に遊べないよ。カスタム曲やるんだったら、めんどくさいからやらないほうがいいと思うな～～～。

Ultima譜面：
WORLD'S END譜面とおんなじでチケットを買わないと遊べないよ。今のところこの難易度は運営が削除曲を追加する時に、作り直しの意味で追加する時に使われてるよ。

# フォルダー

Chunithm's method of receiving updates involves storing the new information in separate "AXXX" folders, found in ``root¥app¥data``. These folders will have varying numbers replacing the Xs depending on the update. Any references to "AXXX" in this document will refer to an unspecified ``A`` Folder. It is worth noting that, while songs usually have their complementary files (audio, jackets, rights) in the same ``A`` folder, it is possible that they are also in other folders. At the moment, it is assumed that newer AXXX folders will overwrite the older AXXX folders' data in terms of being in-game, although the older files will remain intact, however this is not confirmed. It is worth noting that Chunithm's updates will regularly remove certain songs that were prexisting, usually from rights expiring. It is also worth noting that the major updates for Chunithm that change branding and add new features (for example, Amazon to Crystal, or Crystal to Paradise) will not involve new AXXX files, instead condensing them all into the A000 folder. The .exe in ``root¥app¥bin`` may also be overwritten, among other binaries.

# File Types

This is a list of file types of interest that do not have a dedicated page for them, as well as the locations of them and links to additional info if necessary. This is **not** an extensive list, some files that are not of interest will not be included.

## Audio Files

Audio files for music are found in ``root¥app¥data¥AXXX¥cueFile¥cueFileXXXXXX``. The ID of the cueFile can be found in the XML ``<cueFileName>`` tag of the ``Music.xml`` file in the same folder as the chart files for the song of interest. More often than not, these files share the same ID as their corresponding music ID. These files are encoded in the proprietary [CRIWARE ADX2 audio format](https://en.wikipedia.org/wiki/ADX_(file_format)), in pairs of ``.awb`` and ``.acb`` files. These files can be played and converted by the [vgmstream](https://vgmstream.org/) library, specifically the component for [foobar2000](https://www.foobar2000.org/). Information on how to encode your own files into this format can be found in the [Customs](https://github.com/Suprnova123/Chunithm-Research/blob/main/Customs.md) document.

## Jacket Files

Jacket files, otherwise known as the images that are associated with the song, are found in the same folder as the chart files in a ``.dds`` (DirectDraw Surface) file format, which can be opened in software such as [GIMP](https://www.gimp.org/). Jacket files are always in a resolution of 300x300. To imitate the same file size as Chunithm's jackets, although not usually necessary, export any custom ``.dds`` jacket files with BC1 / DXT1 compression from GIMP's export settings.

## Rights Files

Rights files are the images that appear on the bottom left side of the song selection screen for specific songs. They are intended to be used as the file containing the text itself, as the image behind the text is its own separate texture that is reused for every rights file. Rights files are always formatted in a ``.dds`` (DirectDraw Surface) file format in a resolution of 512x48, and can be found in ``root¥app¥data¥AXXX¥rightsInfo¥rightsInfoXXXXXX``. To imitate the same file size as Chunithm's rights files, although not usually necessary, export any custom ``.dds`` rights files with BC1 / DXT1 compression from GIMP's export settings.

# Dummies

Dummy files are used for textures to serve as a template for how the game expects them to be formatted, mostly in terms of resolution. Note that the ``.png`` versions for these files are provided for convenience, all final versions should still be in a ``.dds`` format.

## Jacket Dummies

* [.dds](https://github.com/Suprnova123/Chunithm-Research/blob/main/_assets/jacket_dummy.dds)
* [.png](https://github.com/Suprnova123/Chunithm-Research/blob/main/_assets/jacket_dummy.png)

## Rights Dummies

* [.dds](https://github.com/Suprnova123/Chunithm-Research/blob/main/_assets/rights_dummy.dds)
* [.png](https://github.com/Suprnova123/Chunithm-Research/blob/main/_assets/rights_dummy.png)
