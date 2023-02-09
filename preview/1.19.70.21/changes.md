# Preview 1.19.70.22

アップデート日：2023/2/9(日本時間)

[公式チェンジログ](https://feedback.minecraft.net/hc/en-us/articles/12940778804877)

### コマンド

-   ブロックを扱うコマンドの引数でデータ値を使用できなくなりました

    -   今後は`BlockStates`を使用してください
    -   ビヘイビアパックの場合はパックの`min_engine_version`が`1.19.70`以降の場合のみこの変更を受けます
    -   この変更は実験的機能ではなく、`base_game_version`の影響を受けません
    -   以前のバージョンで設置されたコマンドブロックの場合、この変更の影響を受けません
        -   以前のバージョンで設置されたコマンドブロックとは具体的に、`Version`タグの値が`28`以下のコマンドブロックの事です

-   `dx`,`dy`,`dz`セレクターの変更

    -   このセレクターで指定した範囲と衝突するエンティティも選択されるようになりました
    -   小数点数をサポートするようになりました
    -   おそらくこの変更も古いコマンドブロックでは影響を受けないはずです
    -   試した感じバグがありそう？
        -   コマンドエアプなのでミスってるかも

### ScriptAPI

#### @minecraft/server@1.1.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server/v/1.1.0-beta.1.19.70-preview.21)

-   **`ContainerSlot`クラスの変更**

    -   `clearLore`メソッドの削除
        -   `setLore(undefined)`、`setLore([])`を使用してください
    -   `clearItem`メソッドの削除
        -   `clearItem(undefined)`

-   **`ItemStack`クラスの変更**

    -   文字列状態の ID をコンストラクタに渡して初期化できるようになりました
    -   `data`プロパティの削除
    -   `clearLore`メソッドの削除
        -   `setLore(undefined)`、`setLore([])`を使用してください
    -   `nameTag`プロパティの変更
        -   空の文字列を代入すると名前がリセットされるようになりました
        -   255 文字を超える文字列を代入すると例外を発生させるようになりました
    -   `amount`プロパティの変更
        -   最大スタックサイズより多い値を代入すると、最大スタック数に丸められます
        -   1 より小さい値を代入すると例外を発生させるようになりました

-   **`Entity`クラスの変更**

    -   `playAnimation`メソッドの追加
        -   `playAnimation(animationName: string, options?: PlayAnimationOptions): void`
        -   プレイヤーのアニメーションを再生します

-   **`PlayAnimationOptions`インターフェースの追加**
    -   `blendOutTime`プロパティ
        -   `blendOutTime?: number`
    -   `controller`プロパティ
        -   `controller?: string`
    -   `nextState`プロパティ
        -   `nextState?: string`
    -   `stopExpression`プロパティ
        -   `stopExpression?: string`

### @minecraft/server-ui@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-ui/v/1.0.0-beta.1.19.70-preview.21)

### @minecraft/server-gametest@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-gametest/v/1.0.0-beta.1.19.70-preview.21)

### @minecraft/server-net@1.0.0

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-net/v/1.0.0-beta.1.19.70-preview.21)

### @minecraft/server-admin@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-admin/v/1.0.0-beta.1.19.70-preview.21)

## 個人的な感想

### データ値が消えたことについて

とても良い

羊毛のようにデータ値事態は一応残っている、という感じなると思っていたので消えるのは予想外

`ScriptAPI`ではアイテムのデータ値が一足先に消えたので、コマンドのデータ値も近いうちに消えるんじゃないかな？
