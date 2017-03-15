---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

現在のフレームの残りの部分を、グラフィックス ログ ファイルにキャプチャします。  
  
## 構文  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## 解説  
 `BeginCapture` 関数によって開始されたキャプチャなど、別のキャプチャ操作が進行中の場合、そのキャプチャ操作は完了し、別個のフレームとしてグラフィックス ログに記録されます。  その直後、グラフィック診断によって現在のフレームの残りの部分のキャプチャが開始され、それも個別のフレームとして記録されます。  present への呼び出しによって、現在のフレームの末尾がマークされます。  
  
 フレームをキャプチャするには、グラフィックス情報をキャプチャして記録するようにアプリケーションを準備する必要があります。つまり、`CaptureCurrentFrame` を呼び出す前に、`VsgDbg` クラスのインスタンスを通じて [Init](../debugger/init.md) を呼び出してしておく必要があります。  
  
## 参照  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)