---
title: "IDebugSettingsCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2 インターフェイス"
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

非常設定をリモートで有効なデバッグ エンジン。  
  
## 構文  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはデバッグ セッションのマネージャーのイベント コールバックによって実装されデバッグ エンジンによって実装されます。  またDbgmetric \[d\] .lib ではなくローカルで使用できます。  
  
## メソッド  
 次の表は `IDebugSettingsCallback2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|言語の販売元の ID を持つ使用できる式エバリュエーターを列挙します。|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|メトリックを持つ式エバリュエーターのローカル オブジェクトを取得します。|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|式エバリュエーターの指定に対応する値を取得します。|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|名前やメトリックスを持つ式エバリュエーター メトリック ファイルを取得します。|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|名前を持つ式エバリュエーターの測度の一意の識別子を取得します。|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|名前を持つ式エバリュエーターのメトリックスの値の文字列を取得します。|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|名前を持つメトリックスの値を取得します。|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|名前を持つメトリックスの一意識別子を取得します。|  
|[GetMetricString](../Topic/IDebugSettingsCallback2::GetMetricString.md)|名前を持つメトリックスの値の文字列を取得します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 使用例  
 次の例ではパラメーターとして **IDebugSettingsCallback2** オブジェクトを受け取る関数を示します。  
  
```cpp#  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```