---
title: "DebugStackFrameDescriptor 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor 構造体"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugStackFrameDescriptor 構造体
スタック フレームを列挙し、同じ複数の列挙子のマージ出力です。  
  
## 構文  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## メンバー  
 `pdsf`  
 スタック フレームのオブジェクト。  
  
 `dwMin`  
 物理アドレスの下位のスコープのコンピューターに依存するビューはこのスタック フレームに関連付けられた  
  
 `dwLim`  
 物理アドレスの上限のコンピューターに依存するビューはこのスタック フレームに関連付けられた  
  
 `fFinal`  
 フラグ。フレームが処理中であることを示します。  
  
 `punkFinal`  
 このパラメーターが `NULL`場合、現在の列挙子のマージは停止し、新しいプロセスが開始されます。  オブジェクトは、新しい列挙型を呼び出す方法を示します。  
  
## 解説  
 プロセス デバッグ マネージャーは、複数のスクリプト エンジンからスタック フレームを並べ替えるためにこの構造体を使用します。  通常、スタックが増加します。  その結果、スタックが増大アーキテクチャで、アドレスは 2 の補数する必要があります。  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)