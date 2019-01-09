---
title: '[オプション]、[テキスト エディター]、[XML]、[その他]'
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 85f37f4266f4c05d4de016caa07e8cc6e3cf43a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905625"
---
# <a name="options-text-editor-xml-miscellaneous"></a>[オプション]、[テキスト エディター]、[XML]、[その他]

XML エディターのオート コンプリートとスキーマの設定を変更するには、**[その他]** プロパティ ページを使用します。 **[オプション]** ダイアログ ボックスを開くには、**[ツール]** メニューをクリックし、**[オプション]** をクリックします。 **[その他]** プロパティ ページにアクセスするには、**[テキスト エディター]** > **[XML]** > **[その他]** ノードを展開します。

## <a name="auto-insert"></a>自動挿入

**終了タグ**

XML 要素を作成すると、テキスト エディターが終了タグを追加します。 要素の開始タグが選択されている場合、エディターは、一致する名前空間プレフィックスも含めて、一致する終了タグを挿入します。 既定では、このチェック ボックスはオンです。

**属性値の引用符**

XML 属性の作成時にエディターは文字 `="` および `"` を挿入し、引用符の内側にキャレット (**^**) を配置します。 既定では、このチェック ボックスはオンです。

**名前空間の宣言**

エディターは、必要に応じて名前空間の宣言を自動的に挿入します。 既定では、このチェック ボックスはオンです。

**その他のマークアップ (コメント、CDATA)**

コメント、CDATA、DOCTYPE、処理命令、およびその他のマークアップがオートコンプリートされます。 既定では、このチェック ボックスはオンです。

## <a name="network"></a>ネットワーク

**DTD とスキーマを自動的にダウンロードする**

HTTP の場所から、スキーマやドキュメント型定義 (DTD) を自動的にダウンロードします。 この機能は、プロキシ サーバーの自動検出を有効にした System.Net を使用します。 既定では、このチェック ボックスはオンです。

## <a name="outlining"></a>アウトライン

**[ファイルが開かれたときにアウトライン モードを実行する]**

ファイルが開かれたときにアウトライン機能をオンにします。 既定では、このチェック ボックスはオンです。

## <a name="caching"></a>キャッシュ

**スキーマ**

スキーマ キャッシュの場所を指定します。 参照ボタン [...] をクリックすると、新しいウィンドウで現在のスキーマ キャッシュの場所が開きます。 既定の場所は、\<*Management Studio のインストール ディレクトリ*>\Xml\Schemas です。

## <a name="see-also"></a>関連項目

- [方法: XML ドキュメントを作成する (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [コード生成](../code-generation-in-visual-studio.md)