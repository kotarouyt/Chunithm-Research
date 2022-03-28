ゲーム内で使用されている譜面ファイル(c2s)に関する参考資料です。このファイルは、c2sの音符の配置やBPMなど、曲の構造を示しています。

# 前提で知っておいたほうがいいこと

* この資料は100％正確であることを保証するものではありません。一部のタグ等は仮定に基づくものであり、さらなる研究が必要な場合があります。
* c2s譜面ファイルフォーマットでは、大体のカウントは0から始まります。0小節は曲の始まり、0セルは左の最初のセル、などを意味します。
* 譜面ファイルの場所は「root¥app¥data¥AXXX¥music¥musicXXXX」にあります。譜面ファイルのファイル形式は前述で何回も言っている通り「.c2s」で「Notepad++」などのツールで開けるプレーンテキストファイルです。
* セルは、プレイフィールド上の音符に対応する鍵盤です。プレイフィールドは16列で、左から0～15の数字が並んでいます。
* 小節は、特定の拍数を含む時間の関数です。各小節は基本的に4拍で構成されており、曲全体を通して比較的一定です。
* 自分の経験的に、Chunithmは、譜面ファイルが非常に特殊な方法で書かれているため、既存の書き方に乗っ取っていない書き方の場合、記述されたノーツは描画されません。。既存の譜面ファイルでは、ノーツに修飾を加えるためにスペースキーではなく、タブキーを使うとうまくいきます。スペースキーでやるとうまくいきません。（なおこれはNotepad++を使った場合の話です、別のやつとか使ったら違うかも。）
* Chunithmは、選択時に「.c2s」ファイルを再読み込みします。てことはだよ？、変更される曲を再選択するだけで、カスタム譜面をデバッグすることが可能なんです！この作業を効率化するために、"今わの際 "などのDANGERスキルを使用する。※1(スキルID 102005）を使用し、カスタムノーツの数小節後に≈20 TAPノートを配置します。こうすることで、曲が終わるのを待たずに、自動的に終了し、より早く再選択することができます。

※1 CHUNITHM NEWであるかどうかは忘れました。


# タグ達

## VERSION

バージョンが設定されているよ。よくわからんけど、まあ「1.08.00」にしたら動くからこれでいいと思う。(CHUNITHM自体のバージョンかなと思ったんだけどちがそうだしよくわからん)

## MUSIC

まあこれは大体「0」になってる。(昔のバージョンとか、Music.xmlがなかったからその時のタグが残りっぱなしなんだと思う)

## SEQUENCEID

これもだいたい「0」

## DIFFICULT

これもですね、うん大体「0.0」になってるよ。(さっきも言ったけど、昔のバージョンとかMusic.xmlがなかったからその時のタグだと思うよ。)

## LEVEL

言わずもがな、これも「0.0」になってます。(3回目ですけど、うん、昔のバージョンとかMusic.xmlがなかったらその時のタグだと思うよ。)

## CREATOR

譜面製作者の名前だよー。難易度がBASICとかADVANCEDになってない限り選曲画面の曲の左下に名前が表示されるよ！

## BPM_DEF

名前のまんま。デフォルトのBPM

### スキーマ(図):

| 1 | 2 | 3 | 4 |
| ---- | ---- | ---- | ---- |

「1」は通常、デフォルトBPMです。つまり曲の始まりのBPMだよ。「2」は通常とか、あとは別のBPM、まあ要は、「1」が頻繁に使うやつだとしたらその次に頻繁に使うBPM的な？
まあ別のBPMがないんだったら、「2＝1」でいいよ。「3」と「4」は「2」と「1」と同じらしい。


## RESOLUTION

曲の解像度を指定するよ。ここは絶対「384」になってるよ。

## CLK_DEF

ここも絶対「384」になってる。

## PROGJUDGE_BPM

ここは「240.000」に絶対なってるよ。

## PROGJUDGE_AER

ここはね～毎回「0.999」になってるんだよね。わあすごい。

## TUTORIAL

この譜面がチュートリアルの譜面かどうかだよ。

## BPM

見たらわかるくない？BPMです。BPM。

### スキーマ(図):

| 開始小節 | オフセット | BPM |
| ---- | ---- | ---- |

## MET

曲の拍子だよ。

### Schema:

| 開始小節 | オフセット | 2番目の値 | 1番目の値 |
| ---- | ---- | ---- | ---- |

拍子の値が逆になってるのは、非常に非常に重要だよ。あと、これは結構外観上のことだよっていうことを言っておく。
この値が影響するのはプレイフィールド上の細かい小節線の配置だけだよ。

## SFL

指定された小節でのスクロール速度を指定するよ。

### スキーマ(図):

| 開始小節 | オフセット | デュレーション | どんだけ早くするか |
| ---- | ---- | ---- | ---- |

注意することなんだけど、どんだけ早くするかの値が「0.000001」であること、つまり小数点以下6桁でなければならなきゃいけないんだよね。この数値に基づいてノーツが早くなったり遅くなったりするよ。この値は外観上のもので、マイナスとかにすると逆に動くよ。(太鼓さん次郎のスクロールみたいだよね。)基本的に、[Fracture RayのMASTERチャートのこの部分](https://youtu.be/5m7bMyIDoec?t=48)みたいな、おもしろ目的(？)のために使われるよ。

# ノーツ達

## 大体ノーツってこういう感じのスキーマ(図)になってるよ。

| ノーツタイプ | 小節 | オフセット | セル | 幅 |
| ---- | ---- | ---- | ---- | ---- |

### ノーツタイプ

ノーツタイプは、特定の場所にに配置したいノーツを記述するものだよ。使えるノーツにはいろんなやつがあるよ。
下で説明してるから見てね。


#### ノーツの種類:

* TAP (タップ)
* CHR (ex-タップ(黄色い光るやつ))
* HLD (ホールド)
* SLD (スライド)
* SLC (スライド中継地点)
* FLK (フリック)
* AIR (エアー)
* AUR (右上エアー)
* AUL (左上エアー)
* AHD (エアーで手あげたままにするやつ)
* ADW (エアーダウン)
* ADR (右下エアー)
* ADL (左下エアー)
* MNE (ダメージ(青のやつ))

### 小節

小節は、音符を配置したい特定の小節を示すものだよ。各小節は（大体）4拍子になってる。値は0から始まって、無限に続くけど、曲が終わったら終わるようにしてね。

### オフセット

音符とかタイミングポイントとかがどのタイミングで始めたらいいかの関数だよ。これは、解像度タグで指定された曲の解像度に依存するんだよね。解像度が384の場合(ていうかまあだいたいそうなってるとおもうけど)、小節の最初のビートは「0」、2番目は「96」、3番目は「192」、4番目は「288」となります。自分がやりたい拍子を割り出すためには、解像度を4で割り、それに自分がしたい拍子を掛けてから、解像度を4で割った値を引きます。

端数のビートを得るには、解像度を4で割って、それに必要なビートの端数を掛けます。そして、その結果と希望するビートを足します。

この場合の関数は次のようになります。

b = 小数点以下を切り捨てた自分がしたい拍子
r = 解像度
f = 拍子の分数

```b(r/4)-(r/4) + f(r/4)```


例えば、解像度が384の4拍子の曲の2拍半の無音が欲しい時は、次のようにしよう。

```
2(384/4)-(384/4) + 1/2(384/4)
192 - 96 + 48
144
```


### セル

さっきも書いたけど、この「セル」には、ノーツが表示されるべきプレイフィールドの列の数値IDが入るよ(0～15)。これは、**セルは左から0~15となってること**を注意しておくことが必要だよ。

### 幅

「セル」の数値とは別に、「幅」の数値は、セルに記載されている数値から**右方向**に伸びる音符の幅を指定するよ。最小値は1で、もし1だったらノーツがセルに記載された列だけ描画されることを意味するよ。
他に、セルの数値が7で、ノーツの幅が3だとすると、ノーツはプレイフィールド上のセル番号「7、8、9」列を占めることになるよ。

## その他ノーツの値に関する情報

大体のノーツ達は、しっかり描画されるために追加の情報を書き込むよ。このセクションでは、ノーツが使用するスキーマ(図)の例を見て、その後、
一般的なスキーマ(図)に示されていない値について解説するよ。引用符で囲まれた値は、そのノーツと一致する値を載せてるよ。


### タップ

タップだよ。まあ言わずもがなだよね、めちゃくちゃ基本形だよ。プレイするときはタップすればいいだけだね。

#### スキーマ(図):

| "Tap" | 小節 | オフセット | セル | 幅 |
| ---- | ---- | ---- | ---- | ---- |

ん？さっき見た気がするって？ああ。そうそう。タップはさっき説明した基本形と同じだよ。楽だね～。

### ex-タップ(黄色い光るやつ)

Ex-タップは普通のタップと似てるけど正確に打てば打つほどスコアが違うよ！

#### スキーマ(図):

| "CHR" | 小節 | オフセット | セル | 幅 | エフェクトの種類 |
| ---- | ---- | ---- | ---- | ---- | ---- |

* エフェクトの種類: みんな知ってるかどうかわからないんだけど、CHUNITHMってEx-タップのエフェクトが3種類(あっNEWになって増えたんだっけ？)があるんだよね。それの指定。(UPとかCEとかDWとかあるよ(NEWではもっと増えてるかも！！！))

### ホールド

これ、一回一回説明する必要ある？まあ一応しとくと、あれね、タップノーツをずっと押す版みたいなね。

#### スキーマ(図): 

| "CHR" | 小節 | オフセット | セル | 幅 | デュレーション |
| ---- | ---- | ---- | ---- | ---- | ---- |

* デュレーション: どんだけ押し続けるか的な。さっき説明したオフセットとおんなじ感じの値の計算方法を使ってるよ。

### スライド

あれあれ、あのーそう、ホールドノーツと似てるけど、スライドノーツは押しながら移動できるんだね...というかさっきから思ってるけどこの資料読んでる人絶対こういう知識あるよね、これ毎回説明する必要あります？
スライドノーツには、SLDとSLCの2種類があるよ。直線で始まるスライドはSLDで始まり、すぐに動き出すスライドはSLCで始まる。すべてのスライドはSLDノートで終わる。

#### Schema:

| "SLD"/"SLC" | 小節 | オフセット | セル | 幅 | デュレーション | 終わるセル | 終わる幅 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |

* デュレーション: どんだけ押し続けるか的な。さっき説明したオフセットとおんなじ感じの値の計算方法を使ってるよ。
* 終わるセル: スライドの継続時間中にスライドが移動する列。セルの値と同様に、0～15の範囲で設定できるよ。スライドが持続時間中、まっすぐなままなようにするには、終わるセルの値をセルの値と同じにする。
* 終わる幅: 持続時間の終了時になってるスライド幅だよ。幅の値とおんなじように、この値は0～15の間の任意の場所に設定することができるよ。終わる幅が幅と違ったら、スライドの途中ででかくなったり小さくなったりするよ。

スライドは、その時点で別のスライドがある同じセルでSLDを呼び出すまで、その後に別のスライドが続くことなく終了します。連続したスライドの途中でSLDを呼び出すと、
その特定のポイントに青い音符が追加されますが、これは純粋に外観上のものです。別の音符を追加せずにスライドを調整するには、SLCを使用します。

スライダーが左右に激しく揺れるのは、ゲームに組み込まれた機能ではなく、単にスライダーが非常に短いオフセットで数セル左右に動くだけのものです。

### Flick

A flick note involves the player having their finger within the cells that the flick inhabits, and then swiping in any horizontal direction.

#### Schema:

| "FLK" | Measure | Offset | Cell | Width | Unknown |
| ---- | ---- | ---- | ---- | ---- | ---- |

* Unknown: Always has a value of "L". Note that this is not the direction of the flick, flick notes can be hit from either direction.

### Air

An air note involves the player raising their hands through the IR sensors above the physical keyboard. Unlike other notes, these notes act as modifiers for already existing notes. There are also different cosmetic versions of the note, however they each function identically.

#### Schema:

| "AIR"/"AUR"/"AUL" | Measure | Offset | Cell | Width | Target Note |
| ---- | ---- | ---- | ---- | ---- | ---- |

* AIR/AUR/AUL: Each of these note types are identical functionality-wise, although affect the appearance of the arrow above the note. AIR has an upwards arrow, AUR has an up-right arrow, and AUL has an up-left arrow.
* Target Note: This value designated what note the Air note "leeches" off of. You should have this note be in the same cell, measure, and offset as the Air note. It's also recommended to only use this note at the end of a note, rather than in the middle of a sustained note. This recommendation can be discarded for high-level charts.

## Air Hold

An air hold note involves having the player hold their hands up towards the sensor after performing an air note. Air holds will always end with a mid-air downwards note automatically.

#### Schema:

| "AHD" | Measure | Offset | Cell | Width | Target Note | Duration |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |

* Target Note: This value designated what note the Air note "leeches" off of. You should have this note be in the same cell, measure, and offset as the Air note. It's also recommended to only use this note at the end of a note, rather than in the middle of a sustained note. This recommendation can be discarded for high-level charts.
* Duration: The amount of time that the note will take to move to the target cell. This value is based on the same format for offset.

To have mid-air downwards notes in a sustained air note, make the first air hold note last until the point where the mid-air note would be, then add another air hold note that starts at the same offset where the preceeding air hold note ends.

### Downwards

A downwards note involves the player lowering their hands through the IR sensors above the physical keyboard. Unlike other notes, these notes act as modifiers for already existing notes. There are also different cosmetic versions of the note, however they each function identically.

#### Schema:

| "ADW"/"ADR"/"ADL" | Measure | Offset | Cell | Width | Target Note |
| ---- | ---- | ---- | ---- | ---- | ---- |

* ADW/ADR/ADL: Each of these note types are identical functionality-wise, although affect the appearance of the arrow above the note. ADW has a downwards arrow, ADR has a down-right arrow, and ADL has a down-left arrow.
* Target Note: This value designated what note the downwards note "leeches" off of. You should have this note be in the same cell, measure, and offset as the downwards note. It's also recommended to only use this note at the end of a note, rather than in the middle of a sustained note. This recommendation can be discarded for high-level charts.

### Mines

A mine note involves the player not touching the cell that the mine is placed on. Touching the cell will result in the player losing score and possibly failing the track.

| "MNE" | Measure | Offset | Cell | Width |
| ---- | ---- | ---- | ---- | ---- |

Mine notes require the same information as Tap notes, and simply follow the universal schema mentioned above.

# Notes Demonstration

Below is a recreation of the MASTER difficulty chart for Cyaegha, which has a RESOLUTION of 386.

```
TAP	8	0	6	4
TAP	8	0	12	4
SLC	8	96	4	4	7	3	4
TAP	8	96	10	4
SLC	8	103	3	4	10	2	4
SLC	8	113	2	4	13	1	4
SLC	8	126	1	4	22	0	4
SLD	8	148	0	4	236	0	4
TAP	8	192	8	4
SLC	8	288	6	4	4	7	4
SLC	8	292	7	4	12	9	4
SLC	8	304	9	4	9	10	4
SLC	8	313	10	4	12	11	4
SLC	8	325	11	4	23	12	4
SLD	8	348	12	4	36	12	4
AHD	9	0	0	4	SLD	192
CHR	9	0	4	8	CE
AIR	9	0	4	8	CHR
AHD	9	0	12	4	SLD	192
TAP	9	288	3	4
TAP	9	288	9	4
```

Below is what the gameplay for this section looks like. This will be broken down into each line of the excerpt above to see their corresponding patterns in gameplay.

![Demonstration of Cyaegha Excerpt](https://raw.githubusercontent.com/Suprnova123/Chunithm-Research/main/_assets/cyaegha%20example.gif)

The two tap notes at the beginning appear as:
```
TAP	8	0	6	4
TAP	8	0	12	4
```

The order of values in these lines is the following:

``Tap note | on the 8th measure | with an offset of 0 | starts on cell 6/cell 12 | extends 4 cells to the right``

You can tell that these notes are supposed to occur at the same time because they share the same measure and offset. Remember that the cells are labelled as 0-15, meaning that the first cell on the left is cell 0.

The next two notes are a slide and a tap that occur at the same time. These appear in the document as:
```
SLC	8	96	4	4	7	3	4
TAP	8	96	10	4
```

Note that the slide has the note type of SLC, since the slider starts in motion. If the slider was stationary at the beginning, it would've had an SLD note type.

The order of values for the slide note is the following:

``Slide note | on the 8th measure | with an offset of 96 | starts on cell 4 | extends 4 cells to the right | has a duration of 7 resolution | ends on cell 3 | ends with a width of 4``

There are a few important things to note here. For one, with a measure of 8 and an offset of 96, this means that the note happens on the second beat of the 8th measure (remember, an offset of 0 means the first beat). It also has a very short duration, at only 7 resolution. This means that the slider only lasts for almost 2/100th of a measure. The reason it's so short is because it's designed to look like a curve. There are later SLC notes that attach to the first slider that gradually change to the shape to a curve.

The tap note later on has an order of values of:

``Tap note | on the 8th measure | with an offset of 96 | starts on cell 10 | extends 4 cells to the right``

Again, since the two notes occur at the same measure and offset, they are simultaneous.

The next notes are several control points for a slider, as well as creating a new slider, and a tap note. Their lines are:
```
SLC	8	103	3	4	10	2	4
SLC	8	113	2	4	13	1	4
SLC	8	126	1	4	22	0	4
SLD	8	148	0	4	236	0	4
TAP	8	192	8	4
SLC	8	288	6	4	4	7	4
SLC	8	292	7	4	12	9	4
SLC	8	304	9	4	9	10	4
SLC	8	313	10	4	12	11	4
SLC	8	325	11	4	23	12	4
SLD	8	348	12	4	36	12	4
```

There are several important things to note here. For one, the SLCs at the top are within very quick succession of each other. As stated above, this is because it's creating a curved slider, so it's very precise to look smooth. There is also an SLD immediately after it, which has a duration of 236 resolution. This is important because you can see that this slider is supposed to end at the same time as the other slider. If you add together the offset, which is 148, and the duration, you'll get a value of 384. If you add together the offset and duration of the second SLD at the bottom, you also get 384. Since they are both on the same measure, this shows that they will end at the same time as each other. It's also worth mentioning that the second pair of SLCs are not related to the first pair. They start on a separate cell from the other slider, so it creates a new slider instead of extending a previous one.

The final part of the excerpt contains several air notes, an air hold, an ex-note, and several tap notes. These appear in the file as:
```
AHD	9	0	0	4	SLD	192
CHR	9	0	4	8	CE
AIR	9	0	4	8	CHR
AHD	9	0	12	4	SLD	192
TAP	9	288	3	4
TAP	9	288	9	4
```

You'll notice that both AHDs, the AIR, and the CHR notes all start at the same time, since they share the same measure and offset. Let's break down each note.

The AHD notes represents the following:

``Air hold note | on the 9th measure | with an offset of 0 | starts on the 0th cell/12th cell | extends to the right by 4 cells | leaches off of the Slider note that occupies that same cell | has a duration of 192 resolution``

The CHR note represents:

``Ex-note | on the 9th measure | with an offset of 0 | starts on the 4th cell | extends to the right by 8 cells | CE modifier``

The AIR note represents:

``Air note | on the 9th measure | with an offset of 0 | starts on the 4th cell | extends to the right by 8 cells | leaches off of the ex-note that occupies the same cell``

The excerpt finally ends with two TAP notes, which mean the following:

``Tap note | on the 9th measure | with an offset of 288 | starts on the 3rd/9th cell | extends to the right by 4 cells``

This concludes the analysis of this excerpt of Cyaegha.

# Ending Tags

**Note:** Although resulting from minimal testing, these values do not seem to influence the functionality of the track. As such, they can be completely ignored when creating custom tracks.

## T_REC_XXX

``XXX`` is replaced with the shorthand for a note type (TAP, CHR, FLK, MNE, HLD, SLD, AIR, AHD), as well as one field labeled ``T_REC_ALL``. Appears to be a count of the amount of notes of the specified type that are in each chart. ``T_REC_ALL`` is equal to the values of the preceeding ``T_REC_XXX`` fields added together.

## T_NOTE_XXX

Seems to be identical to ``T_REC_XXX``, although the values are different from each other despite being in the same chart.

## T_NUM_XXX

Seems to be identical to ``T_REC_XXX`` and ``T_NOTE_XXX``, although there is no ``T_XXX_ALL`` field,  instead there is an unknown ``T_NUM_AAC`` field.

## T_CHRTYPE_XX

``XX`` is replaced with the shorthand for the CHR note's modifiers (UP, DW, CE). Appears to count the amount of CHR notes with the specified modifier in the track.

## T_LEN_XXX

``XXX`` is replaced with the shorthand for "sustain" notes (HLD, SLD, AHD, ALL), as well as one field labeled ``T_LEN_ALL``. Seems to be identical to ``T_REC_XXX``, although it instead counts the amount of milliseconds that the specified type of "sustain" note is active. ``T_LEN_ALL`` is equal to the values of the preceeding ``T_LEN_XXX`` fields added together.

## T_JUDGE_XXX

Unknown.

## T_FIRST_XXXX

Has two tags, ``T_FIRST_MSEC`` and ``T_FIRST_RES``. Both denote the timestamp of the first note in milliseconds and resolution respectively.

## T_FINAL_XXXX

Has two tags, ``T_FINAL_MSEC`` and ``T_FINAL_RES``. Both denote the timestamp of the last note in milliseconds and resolution respectively. This is not necessarily equal to the timestamp of the note listed in the chart file, as sustained notes will move the timestamp to when the note is finished.

## T_PROG_XX

Has 20 tags, starting from ``T_PROG_00`` and progressing to ``T_PROG_95`` as the final tag in increments of 5. Unknown.

# Cosmetics

This portion of the document will outline various cosmetic information on the notes found in game. This is NOT about generic information on the notes, like what the exact color of a note is, but rather the small details that might be useful to know when creating custom charts. This information does not have any bearing on gameplay.

## Flick Notes

Flick notes appear as a gray note with a small blue note inside of it. The blue note has a third of the width of the flick note and is centered on the note.

## Air/Down Notes

Both air and down notes have an arrow either above or below the note that it leeches off of, which has the same width as the note in question. Angled versions of these notes are always angled in a way that points to the cell immediately to the left or right of the original note.