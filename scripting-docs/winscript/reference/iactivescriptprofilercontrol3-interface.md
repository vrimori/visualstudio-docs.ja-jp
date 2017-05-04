---
title: "IActiveScriptProfilerControl3 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerControl3 インターフェイス
メソッドを、スクリプト エンジンに関連付けられた GC ヒープのオブジェクトを列挙する手順について説明します。  
  
## 構文  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## メソッド  
 [IActiveScriptProfilerControl3::EnumHeap メソッド](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 関連のスクリプト エンジンのコンテキストで GC ヒープのオブジェクトを反復処理するために使用できるインターフェイス \([IActiveScriptProfilerHeapEnum インターフェイス](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) を返します。