---
title: "[古いコードの警告] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.stalecode"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[古いコードの警告] ダイアログ ボックス"
  - "コード、古いコードの警告"
  - "警告、[古いコードの警告] ダイアログ ボックス"
  - "エディット コンティニュ、古いコード"
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# [古いコードの警告] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスは、**エディット コンティニュ**ではすぐに適用されない、ネイティブ コードへの変更を行った場合に表示されます。  結果として、現在のスタック フレーム内の一部のネイティブ コードが最新でない \(陳腐化している\) 場合があります。  詳細については、「[How to: Work with Stale Code](http://msdn.microsoft.com/ja-jp/c7536e95-66a6-44a0-995d-3fe5035250b4)」を参照してください。  
  
 **\[次回からこのダイアログ ボックスを表示しない\]**  
 このチェック ボックスをオンにすると、以後エディット コンティニュは、このダイアログ ボックスを表示せずにコード変更を適用します。  この警告がまた表示されるようにするには、**\[オプション\]** ダイアログ ボックスで、**\[デバッグ\]** フォルダーを開き、**\[エディット コンティニュ\]** ページをクリックし、**\[古いコードの警告を表示する\]** をオンにします。  
  
## 参照  
 [サポートされているコードの変更と制限事項 \(C\+\+\)](../debugger/supported-code-changes-cpp.md)   
 [\(ダイアログ ボックス \-\)](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)