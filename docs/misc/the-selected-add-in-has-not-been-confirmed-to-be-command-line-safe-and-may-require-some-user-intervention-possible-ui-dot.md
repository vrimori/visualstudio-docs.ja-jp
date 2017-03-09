---
title: "The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI). | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0031"
  - "vs.message.VB_E_IDWADDINCMDLINE"
ms.assetid: 19dd24d4-b0f5-4c92-9005-aad48ffda7d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The selected Add-In has not been confirmed to be &#39;Command Line Safe&#39;, and may require some user intervention (possible UI).
通常、このエラーが発生するのは、コマンド プロンプト \(DOS プロンプト\) からアドインを使用するように指定していても、そのアドイン自体がコマンド ラインで安全に使用できないと見なされている場合です。  コマンド ラインでのアドインの使用を妨げる UI が表示されることがあります。  
  
### このエラーを解決するには  
  
1.  **\[ツール\]** メニューの **\[アドイン マネージャー\]** をクリックします。  
  
2.  **\[アドイン マネージャー\]** ダイアログ ボックスで、アドインの **\[コマンド ライン\]** をオフにします。  
  
## 参照  
 [How to: Control Add\-Ins By Using the Add\-In Manager](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md)   
 [How to: Create an Add\-In](../Topic/How%20to:%20Create%20an%20Add-In.md)