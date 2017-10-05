---
title: "IDebugStackFrame2::EnumProperties |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5359698b2ae148abd5fc38da346ebcd5c456634c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
ローカル変数など、スタック フレームに関連付けられたプロパティの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFieldSpec`  
 [in]フラグの組み合わせ、 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 、列挙内のどのフィールドを指定する列挙体[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造は、入力します。  
  
 `nRadix`  
 [in]任意の数値情報を書式設定で使用する基数。  
  
 `refiid`  
 [in]選択に使用するフィルターの GUID [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造はように、列挙されるまで、`guidFilterLocals`です。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位の最大時間。 使用して`INFINITE`無制限に待機します。  
  
 `pcelt`  
 [out]列挙プロパティの数を返します。 これは、呼び出した場合と同じ、 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)メソッドです。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)必要なプロパティの一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドにより、選択したすべてのプロパティを 1 回の呼び出しで取得できる、ために、順番に呼び出すよりも高速です、 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)と[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
