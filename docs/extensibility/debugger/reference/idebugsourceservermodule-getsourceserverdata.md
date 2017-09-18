---
title: "IDebugSourceServerModule::GetSourceServerData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSourceServerModule::GetSourceServerData"
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSourceServerModule::GetSourceServerData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ソース サーバーの情報の配列を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetSourceServerData(  
   ULONG* pDataByteCount,   
   BYTE** ppData  
);  
```  
  
```c#  
public int GetSourceServerData(  
   out uint  pDataByteCount,   
   out int[] ppData  
);  
```  
  
#### パラメーター  
 `pDataByteCount`  
 \[入力\] データ配列のバイト数。  
  
 `ppData`  
 \[入力\] 配列データへの参照。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 使用例  
 次の例に [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) インターフェイスを公開する **CModule の**  オブジェクトに対してこのメソッドを実装する方法を示します。  
  
```cpp#  
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)  
{  
    HRESULT hr = S_OK;  
    CComPtr<ISymUnmanagedReader> pSymReader;  
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;  
  
    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );  
    *pDataByteCount = 0;  
    *ppData = NULL;  
  
    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );  
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );  
  
    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );  
  
Error:  
  
    return hr;  
}  
```  
  
## 参照  
 [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)