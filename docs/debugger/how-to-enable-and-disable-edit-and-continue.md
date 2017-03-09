---
title: "方法 : エディット コンティニュを有効および無効にする | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/INCREMENTAL リンカー オプション"
  - "[コード変更を適用] コマンド"
  - "中断モード, 適用 (コード変更の)"
  - "コード変更, 適用 (中断モードで)"
  - "エディット コンティニュ, 適用 (コード変更の)"
  - "エディット コンティニュ, 無効化"
  - "エディット コンティニュ, 有効化"
  - "[移動] コマンド"
  - "INCREMENTAL リンカー オプション"
  - "Step コマンド"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : エディット コンティニュを有効および無効にする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディット コンティニュの有効と無効の切り替えは、デザイン時に **\[オプション\]** ダイアログ ボックスで行います。  デバッグの最中にこの設定を変更することはできません。  
  
 エディット コンティニュはデバッグ ビルドでのみ動作します。  ネイティブ C\+\+ については、エディット コンティニュで \/INCREMENTAL オプションを使用する必要があります。  
  
## 手順  
  
#### \[エディット コンティニュ\] を有効または無効にするには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスで、**\[デバッグ\]** ノードを開き、**\[エディット コンティニュ\]** カテゴリをクリックします。  
  
3.  有効にするには、**\[エディット コンティニュを有効にする\]** チェック ボックスをオンにします。  無効にするには、このチェック ボックスをオフにします。  
  
    > [!NOTE]
    >  IntelliTrace が有効になっている場合に、IntelliTrace イベントと呼び出し情報の両方を収集すると、エディット コンティニュが無効になります。  詳細については、「[デバッグ情報収集のための IntelliTrace の構成](http://msdn.microsoft.com/ja-jp/7657ecab-e07e-4b1b-872d-f05d966be37e)」を参照してください。  
  
4.  **\[OK\]** をクリックします。  
  
## 参照  
 [エディット コンティニュ](../debugger/edit-and-continue.md)   
 [\(ダイアログ ボックス \-\)](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)