---
title: '[書式設定] ([オプション] ダイアログ ボックス - [テキスト エディター] - [XML])'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5fbc4678431cd8b540b5bbc90bfab5dc2bb2bd4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020790"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>書式設定すると、XML、テキスト エディターのオプション ダイアログ ボックス

このダイアログ ボックスでは、XML エディターの書式設定を指定することができます。 アクセスできる、**オプション** ダイアログ ボックスから、**ツール**メニュー。

> [!NOTE]
> 選択すると、これらの設定は使用可能な**テキスト エディター**フォルダー、 **XML**フォルダーをクリックし、**書式設定**オプションを**のオプション**  ダイアログ ボックス。

## <a name="attributes"></a>属性
 **手動による属性の書式設定を保持する**

 属性の書式は再設定されません。 既定値です。

> [!NOTE]
> 属性が複数行にわたっている場合、エディターは親要素のインデントに対応するように属性の各行にインデントを設定します。

 **独自の行の属性を整列します。**

 最初の属性のインデントに対応するように、2 番目およびそれ以降の行頭を揃えて配置します。 XML テキストで属性がどのように並べられるかについて例を次に示します。

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>自動再フォーマット
 **クリップボードから貼り付け時に**

 クリップボードから貼り付ける XML テキストの書式を再設定します。

 **終了タグの完成時**

 終了タグが完了したときに要素の書式を再設定します。

## <a name="mixed-content"></a>混合コンテンツ
 **既定では混合コンテンツを保持します。**

 エディターで混合コンテンツの書式を再設定するかどうかを指定します。 既定では、コンテンツが `xml:space="preserve"` スコープで見つかった場合を除き、エディターは混合コンテンツの書式を再設定しようとします。

 要素にテキストとマークアップが混在して含まれている場合、そのコンテンツは混合コンテンツと見なされます。 混合コンテンツを持つ要素の例を次に示します。

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>関連項目

- [XML ドキュメントのプロパティと [プロパティ] ウィンドウ](../xml-tools/xml-document-properties-properties-window.md)
- [XML エディターのコンポーネント](../xml-tools/xml-editor-components.md)