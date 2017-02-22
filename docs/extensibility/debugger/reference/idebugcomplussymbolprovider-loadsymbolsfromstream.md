---
title: "IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Microsoft Docs"
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
  - "IDebugComPlusSymbolProvider::LoadSymbolsFromStream"
  - "LoadSymbolsFromStream"
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider::LoadSymbolsFromStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

データ ストリームはデバッグ シンボルを読み込みます。  
  
## 構文  
  
```cpp#  
HRESULT LoadSymbolsFromStream(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IStream*  pStream  
);  
```  
  
```c#  
int LoadSymbolsFromStream(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   IStream pStream  
);  
```  
  
#### パラメーター  
 `ulAppDomainID`  
 \[出力\] アプリケーション ドメインの ID。  
  
 `guidModule`  
 \[出力\] モジュールの一意の識別子。  
  
 `baseAddress`  
 \[入力\] メモリのベース アドレス。  
  
 `pUnkMetadataImport`  
 \[入力\] オブジェクト。シンボルのメタデータを含む。  
  
 `pStream`  
 \[入力\] シンボルを含むデータ ストリーム。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 使用例  
 次の例に [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) インターフェイスを公開する **CDebugSymbolProvider の**  オブジェクトに対してこのメソッドを実装する方法を示します。  メソッド呼び出し [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) のメソッド。  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IStream* pStream  
)  
{  
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);  
}  
```  
  
## 参照  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)