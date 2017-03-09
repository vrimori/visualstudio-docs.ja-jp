---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`BeginCapture` で開始されたキャプチャ区間を終了します。  
  
## 構文  
  
```cpp  
void EndCapture();  
```  
  
## 解説  
 特定種類の描画呼び出しに関するグラフィック情報だけをキャプチャするときなど、キャプチャ区間は通常 1 つのフレームのサブセットに及びます。  キャプチャ区間が present への呼び出しに及ぶ場合は、2 つのフレームのグラフィックス情報がキャプチャされます。  最初のフレームは、`BeginCapture` への呼び出しと present への呼び出しの間の区間に及びます。2 つ目のフレームは、present への呼び出しの後の最初の Direct3D イベントと `EndCapture` への呼び出しの間の区間に及びます。  
  
 区間をキャプチャするには、グラフィックス情報をキャプチャして記録するようにアプリケーションを準備する必要があります。つまり、`BeginCapture` または `EndCapture` を呼び出す前に、`VsgDbg` クラスのインスタンスを通じて [Init](../debugger/init.md) を呼び出してしておく必要があります。  
  
## 参照  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)