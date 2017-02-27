---
title: "IDiaStackWalkHelper | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2 インターフェイス"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラム デバッグ データベース \(.pdb\) ファイルを使用してスタック ウォーク Facilitates。  
  
## 構文  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## VTable の順序でメソッド  
 次の表は`IDiaStackWalkHelper` のメソッドを示しています :  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|レジスタの値を取得します。|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|レジスタの値を設定します。|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|メモリの実行可能ファイルのイメージのデータのブロックを読み取ります。|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|最も近い関数の戻り値をアドレス指定したスタック フレームを検索します。|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../Topic/IDiaStackWalkHelper::searchForReturnAddressStart.md)|指定のアドレスでスタックまたはその近辺でリターン アドレスを指定したスタック フレームを検索します。|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|指定された仮想アドレスを格納するスタック フレームを取得します。|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|指定された仮想アドレスを含むシンボルを取得します。 **Note:**  シンボルは型 `SymTagFunctionType` \([SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md) の列挙値\) が必要です。|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|指定された仮想アドレスに関連付けられた PDATA のデータ ブロックを返します。|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|実行可能ファイルのメモリ空間で仮想アドレスが別の場所にある実行可能の先頭の仮想アドレスを取得します。|  
  
## 解説  
 このインターフェイスはDIA コードでプログラムの実行中にスタック フレームの一覧を構成するために実行可能ファイルに関する情報を取得するために呼び出されます。  
  
## 呼び出し元のメモ  
 クライアント アプリケーションはプログラムの実行中にこのようをサポートするスタックこのインターフェイスを実装します。  このインターフェイスのインスタンスは[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) または [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) のメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)