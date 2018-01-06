---
title: "IDebugCoreServer3::CreateInstanceInServer |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords: IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cbd287f5ab75374a3272ecbb34c36ffdf384ba84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [Setlocale、_wsetlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)