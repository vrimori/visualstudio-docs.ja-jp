---
title: "IDiaStackWalker | Microsoft Docs"
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
  - "IDiaStackWalker インターフェイス"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

メソッドを .pdb ファイルの情報を使用してスタック ウォークを行います。  
  
## 構文  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaStackWalker` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|x86 プラットフォームのスタック フレームの列挙子を取得します。|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|特定のプラットフォームの種類のスタック フレームの列挙子を取得します。|  
  
## 解説  
 このインターフェイスが読み込まれたモジュールのスタック フレームの一覧を取得するために使用します。  各メソッドはスタック フレームの一覧を作成するために必要な情報を提供する [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) のオブジェクトが渡されます \(クライアント アプリケーションで実行されます\)。  
  
## 呼び出し元のメモ  
 クラス ID `CLSID_DiaStackWalker` でこのインターフェイスは `CoCreateInstance` のメソッドによって`IID_IDiaStackWalker` のインターフェイス ID を呼び出して取得されます。  このインターフェイスを取得する例を次に示します。  
  
## 使用例  
 この例で `IDiaStackWalker` のインターフェイスを取得する方法を示します。  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)