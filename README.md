# FancyScrollView [![license](https://img.shields.io/badge/license-MIT-green.svg?style=flat-square)](https://github.com/setchi/FancyScrollView/blob/master/LICENSE)

[English](https://translate.google.com/translate?sl=ja&tl=en&u=https://github.com/setchi/FancyScrollView) (by Google Translate)

高度に柔軟なアニメーションを実装できる汎用の ScrollView コンポーネントです。 無限スクロールもサポートしています。

<img src="https://user-images.githubusercontent.com/8326814/68384224-84a1a980-019a-11ea-9cee-aa6acc4860e2.gif" width="320"><img src="https://user-images.githubusercontent.com/8326814/69004520-d2b36b80-0957-11ea-8277-06bfd3e8f033.gif" width="320"><img src="https://user-images.githubusercontent.com/8326814/59548448-a3549900-8f8a-11e9-9a27-b04f1410a7b5.gif" width="320"><img src="https://user-images.githubusercontent.com/8326814/59548462-b8c9c300-8f8a-11e9-8985-5f1c2e610309.gif" width="320"><img src="https://user-images.githubusercontent.com/8326814/59550410-7f528100-8fa5-11e9-8f1b-41e59b645571.gif" width="320"><img src="https://user-images.githubusercontent.com/8326814/59550411-7f528100-8fa5-11e9-8bfb-bd42da47f7a0.gif" width="320">

## Demo
https://setchi.jp/FancyScrollView/demo/

## API Documentation
https://setchi.jp/FancyScrollView/api/FancyScrollView.html

## Requirements
- Unity 2019.2 or later.
- [.NET 4.x Scripting Runtime](https://docs.unity3d.com/2018.3/Documentation/Manual/ScriptingRuntimeUpgrade.html)

## Installation
### Unity Asset Store
[Asset Store](https://assetstore.unity.com/packages/tools/gui/fancyscrollview-96530) からパッケージをプロジェクトにインストールします。

### Unity Package Manager *(Example scenes not included)*
プロジェクトディレクトリの [`Packages/manifest.json`](https://docs.unity3d.com/Packages/com.unity.package-manager-ui@1.8/manual/index.html#project-manifests) ファイルにリポジトリへの参照を追加します。

```json
{
  "dependencies": {
    "jp.setchi.fancyscrollview": "https://github.com/setchi/FancyScrollView.git#upm"
  }
}
```

### Manual
このリポジトリを Clone または Download します。

## Features
### 自由にスクロールアニメーションを実装できます
FancyScrollView はセルの位置を更新するとき、可視領域の正規化された値を各セルに渡します。セル側では、0.0 ~ 1.0 の値に基づいてスクロールの外観を自由に制御できます。サンプルでは Animator を使用してセルの動きを制御しています。

### データ件数が多くても軽快に動作します
表示に必要なセル数のみが生成され、セルは再利用されます。

### セルとスクロールビュー間で自由にメッセージのやりとりができます
`Context` 経由で、セルがクリックされたことをスクロールビューで検知したり、スクロールビューからセルに指示を出す処理がシンプルに実装できます。実装例（[Examples/02_FocusOn](https://github.com/setchi/FancyScrollView/tree/master/Assets/FancyScrollView/Examples/Sources/02_FocusOn)）が含まれていますので、参考にしてください。

### 特定のセルにスクロールやジャンプができます
移動にかける秒数や Easing の指定もできます。詳しくは API Reference の [Scroller - Methods](https://github.com/setchi/FancyScrollView/blob/master/README.md#methods-2) を参照してください。

### スクロールの挙動を細かく設定できます
慣性の有無、減速率などスクロールに関する挙動の設定ができます。詳しくは API Reference の [Scroller - Inspector](https://github.com/setchi/FancyScrollView/blob/master/README.md#inspector-1) を参照してください。

### スナップをサポートしています
スナップを有効にすると、スクロールが止まる直前に最寄りのセルへ移動します。スナップがはじまる速度のしきい値、移動にかける秒数、 Easing を指定できます。[FancyScrollRect](https://setchi.jp/FancyScrollView/api/FancyScrollView.FancyScrollRect-2.html) および [FancyGridView](https://setchi.jp/FancyScrollView/api/FancyScrollView.FancyGridView-2.html) はスナップをサポートしていません。

### 無限スクロールをサポートしています
Inspector で下記の設定をすることで無限スクロールを実装できます。
1. `FancyScrollView` の `Loop` をオンにするとセルが循環し、先頭のセルの前に末尾のセル、末尾のセルの後に先頭のセルが並ぶようになります。
1. サンプルで使用されている `Scroller` を使うときは、 `Movement Type` を `Unrestricted` に設定することで、スクロール範囲が無制限になります。 1. と組み合わせることで無限スクロールを実現できます。

実装例（[Examples/03_InfiniteScroll](https://github.com/setchi/FancyScrollView/tree/master/Assets/FancyScrollView/Examples)）が含まれていますので、こちらも参考にしてください。[FancyScrollRect](https://setchi.jp/FancyScrollView/api/FancyScrollView.FancyScrollRect-2.html) および [FancyGridView](https://setchi.jp/FancyScrollView/api/FancyScrollView.FancyGridView-2.html) は無限スクロールをサポートしていません。

## Examples
[FancyScrollView/Examples](https://github.com/setchi/FancyScrollView/tree/master/Assets/FancyScrollView/Examples) を参照してください。

WebGL Demo : https://setchi.jp/FancyScrollView/demo/

| Name | Description |
|:-----------|:------------|
|01_Basic|最もシンプルな構成の実装例です。|
|02_FocusOn|ボタンで左右のセルにフォーカスする実装例です。|
|03_InfiniteScroll|無限スクロールの実装例です。|
|04_Metaball|シェーダー表現を活用したメタボールの実装例です。|
|05_Voronoi|シェーダー表現を活用したボロノイの実装例です。|
|06_LoopTabBar|タブで画面を切り替える実装例です。|
|07_ScrollRect|スクロールバー付きの `ScrollRect` 風スクロールビューの実装例です。|
|08_GridView|グリッドレイアウトの実装例です。|

## Usage
もっともシンプルな構成では、

- セルにデータを渡すためのオブジェクト
- セル
- スクロールビュー

の実装が必要です。

### Implementation
セルにデータを渡すためのオブジェクトを定義します。
```csharp
public class ItemData
{
    public string Message { get; }

    public ItemData(string message)
    {
        Message = message;
    }
}
```
`FancyScrollViewCell<TItemData>` を継承して自分のセルを実装します。
```csharp
using UnityEngine;
using UnityEngine.UI;
using FancyScrollView;

public class MyCell : FancyScrollViewCell<ItemData>
{
    [SerializeField] Text message = default;

    public override void UpdateContent(ItemData itemData)
    {
        message.text = itemData.Message;
    }

    public override void UpdatePosition(float position)
    {
        // position は 0.0 ~ 1.0 の値です
        // position に基づいてスクロールの外観を自由に制御できます
    }
}
```
`FancyScrollView<TItemData>` を継承して自分のスクロールビューを実装します。
```csharp
using UnityEngine;
using System.Linq;
using FancyScrollView;

public class MyScrollView : FancyScrollView<ItemData>
{
    [SerializeField] Scroller scroller = default;
    [SerializeField] GameObject cellPrefab = default;

    protected override GameObject CellPrefab => cellPrefab;

    void Start()
    {
        scroller.OnValueChanged(base.UpdatePosition);
    }

    public void UpdateData(IList<ItemData> items)
    {
        base.UpdateContents(items);
        scroller.SetTotalCount(items.Count);
    }
}
```
スクロールビューにデータを流し込みます。
```csharp
using UnityEngine;
using System.Linq;

public class EntryPoint : MonoBehaviour
{
    [SerializeField] MyScrollView myScrollView = default;

    void Start()
    {
        var items = Enumerable.Range(0, 20)
            .Select(i => new ItemData($"Cell {i}"))
            .ToArray();

        myScrollView.UpdateData(items);
    }
}
```

## Author
[setchi](https://github.com/setchi)

## License
[MIT](https://github.com/setchi/FancyScrollView/blob/master/LICENSE)
