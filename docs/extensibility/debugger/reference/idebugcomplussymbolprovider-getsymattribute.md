---
title: "IDebugComPlusSymbolProvider::GetSymAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::GetSymAttribute"
  - "GetSymAttribute"
ms.assetid: 6cbaac92-a60b-4165-a7f5-c34407770f3c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider::GetSymAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定したモジュールの特定の親の属性のデバッグ シンボルを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetSymAttribute (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   _mdToken tokParent,  
   LPOLESTR pstrName,  
   ULONG32  cBuffer,  
   ULONG32* pcBuffer,  
   BYTE*    buffer  
);  
```  
  
```c#  
int GetSymAttribute (  
   uint      ulAppDomainID,  
   Guid      guidModule,  
   int       tokParent,  
   string    pstrName,  
   uint      cBuffer,  
   out uint  pcBuffer,  
   out int[] buffer  
);  
```  
  
#### パラメーター  
 `ulAppDomainID`  
 \[出力\] アプリケーション ドメインの ID。  
  
 `guidModule`  
 \[出力\] モジュールの一意の識別子。  
  
 `tokParent`  
 \[入力\] 親の属性のトークン。  
  
 `pstrName`  
 \[出力\] モジュールの名前。  
  
 `cBuffer`  
 \[出力\] `buffer` に必要なバイト数。  
  
 `pcBuffer`  
 \[出力\] `buffer` の長さ。  
  
 `buffer`  
 \[出力\] 配列します。シンボルを格納する。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 使用例  
 次の例に [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) インターフェイスを公開する **CDebugSymbolProvider の**  オブジェクトに対してこのメソッドを実装する方法を示します。  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetSymAttribute(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    _mdToken tokParent,  
    __in_z LPOLESTR pstrName,  
    ULONG32 cBuffer,  
    ULONG32 *pcBuffer,  
    BYTE buffer[])  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetSymAttribute );  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetSymAttribute( tokParent, pstrName, cBuffer, pcBuffer, buffer ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetSymAttribute, hr);  
  
    return hr;  
}  
```  
  
## 参照  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)