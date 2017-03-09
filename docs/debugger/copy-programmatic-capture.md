---
title: "コピー (プログラムによるキャプチャ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# コピー (プログラムによるキャプチャ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アクティブなグラフィックス ログ \(.vsglog\) ファイルの内容を、新しいファイルにコピーします。  
  
## 構文  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### パラメーター  
 `szNewVSGLog`  
 新しいグラフィックス ログ ファイルのファイル名。  
  
## 解説  
 グラフィックス情報を新しいファイルにコピーするには、グラフィック情報を既にキャプチャしている必要があります。していない場合は、何も実行されません。