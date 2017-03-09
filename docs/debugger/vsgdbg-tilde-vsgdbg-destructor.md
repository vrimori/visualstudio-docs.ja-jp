---
title: "VsgDbg::~VsgDbg (デストラクター) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (デストラクター)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`VsgDbg` クラスのインスタンスを破棄します。  グラフィックス情報がアクティブに記録されている場合、グラフィック ログ ファイルは終了して閉じられ、グラフィックス情報がアクティブにキャプチャされているときに使用されたリソースが解放されます。  
  
## 構文  
  
```cpp  
~VsgDbg();  
```  
  
## 参照  
 [VsgDbg::VsgDbg \(コンストラクター\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)