# API

MODや拡張機能から、`window.AnimationApp` を通じてMagic Paintへ機能を追加できます。

## 基本

```js
const app = window.AnimationApp;
```

## MOD登録

```js
app.registerMod({
  id: 'sample-mod',
  name: 'Sample MOD',
  version: '1.0.0',
  description: 'サンプルMOD'
});
```

## 主要API

### `registerMod(info)`
MODの基本情報をMagic Paintへ登録します。

### `registerShapeType(type, renderer)`
独自の図形タイプと描画処理を追加します。

### `registerBrush(brush)`
独自ブラシを右側のツールパネルへ追加します。

### `addShape(shape)`
キャンバスへ新しい図形データを追加します。

### `getSelected()`
現在選択されている図形を取得します。

## 図形タイプの例

```js
app.registerShapeType('star', {
  draw(ctx, shape) {
    // 描画処理
  },
  bounds(shape) {
    return { x: shape.x, y: shape.y, w: 100, h: 100 };
  },
  move(shape, dx, dy) {
    shape.x += dx;
    shape.y += dy;
  }
});
```

> **注意:** MODはJavaScriptを実行します。信頼できる作者のMODのみ使用してください。
