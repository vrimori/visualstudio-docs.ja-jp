---
title: "警告 : スクリプト デバッグが無効 | Microsoft Docs"
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
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 警告 : スクリプト デバッグが無効
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Internet Explorer では、スクリプトのデバッグは現在無効になっています。  
  
 この警告は、Internet Explorer でスクリプトのデバッグを有効にしないままスクリプトをデバッグした場合に発生します。  セキュリティ上の理由から、Internet Explorer ではスクリプトのデバッグは既定で無効になっています。  
  
### Internet Explorer でスクリプトのデバッグを有効にするには  
  
1.  Internet Explorer で、**\[ツール\]** メニューの **\[インターネット オプション\]** をクリックします。  
  
2.  **\[インターネット オプション\]** ダイアログ ボックスの **\[詳細設定\]** タブをクリックします。  
  
3.  **\[詳細設定\]** タブの **\[設定\]** で **\[ブラウズ\]** カテゴリを表示します。  
  
4.  **\[スクリプトのデバッグを使用しない \(Internet Explorer\)\]** チェック ボックスをオフにします。  
  
5.  **\[OK\]** をクリックします。  
  
6.  Internet Explorer を終了して再起動します。  
  
     新しい設定が反映されます。  
  
## 参照  
 [方法 : スクリプトにアタッチする](../debugger/how-to-attach-to-script.md)