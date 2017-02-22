---
title: "コード スニペット ピッカー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.expansionpicker"
helpviewer_keywords: 
  - "コード スニペット ピッカー"
  - "コード スニペット, コード スニペット ピッカー"
  - "IntelliSense コード スニペット, コード スニペット ピッカー"
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# コード スニペット ピッカー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] コード エディターには、マウスを数回クリックするだけで、あらかじめ用意されたコードのまとまりをアクティブ ドキュメントに挿入できる**コード スニペット ピッカー**が用意されています。  
  
 **コード スニペット ピッカー**を表示する手順は、使用している言語によって異なります。  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \- コード エディターの希望する位置で右クリックしてショートカット メニューを表示し、**\[スニペットの挿入\]** をクリックします。  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] \- コード エディターの希望する位置で右クリックしてショートカット メニューを表示し、**\[スニペットの挿入\]** または **\[ブロックの挿入\]** をクリックします。  
  
-   [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] \- **コード スニペット ピッカー**は使用できません。  
  
-   Visual F\# \- **コード スニペット ピッカー**は使用できません。  
  
-   [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] \- コード エディターの希望する位置で右クリックしてショートカット メニューを表示し、**\[スニペットの挿入\]** または **\[ブロックの挿入\]** をクリックします。  
  
-   XML \- コード エディターの希望する位置で右クリックしてショートカット メニューを表示し、**\[スニペットの挿入\]** または **\[ブロックの挿入\]** をクリックします。  
  
-   HTML \- コード エディターの希望する位置で右クリックしてショートカット メニューを表示し、**\[スニペットの挿入\]** または **\[ブロックの挿入\]** をクリックします。  
  
-   SQL \- コード エディターの希望する位置で右クリックしてショートカット メニューを表示し、**\[スニペットの挿入\]** をクリックします。  
  
 Visual Studio の開発のほとんどの言語では、使用できる、 **コード スニペット マネージャー** にフォルダーを追加するのには、 **フォルダー\] ボックスの一覧** は、 **コード スニペット ピッカー** XML スニペット ファイルをスキャンします。  独自のスニペットを作成してリストに追加することもできます。  詳細については、「[チュートリアル: コード スニペットを作成する](../../ide/walkthrough-creating-a-code-snippet.md)」を参照してください。  
  
## UIElement の一覧  
 アイテム名  
 **\[項目一覧\]** で選択された項目の名前を表示する、編集可能なテキスト フィールドです。  項目のインクリメンタル検索を実行するには、このフィールドにその名前を入力し始めます。  希望する項目が **\[項目一覧\]** で選択されるまで文字を追加します。  
  
 \[項目一覧\]  
 挿入に使用できるコード スニペットの一覧、またはコード スニペットが格納されたフォルダーの一覧です。  スニペットを挿入またはフォルダーを展開するには、希望する項目を選択し、Enter キーを押します。  
  
## 参照  
 [コード スニペットを使用するためのベスト プラクティス](../../ide/best-practices-for-using-code-snippets.md)   
 [Visual Basic IntelliSense Code Snippets](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [コードへのブックマークの設定](../../ide/setting-bookmarks-in-code.md)   
 [方法 : surround\-with コード スニペットを使用する](../Topic/How%20to:%20Use%20Surround-with%20Code%20Snippets.md)