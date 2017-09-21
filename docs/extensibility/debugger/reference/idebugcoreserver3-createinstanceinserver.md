---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

サーバーのデバッグ エンジンのインスタンスを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### パラメーター  
 `szDll`  
 \[入力\] CLSID を実行する dll へのパスが `clsidObject` のパラメーターで指定します。  これは `NULL` 場合COM `CoCreateInstance` 関数が呼び出されます。  
  
 `wLangId`  
 \[入力\] デバッグ エンジンのロケール。  これは [Setlocale 関数](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) のメソッドが呼び出された場合は 0 になります。  
  
 `clsidObject`  
 \[入力\] 作成するデバッグ エンジンの CLSID。  
  
 `riid`  
 \[入力\] クラス オブジェクトから取得する特定のインターフェイスのインターフェイス ID。  
  
 `ppvObject`  
 \[入力\] インスタンス化されたオブジェクトの `IUnknown` のインターフェイス。  目的のインターフェイスにこのオブジェクトをキャストするかマーシャリングします。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [Setlocale 関数](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)