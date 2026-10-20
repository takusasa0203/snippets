# My Code Snippets

日常の開発（主に組み込みC/C++、Python等）でよく使う定型コードやデザインパターンをまとめたスニペット集です。
VS Code形式（JSON）で管理しているため、**Neovim (LuaSnip)** や **VS Code** でそのまま利用できます。

## 📁 構成 (Directory Structure)

```text
.
├── c.json          # C言語用スニペット
├── cpp.json        # C++用スニペット
└── README.md
```

## 🚀 導入方法 (Installation)

### For Neovim (LazyVim + LuaSnip)

1. このリポジトリを Neovim の設定ディレクトリ内にクローン（またはサブモジュール化）します。

```bash
git clone <このリポジトリのURL> ~/.config/nvim/snippets
```

2. `~/.config/nvim/lua/plugins/snippets.lua` に以下を追加して、VS Code形式として読み込みます。

```lua
return {
  {
    "L3MON4D3/LuaSnip",
    config = function()
      require("luasnip.loaders.from_vscode").lazy_load({
        paths = { vim.fn.stdpath("config") .. "/snippets" },
      })
    end,
  },
}
```

---

## 📖 収録スニペット一覧 (Snippets List)

### C / C++ (`c.json`, `cpp.json`)

| Prefix | 説明 | 展開されるコードの概要 |
| :--- | :--- | :--- |
| `statemachine` | テーブル駆動ステートマシン | `enum` と関数ポインタ配列による状態遷移の雛形 |
| `incguard` | インクルードガード | ファイル名に基づいた `#ifndef ... #define` |
| `main` | main関数の雛形 | 標準的な `int main(int argc, char *argv[])` |

<!-- 新しいスニペットを追加したら、ここに Prefix と説明を書き足していく -->

---

## 💡 スニペット作成のルール（自分用メモ）

- **汎用的なイディオムのみを登録する:** 特定のプロジェクト依存のコードや、機密情報は含めな
いこと。
- **VS Code 互換の構文を使う:** 変数には `${TM_FILENAME_BASE}` などを活用する。
