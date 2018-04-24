---
title: コード スニペット ピッカー | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb01cfc51591264b258518f4c90276a7ece11250
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="code-snippet-picker"></a>コード スニペット ピッカー

Visual Studio コード エディターでは、**コード スニペット ピッカー**が提供されています。これを使うと、数回マウスをクリックするだけで、既成のコードのブロックをアクティブなドキュメントに挿入することができます。

**コード スニペット ピッカー**を表示する手順は、使用している言語によって異なります。

- Visual Basic: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** を選択します。

- C#: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。

- C++: **コード スニペット ピッカー**は使用できません。

- F#: **コード スニペット ピッカー**は使用できません。

- JavaScript: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。

- XML: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。

- HTML: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。

- SQL: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** をクリックします。

ほとんどの Visual Studio 開発言語では、**コード スニペット マネージャー**を使って、**コード スニペット ピッカー**が XML スニペット ファイルをスキャンするフォルダー一覧にフォルダーを追加することができます。 独自のスニペットを作成して一覧に追加することもできます。 詳細については、「[チュートリアル: コード スニペットを作成する](../../ide/walkthrough-creating-a-code-snippet.md)」を参照してください。

## <a name="uielement-list"></a>UIElement の一覧

項目名  
**[項目一覧]** で選択した項目の名前を表示する編集可能なテキスト フィールドです。 目的の項目のインクリメンタル検索を実行するには、このフィールドで名前の入力を開始します。 **[項目一覧]** で目的の項目が選択されるまで、文字の追加を続けます。

項目一覧  
挿入に使用できるコード スニペットの一覧、またはコード スニペットを含むフォルダーの一覧です。 スニペットを挿入またはフォルダーを展開するには、目的の項目を選択して Enter キーを押します。

## <a name="see-also"></a>関連項目

[コード スニペットを使用するためのベスト プラクティス](../../ide/best-practices-for-using-code-snippets.md)  
[Visual Basic の IntelliSense コード スニペット](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)  
[コードへのブックマークの設定](../../ide/setting-bookmarks-in-code.md)  
[方法 : surround-with コード スニペットを使用する](../../ide/how-to-use-surround-with-code-snippets.md)