---
title: "コードへのブックマークの設定 | Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a7ace58e8cf3a82dce1db789466c55b0e40995c5
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2017
---
# <a name="setting-bookmarks-in-code"></a>コードへのブックマークの設定

ブックマークを使用してコード内の行に印を付けると、特定の位置にすぐに戻り、印を付けた位置の間をすばやく移動することができます。 ブックマークのコマンドとアイコンは、ブックマーク ウィンドウ (**[表示]** > **[ブックマーク ウィンドウ]**) とテキスト エディターのツール バーの 2 か所で使用できます。

## <a name="managing-bookmarks"></a>ブックマークの管理

ブックマークを追加するには、ブックマークを設定する行にカーソルを置きます。 **トグル** ボタンをクリックするか、Ctrl + K キーを押します。 これで、ブックマークが追加されます。 もう一度、トグル ボタンをクリックすると (または Ctrl + K を押すと)、ブックマークが削除されます。 ブックマーク ウィンドウの **[削除]** ボタンをクリックしても、ブックマークを削除できます。

> [!IMPORTANT]
> ブックマークは、コードではなく行番号に設定されます。 コードを変更しても、ブックマークはその行番号の位置に維持され、コードと一緒に移動しません。

ブックマーク ウィンドウの **[次のブックマーク]** および **[前のブックマーク]** ボタンを使用して、ブックマークの間で移動できます。

ブックマーク ウィンドウの **[新しいフォルダー]** をクリックし、選択したブックマークを新しいフォルダーにドラッグして、ブックマークを仮想フォルダーに編成することができます。

ブックマーク ウィンドウの **[すべてのブックマークを無効にする]** ボタンをクリックして、ブックマークを (削除せずに) オフにできます。 同じボタン (**[すべてのブックマークを有効にする]** に変わっています) をクリックして、ブックマークを再び有効にすることができます。

## <a name="see-also"></a>関連項目

[コード エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md)