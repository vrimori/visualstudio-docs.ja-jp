---
title: "IDebugSymbolProviderDirect::GetMetaDataImport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMetaDataImport"
  - "IDebugSymbolProviderDirect::GetMetaDataImport"
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMetaDataImport
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メタデータのインポートの情報を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```c#  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### パラメーター  
 `guid`  
 \[出力\] モジュールの一意の識別子。  
  
 `appID`  
 \[出力\] アプリケーション ドメインの ID。  
  
 `ppImport`  
 \[出力\] メタデータのインポートの情報を含むオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)