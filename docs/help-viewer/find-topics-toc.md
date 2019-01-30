---
title: ヘルプ ビューアーの目次を使用する
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6becee36b4d78d6522e662d3b6bc4879cad7501d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940844"
---
# 方法:目次でトピックを検索する

**[目次]** タブでは、目次 (TOC) を使用して情報を検索できます。 目次は、インストールしたブックに関するトピックをすべて含む、展開可能なリストです。 TOC 内の移動方法に関するアクセシビリティについては、「[ショートカット キー (ヘルプ ビューアー)](../help-viewer/shortcut-keys.md)」を参照してください。

> [!IMPORTANT]
> TOC で使用できるトピックの範囲は、選択したフィルターによって異なります。

## TOC のフィルター処理

TOC をフィルター処理して、**[目次]** タブに表示されるトピックの範囲を絞り込むことができます。指定した用語のルートがタイトルに含まれている場合にのみ、一覧にタイトルが表示されます。 たとえば、フィルターとして「troubleshooting」を指定すると、「troubleshoot」または「troubleshooting」を含むタイトルのみが表示されます。 タイトルに用語が含まれないノードは、省略記号 (**...**) と共に単一のノードに折りたたまれます。

1.  **[目次]** タブをクリックします。

2.  **[フィルターの内容]** テキスト ボックスに、用語を入力します。

> [!NOTE]
> フィルターの実行に時間がかかる場合は、高度な検索演算子 `title:` を使用すると、結果がすばやく表示される場合があります。

## TOC とのトピックの同期

インデックスまたはフルテキストの検索機能を使用してトピックを開いている場合は、トピック ウィンドウと TOC を同期させることによって、TOC のどこにこのトピックがあるかを特定できます。

1.  トピックを表示します。

2.  ツール バーの **[目次のトピックを表示]** ボタンをクリックするか、**Ctrl**+**S** キーを押します。

     **[目次]** タブが開き、TOC 内のトピックの場所が表示されます。

## 関連項目

- [方法: インデックスでトピックを検索する](../help-viewer/find-topics-index.md)
- [方法: トピックを検索する](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)