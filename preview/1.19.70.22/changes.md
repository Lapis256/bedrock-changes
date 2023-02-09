# Preview 1.19.70.22

アップデート日：2023/2/9(日本時間)

[公式チェンジログ](https://feedback.minecraft.net/hc/en-us/articles/12739185905933)

### ScriptAPI

開発者が投稿した[ドキュメント](https://discord.com/channels/494194063730278411/879773489601585244/1072941310824169492)を使用しました。

#### @minecraft/server@1.1.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server/v/1.1.0-beta.1.19.70-preview.22)

-   **`BeforeExplosionEvent`クラスの変更**

    -   `impactedBlocks`プロパティの削除
    -   `getImpactedBlocks`メソッドの追加
        ```
        getImpactedBlocks(): Vector3[]
        ```
    -   `setImpactedBlocks`メソッドの追加
        ```
        setImpactedBlocks(blocks: Vector3[]): void
        ```

-   **`BeforeItemUseOnEvent`クラスの変更**

    -   `blockLocation`プロパティの削除
    -   `getBlockLocation`メソッドの追加
        ```
        getBlockLocation(): Vector3
        ```

-   **`BlockInventoryComponent`クラスの変更**
    -   `location`プロパティの削除
-   **`BlockLavaContainerComponent`クラスの変更**
    -   `location`プロパティの削除
-   **`BlockPistonComponent`クラスの変更**

    -   `attachedBlocks`プロパティの削除
    -   `location`プロパティの削除
    -   `getAttachedBlocks`メソッドの追加
        ```
        getAttachedBlocks(): Vector3[]
        ```

-   **`BlockPotionContainerComponent`クラスの変更**

    -   `location`プロパティの削除

-   **`BlockRecordPlayerComponent`クラスの変更**

    -   `location`プロパティの削除

-   **`BlockSignComponent`クラスの変更**

    -   `location`プロパティの削除

-   **`BlockSnowContainerComponent`クラスの変更**

    -   `location`プロパティの削除

-   **`BlockWaterContainerComponent`クラスの変更**

    -   `location`プロパティの削除

-   **`ContainerSlot`クラスの変更**

    -   `isStackable`プロパティの追加
        ```
        readonly isStackable: boolean
        ```
        アイテムがスタック可能かどうか
    -   `keepOnDeath`プロパティの追加
        ```
        keepOnDeath: boolean
        ```
        死亡時にアイテムを保持するかどうか
    -   `lockMode`プロパティの追加
        ```
        lockMode: ItemLockMode
        ```
        アイテムのロックモードです
    -   `maxAmount`プロパティの追加
        ```
        readonly maxAmount: number
        ```
        最大スタック数です
    -   `type`プロパティの追加
        ```
        readonly type: ItemType
        ```
    -   `clone`メソッドの追加
        ```
        clone(): ItemStack
        ```
        複製された`ItemStack`クラスを返します
    -   `isStackableWith`メソッドの追加
        ```
        isStackableWith(itemStack: ItemStack): boolean
        ```
        指定したアイテムとスタック可能かどうか
    -   `setCanDestroy`メソッドの追加
        ```
        setCanDestroy(blockIdentifiers?: string[]): void
        ```
        アイテムをもったアドベンチャーモードのプレイヤーが、破壊できるブロックを指定します
    -   `setCanPlaceOn`メソッドの追加
        ```
        setCanPlaceOn(blockIdentifiers?: string[]): void
        ```
        アドベンチャーモードのプレイヤーが、アイテムを設置できるブロックを指定します

-   **`Entity`クラスの変更**

    -   `headLocation`プロパティの削除
    -   `applyImpulse`メソッドの追加
        ```
        applyImpulse(vector: Vector3): void
        ```
        エンティティに指定したベクトルを移動ベクトルとして適応します
    -   `applyKnockback`メソッドの追加
        ```
        applyKnockback(directionX: number, directionZ: number, horizontalStrength: number, verticalStrength: number): void
        ```
        エンティティにノックバックを与えます
    -   `clearVelocity`メソッドの追加
        ```
        clearVelocity(): void
        ```
        エンティティの移動ベクトルをリセットします。
    -   `getHeadLocation`メソッドの追加
        ```
        getHeadLocation(): Vector3
        ```
    -   `setVelocity`メソッドの削除

-   **`ExplosionEvent`クラスの変更**

    -   `impactedBlocks`プロパティの削除
    -   `getImpactedBlocks`メソッドの追加
        ```
        getImpactedBlocks(): Vector3[]
        ```

-   **`ItemStack`クラスの変更**

    -   `isStackable`プロパティの追加
        ```
        readonly isStackable: boolean
        ```
        アイテムがスタック可能かどうか
    -   `keepOnDeath`プロパティの追加
        ```
        keepOnDeath: boolean
        ```
        死亡時にアイテムを保持するかどうか
    -   `lockMode`プロパティの追加
        ```
        lockMode: ItemLockMode
        ```
        アイテムのロックモードです
    -   `maxAmount`プロパティの追加
        ```
        readonly maxAmount: number
        ```
        最大スタック数です
    -   `type`プロパティの追加
        ```
        readonly type: ItemType
        ```
    -   `clone`メソッドの追加
        ```
        clone(): ItemStack
        ```
        複製された`ItemStack`クラスを返します
    -   `isStackableWith`メソッドの追加
        ```
        isStackableWith(itemStack: ItemStack): boolean
        ```
        指定したアイテムとスタック可能かどうか
    -   `setCanDestroy`メソッドの追加
        ```
        setCanDestroy(blockIdentifiers?: string[]): void
        ```
        アイテムをもったアドベンチャーモードのプレイヤーが、破壊できるブロックを指定します
    -   `setCanPlaceOn`メソッドの追加
        ```
        setCanPlaceOn(blockIdentifiers?: string[]): void
        ```
        アドベンチャーモードのプレイヤーが、アイテムを設置できるブロックを指定します

-   **`ItemStartUseOnEvent`クラスの変更**

    -   `blockLocation`プロパティの削除
    -   `buildBlockLocation`プロパティの削除
    -   `getBlockLocation`メソッドの追加
        ```
        getBlockLocation(): Vector3
        ```
    -   `getBuildBlockLocation`メソッドの追加
        ```
        getBuildBlockLocation(): Vector3
        ```

-   **`ItemStopUseOnEvent`クラスの変更**

    -   `blockLocation`プロパティの削除
    -   `getBlockLocation`メソッドの追加
        ```
        getBlockLocation(): Vector3
        ```

-   **`ItemUseOnEvent`クラスの変更**

    -   `blockLocation`プロパティの削除
    -   `getBlockLocation`メソッドの追加
        ```
        getBlockLocation(): Vector3
        ```

-   **`NavigationResult`クラスの変更**

    -   `path`プロパティの削除
    -   `getPath`メソッドの追加
        ```
        getPath(): Vector3[]
        ```

-   **`Player`クラスの変更**

    -   `headLocation`プロパティの削除
    -   `applyImpulse`メソッドの追加
        ```
        applyImpulse(vector: Vector3): void
        ```
        プレイヤーでは使用できません
    -   `applyKnockback`メソッドの追加
        ```
        applyKnockback(directionX: number, directionZ: number, horizontalStrength: number, verticalStrength: number): void
        ```
        プレイヤーにノックバックを与えます
    -   `clearVelocity`メソッドの追加
        ```
        clearVelocity(): void
        ```
        プレイヤーでは使用できません
    -   `getHeadLocation`メソッドの追加
        ```
        getHeadLocation(): Vector3
        ```
    -   `setVelocity`メソッドの削除

-   `ItemLockMode`列挙型の追加

    ```
    export enum ItemLockMode {
      inventory = "inventory",
      none = "none",
      slot = "slot"
    }
    ```

    `ItemStack.prototype.lockMode`, `ContainerSlot.prototype.lockMode`で利用

### @minecraft/server-ui@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-ui/v/1.0.0-beta.1.19.70-preview.22)

### @minecraft/server-gametest@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-gametest/v/1.0.0-beta.1.19.70-preview.22)

### @minecraft/server-net@1.0.0

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-net/v/1.0.0-beta.1.19.70-preview.22)

### @minecraft/server-admin@1.0.0-beta

[型定義パッケージ](https://www.npmjs.com/package/@minecraft/server-admin/v/1.0.0-beta.1.19.70-preview.22)

## 個人的な感想

-   `setVelocity`の代替メソッドが`applyKnockback`がプレイヤーでも使えるのは非常に良い
    -   [動画(Twitter)](https://twitter.com/Lapis256/status/1623386860948164608)
    -   `applyImpulse`, `clearVelocity`も使えたら…
