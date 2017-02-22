---
title: "IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetMethodFromAddress"
  - "GetMethodFromAddress"
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ指定のアドレスのメソッドについての情報を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```c#  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### パラメーター  
 `pAddress`  
 \[入力\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のインターフェイスで表されるアドレスをデバッグします。  
  
 `pGuid`  
 \[出力\] モジュールの一意の識別子。  
  
 `pAppID`  
 \[出力\] アプリケーション ドメインの ID。  
  
 `pTokenClass`  
 \[コンテナー\] クラスを表すトークン。  
  
 `pTokenMethod`  
 \[入力\] モジュールを表すトークン。  
  
 `pdwOffset`  
 \[入力\] `pAddress` のパラメーターのバイトの開始時からのオフセット。  
  
 `pdwVersion`  
 \[入力\] メソッドのバージョン番号。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)