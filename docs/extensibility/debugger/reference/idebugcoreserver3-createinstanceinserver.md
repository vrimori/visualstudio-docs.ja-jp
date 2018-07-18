---
title: IDebugCoreServer3::CreateInstanceInServer |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71995e38cf58c23437cbb9a6d6973fbd09cab8ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105847"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
サーバー上のデバッグ エンジンのインスタンスを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szDll`  
 [in]指定されている CLSID を実装する dll へのパス、`clsidObject`パラメーター。 これは、する場合`NULL`、し、COM の`CoCreateInstance`関数が呼び出されます。  
  
 `wLangId`  
 [in]デバッグ エンジンのロケールです。 これは、場合は 0 になりますが、 [setlocale、_wsetlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)メソッドを呼び出すことはできません。  
  
 `clsidObject`  
 [in]作成するデバッグ エンジンの CLSID。  
  
 `riid`  
 [in]インターフェイス クラスのオブジェクトから取得するには、特定のインターフェイスの ID。  
  
 `ppvObject`  
 [out]`IUnknown`オブジェクトのインスタンスからのインターフェイスです。 キャストまたは目的のインターフェイスには、このオブジェクトをマーシャ リングします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [setlocale、_wsetlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)