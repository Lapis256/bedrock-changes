# Preview 1.19.70.20

アップデート日：2023/1/27(日本時間)

[公式チェンジログ](https://feedback.minecraft.net/hc/en-us/articles/12571216557709)

## 主な新機能

-   スニーク中、ヒットボックスのサイズが 1.5 ブロックになった
    -   既知のバグが多数あります
        -   詳細はチェンジログを確認してください

## 技術的な新機能

### エンティティ

-   以下の動作が`.json`ファイルで定義されるようになりました
    -   ポーションを飲む動作
        -   [サンプル (ウィッチ)](https://github.com/Mojang/bedrock-samples/blob/dfc3626c1aed058342f4780b32d40c1d3c4333fe/behavior_pack/entities/witch.json#L173-L235)
    -   遠距離攻撃
        -   [サンプル (ウィッチ)](https://github.com/Mojang/bedrock-samples/blob/dfc3626c1aed058342f4780b32d40c1d3c4333fe/behavior_pack/entities/witch.json#L109-L160)

### アイテム・ブロック

-   羊毛の ID が JE と同じになりました
    -   引き続き`minecraft:wool`を利用し続けることはできますが、コマンドの候補には表示されません

### ScriptAPI

#### @minecraft/server@1.1.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server/v/1.1.0-beta.1.19.70-preview.20)

-   **一部のプロパティとプロパティの`setter`、`getter`メソッドが削除され、メソッドに置き換え**

    -   例：`Entity.prototype.velocity` -> `Entity.prototype.getVelocity`
    -   他にもありますが、詳細はチェンジログや、型定義パッケージの型定義ファイルを確認してください

-   **`Location`と`BlockLocation`が削除されました**

    -   代わりに`Vector3`インターフェースを使用します

-   **`EntityDieEventSignal`クラスの追加**

    -   `subscribe(callback: (arg: EntityDieEvent) => void, options?: EntityEventOptions): (arg: EntityDieEvent) => void;`
        -   `EntityEventOptions`インターフェースでイベントが発火する条件を搾れる
            -   それ以外はいたって普通のイベントシグナルクラス

-   **`EntityDieEvent`クラスの追加**

    -   `damageSource`プロパティ
        -   `readonly damageSource: EntityDamageSource`
        -   `EntityHurtEvent`の物と同じ
    -   `deadEntity`プロパティ
        -   `readonly deadEntity: Entity`
        -   死亡したエンティティ

-   **`ItemStack`クラスの変更**

    -   `clearLore`メソッドの追加
        -   `clearLore(): void`
        -   Lore を削除するメソッド
        -   `setLore(undefined)`、`setLore([])`でも可

-   **`ContainerSlot`クラスの変更**

    -   `clearLore`メソッドの追加
        -   `ItemStack`の物と同じ

-   **`Player`クラスの変更**

    -   `tell`メソッドが`sendMessage`に変更
    -   `setSpawn`メソッドの追加
        -   プレイヤーのスポーン座標とディメンションを設定する
        -   `setSpawn(spawnPosition: Vector3, spawnDimension: Dimension): void`
    -   `getSpawnPosition`メソッドの追加
        -   プレイヤーのスポーンする座標を取得する
        -   `getSpawnPosition(): Vector3`
    -   `spawnDimension`プロパティの追加
        -   プレイヤーのスポーンするディメンション
        -   `readonly spawnDimension?: Dimension`
        -   (今後、`getSpawnDimension`に置き換えられる可能性があるかもしれない)
    -   `clearSpawn`メソッドの追加
        -   プレイヤーのスポーンポイントを削除します
        -   `clearSpawn(): void`

-   **`Block`クラスの変更**

    -   `isAir`メソッドの追加
        -   ブロックが空気かを返します
    -   `isLiquid`メソッドの追加
        -   ブロックが液体かを返します
    -   `isSolid`メソッドの追加
        -   ブロックが固体かを返します
        -   丸石は`true`を返しますが、フェンスは`false`を返します

-   **`World`クラスの変更**

    -   `say`メソッドが`sendMessage`に変更
    -   `getDefaultSpawnPosition`メソッドの追加
        -   ワールドスポーン座標を取得します
    -   `setDefaultSpawn`メソッドの追加
        -   ワールドのスポーン座標を設定します
        -   ディメンションはオーバーワールド固定

-   **`System`クラスの変更**

    -   `clearRunSchedule`メソッドが削除されました
    -   `runSchedule`メソッドが削除されました
    -   `runInterval`
        -   `runInterval(callback: () => void, tickInterval?: number): number`
        -   `tickInterval`で指定した tick 間隔で`callback`を実行します
    -   `runTimeout`
        -   `runTimeout(callback: () => void, tickDelay?: number): number`
        -   `tickDelay`で指定した tick が経った後`callback`を実行します
    -   `clearRun`メソッドの変更
        -   `run`以外の`runInterval`、`runTimeout`メソッドで登録された処理を削除するようになりました

-   **`BlockInventoryComponent`クラスに関する変更**

    -   以下のブロックにコンポーネントが追加されました
        -   樽
        -   ビーコン
        -   溶鉱炉
        -   醸造台
        -   ディスペンサー
        -   ドロッパー
        -   かまど
        -   ホッパー
        -   ジュークボックス
        -   書見台
        -   燻製機
        -   シュルカーボックス

-   **ワールドイベントの変更**

    -   `entityDie`イベントの追加
        -   `readonly entityDie: EntityDieEventSignal`
        -   イベントクラスは`EntityDieEvent`

-   **`RawMessageScore`インターフェースの追加**

    -   `objective`プロパティ
        -   `objective?: string`
        -   スコアのオブジェクティブ名
    -   `name`プロパティ
        -   `name?: string`
        -   スコアを持っているプレイヤー名
            -   コマンド違い`@s`使用不可

-   **`RawMessage`インターフェースの変更**

    -   `score`プロパティの追加
        -   `score?: RawMessageScore`
        -   メッセージにスコアを指定します

-   **`Color`クラスがインターフェースに変更**
    -   プロパティはクラスの時と同じ

### @minecraft/server-ui@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-ui/v/1.0.0-beta.1.19.70-preview.20)

### @minecraft/server-gametest@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-gametest/v/1.0.0-beta.1.19.70-preview.20)

### @minecraft/server-net@1.0.0

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-net/v/1.0.0-beta.1.19.70-preview.20)

### @minecraft/server-admin@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-admin/v/1.0.0-beta.1.19.70-preview.20)

## 個人的な感想

### 羊毛の ID 変更について

このアップデートで一番うれしい変更

古い ID を内部的には残しつつ新しい ID に変更する仕組みが完成したと思うので、今後のアップデートで羊毛以外の ID も変更されると思う

### BlockLocation と Location が削除されたことについて

`BlockLocation`/`Location`と`Vector3`が混在していたことを考えると、悪くない変更だと思う

ただ、そこそこ便利なメソッドも消えたのは面倒だなと…

### 一部プロパティの setter、getter メソッドが置き換えられたことについて

個人的にはあまり好きではない…

ただ、メソッドとしてある方が明確なので悪くはないと思う
