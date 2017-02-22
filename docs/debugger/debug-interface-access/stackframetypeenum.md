---
title: "StackFrameTypeEnum | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "StackFrameTypeEnum 列挙型"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

スタック フレームの種類を指定します。  
  
## 構文  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elements  
 `FrameTypeFPO`  
 フレーム ポインターを省略します ; FPO の情報を使用できます。  
  
 `FrameTypeTrap`  
 カーネルの点のフレーム。  
  
 `FrameTypeTSS`  
 カーネルの点のフレーム。  
  
 `FrameTypeStandard`  
 は標準のスタック フレーム。  
  
 `FrameTypeFrameData`  
 フレーム ポインターを省略します ; フレームのデータヒントで使用できます。  
  
 `FrameTypeUnknown`  
 構築します。デバッグ情報がありません。  
  
## 解説  
 この列挙体の値は [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) メソッドの呼び出しによって返されます。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)