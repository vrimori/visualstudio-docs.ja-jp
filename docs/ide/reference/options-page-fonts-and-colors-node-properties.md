---
title: '[フォントおよび色] ノード プロパティ ([オプション] ページ)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a67b683f92a7fc05f8c6c25cead9921959aa550
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959357"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>[フォントおよび色] ノード プロパティ ([オプション] ページ)
このドキュメントでは、**[オプション]** ダイアログ ボックスの **[環境]** カテゴリの **[フォントと色]** に表示されるように登録されているツール ウィンドウのフォントと色のプロパティについて説明します。 ここで説明するプロパティを使用することにより、色を設定できる項目のグループの動的な特性がサポートされます。このグループは、VSPackages がインストールまたはアンインストールされる場合に変化させることができます。

 次のセクションでは、登録されているウィンドウの種類の例、および各ウィンドウで使用できるプロパティを示します。

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>テキスト エディター、プリンターまたはダイアログとツール ウィンドウ
 `DTE.Properties("FontsAndColors", "TextEditor")`

 - または -

 `DTE.Properties("FontsAndColors", "Printer")`

 - または -

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|プロパティ項目名|[値]|説明|
| - |-----------|-----------------|
|FontFamily|Get/Set (String)|使用するフォント名 ("MS P ゴシック" など)。|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|<xref:EnvDTE.vsFontCharSet> の値。ヘブライ語やロシア語など、使用する文字セットの種類を指定します。|
|FontSize|Get/Set (Short)|使用するフォントのサイズ (ポイント単位)。 例: 10 や 12 など。|

## <a name="see-also"></a>「

- [オプション設定の制御](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [オプション ページにあるプロパティ項目名の確認](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [[環境] ノード プロパティ ([オプション] ページ)](../../ide/reference/options-page-environment-node-properties.md)
- [[テキスト エディター] ノード プロパティ ([オプション] ページ)](../../ide/reference/options-page-text-editor-node-properties.md)