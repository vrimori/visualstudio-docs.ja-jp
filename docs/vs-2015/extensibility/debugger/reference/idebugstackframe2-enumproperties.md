---
title: IDebugStackFrame2::EnumProperties |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cbbdfe2585ec7fa90b2e98bbd76baa5093f296e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533536"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugStackFrame2::EnumProperties](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2-enumproperties)します。  
  
ローカル変数など、スタック フレームに関連付けられているプロパティの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]フラグの組み合わせ、 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 、列挙型のフィールドを指定する列挙体[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造体入力します。  
  
 `nRadix`  
 [in]任意の数値情報を書式設定で使用する基数。  
  
 `refiid`  
 [in]選択に使用するフィルターの GUID [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造がなど、列挙`guidFilterLocals`します。  
  
 `dwTimeout`  
 [in]このメソッドから戻る前に待機するミリ秒単位で最大時間。 使用`INFINITE`を無期限に待機します。  
  
 `pcelt`  
 [out]列挙プロパティの数を返します。 これは、呼び出すことと同じ、 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)メソッド。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)必要なプロパティの一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 この方法により、選択したすべてのプロパティを単一の呼び出しで取得するため、順番に呼び出すよりも高速です、 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)と[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

