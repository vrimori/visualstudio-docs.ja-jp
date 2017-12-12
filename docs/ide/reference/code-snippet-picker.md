---
title: "コード スニペット ピッカー | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58f419d52d2d89f998f64e236cfc1f0053c9cfd1
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="code-snippet-picker"></a>コード スニペット ピッカー
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Code エディターでは、**コード スニペット ピッカー**が提供されています。これを使用すると、数回マウスをクリックするだけで、既成のコードのブロックをアクティブなドキュメントに挿入することができます。  
  
 **コード スニペット ピッカー**を表示する手順は、使用している言語によって異なります。  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** を選択します。  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。  
  
-   [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]: **コード スニペット ピッカー**は使用できません。  
  
-   Visual F#: **コード スニペット ピッカー**は使用できません。  
  
-   [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。  
  
-   XML: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。  
  
-   HTML: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** または **[ブロックの挿入]** をクリックします。  
  
-   SQL: コード エディターで目的の場所を右クリックしてショートカット メニューを表示し、**[スニペットの挿入]** をクリックします。  
  
ほとんどの Visual Studio 開発言語では、**コード スニペット マネージャー**を使用して、**コード スニペット ピッカー**が XML スニペット ファイルをスキャンする**フォルダー一覧**にフォルダーを追加することができます。 独自のスニペットを作成して一覧に追加することもできます。 詳細については、「[チュートリアル: コード スニペットを作成する](../../ide/walkthrough-creating-a-code-snippet.md)」を参照してください。  
  
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